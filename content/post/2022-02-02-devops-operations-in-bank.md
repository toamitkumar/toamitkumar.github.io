---
showonlyimage: true
title:      "DevOps: Technology Operations in the Bank"
subtitle:   "Building an Engineering setup in Financial Services - V"
excerpt: "Fifth and final article of the series of 5 posts describing the journey to build Product & Engineering for Financial Services"
description: "Fifth and final article of the series of 5 posts describing the journey to build Product & Engineering for Financial Services"
date:       2022-02-02
author: Amit Kumar
image: "img/operations-bank.jpg"
draft: false

tags:
    - product engineering
    - engineering at scale
    - financial services
    - engineering excellence
    - infrastructure as a service
    - platform engineering

categories: [ Tech ]
URL: "/2022/02/02/infrastructure-as-a-service/"
---

The Fifth and final article of the series of 5 articles describes my journey to build an Engineering setup in Financial Services. Read the [preface](/2022/01/02/building-engineering-setup-financial-services/). 

- [Building and scaling Engineering team](/2022/01/03/building-and-scaling-engineering-team/): Principles and practices adopted to build the product and engineering team
- [Technology choices & Engineering practices](/2022/01/04/technology-choice-and-engineering-practices/): We took an outward-in approach to establish the foundation of technology stack, architecture/design choices & engineering practices
- [Platform Engineering](/2022/01/05/platform-engineering/): A team responsible for architecture reference, engineering tools/ practices, cross-cutting-concerns, DevOps processes, playbooks. Provide platform-as-service to the internal product team.
- [Infrastructure]((/2022/01/27/infrastructure-as-a-service/)): The core principle was IAC (Infrastructure as Code). We built a service-oriented structure with Infrastructure as Service
- **Operations - keep the lights ON aka DevOps**: Traditionally, financial services have a dedicated operations team. Following DevOps principle, we followed -- _You build it, you run it!_
---

_**Disclaimer: the scope of this article is limited to System & Application Operations and not all aspects of Operations in a Bank - a much broader subject, to be covered in the future.**_ 

---

Implementing DevOps mindset in a banking setup faces resistance from risk, governance, and regulatory functions. These functions, due to high regulations, create a silos corporate culture. Implementing DevOps later requires cultural changes, hence, based on our past experiences (building/ transforming other banks), we wanted to sow the seed of DevOps from the beginning.


> the term DevOps doesn't need an introduction. 

however, in a financial services setup, we made sure regulatory & audit requirements are taken care and implemented accordingly (avoid future. hassles). Our DevOps setup in DKatalis was driven by our core guiding principle - [Build X-as-a-service]({{< relref path="2022-01-02-building-engineering-financial-services.md#5-build-x-as-a-service-mindset">}}). We had clear domain boundaries for squads:
- registration & sign-ups
- payments
- transfers
- customer & accounts
- etc

Squad(s) were responsible to manage operational support for each of these domain boundaries. 

### Guiding Principles and practices followed
* **Create changelogs**: make sure all deployments to production have a related changelog document with details of:
    - steps and version of the artifact deployed (applicable for both - deployment train & hotfixes)
    - steps and version of any data changes (applicable for both - deployment train & hotfixes)
    - documentation proof about sanity testing of critical user journeys in staging
    - performance and security test results: performance is an automated pipeline. Security is still conducted manually.
    - approval from signing authority in the bank
* **Setup pagerduty alerts based on journey and domain boundaries**: {{< link_target_blank href="https://www.pagerduty.com/" title="pagerduty" >}} alerts are to be generated based on domain boundaries. Each respective squad (for their respective domain) will have {{< link_target_blank href="https://dictionary.cambridge.org/dictionary/english/rota" title="ROTA" >}} in pairs.
* **Monitor and generate alerts for key customer journeys**: each squad is tasked to make sure monitoring metrics associated with customer journeys are captured and alerts are generated as per pagerduty setup.
* **Log monitoring**: define clear error codes (business, application, system). Setup alerts and dashboards based on errors codes.
* **System/ Cloud operations should be managed by Snipers**: [Snipers]({{< relref path="2022-01-27-infrastructure-as-a-service.md#birth-of-snipers">}}) is responsible for the operational health of the Infrastructure. Practices of PD and Log monitoring is applicable to them.
* **Document incidents and capture downtimes**: all incidents on production should be captured using a post-mortem template. Have a weekly post-mortem cadence to discuss the cause of the incident.
* **Single monitoring dashboard**: create a single monitoring dashboard. This has been one of the challenges since we have different tools for APM, Infrastructure, and network monitoring. Not ideal but, we are pulling real-time data pipelines from these monitoring tools into BigQuery and generating reports using data-studio

## Incident Management
As the number of customers grows, it becomes important to have a clear definition of what is considered an Incident on Production. 

> a planned or an unplanned interruption of a service or services

If we go by the above definition, can we classify a bug that interrupts service as an incident? example:

- if a customer is not able to login, **is that an incident or a bug**? Probably not, as it could be an issue with the specific customer.
- can we classify the same bug as an incident if 15% percent of customers are not able to login? The answer here would be, yes.

Hence, it is important to answer the basic question - **what can be considered as an incident?**

We did multiple sessions with Product, Engineering, and Systems teams to outline which customer journeys and under what circumstances, can be classified as an incident. This helped to make sure proper notification and alert setup was configured. This was also helpful to categorise an incident into severity levels - critical, high, medium, low.

> An incident can be either planned (scheduled maintenance causing degradation) or unplanned (unexpected degradation or threat). This also includes security incidents

##### What’s the impact of an incident?
An incident impact is a categorization of the percent of active users who are likely impacted by an incident. We defined the following buckets:

- less than 10%
- 10% - 25%
- 25% - 50%
- more than 50%

During the incident postmortem, reporting a more accurate impact analysis will be needed along with the rationale of how the impact was determined. Considering the multi-stakeholders environment that we have in the bank, it is not easy to have a standard way for assessing impact.

#### Preparing for production support

##### Metrics
As explained above, the domain boundaries were defined for each squad. Each squad was responsible to capture the following:
- throughput, latency, % of errors (and their breakup), apdex score for each API consumed from the services in their boundary
- compute resources: cpu & memory utilisation, network & IOPS, 
- other metrics: kafka lags, # of timeouts & retries 

Each squad was also responsible to create a dashboard with these metrics which need to be linked to the central dashboard.

##### On-call support
- ensure every squad member has an account setup in Pagerduty
- ensure proper levels are setup in PD for each team
- ensure paired ROTA is setup from each squad

##### Escalation policy
Define a clear escalation policy in PD. Some of the important steps to be covered by each squad:
- follow outlined steps for adding journeyID for each service API
- ensure each customer journey is accordingly tagged with the journeyID (triggers rules for generating alerts in PD). 
- ensure all error codes are captured for the specific journey

{{< link_target_blank href="https://id.linkedin.com/in/laksmana" title="Andre Laksmana" >}} was instrumental to make sure the escalation policy is templatised and gets implemented by all squads. As part of regulatory needs (a public bank), the escalation policy needs review from compliance.

##### Postmortem

> Fail. Learn. Grow.

This has been the fundamental philosophy for forming the layered support model for us. More popularly called **RCAs**, we mandated the squads (with domain boundaries) to capture a detailed report with the root cause for an incident on production. Some important aspects included:
- time and duration for the incident
- customer impact
- services and infra components impacted
- the root cause (and tag the issue with the associated taxonomy: database, integration - internal or external, error codes, timeouts, )
- fix (short-term and long-term). All long-term fixes go into the backlog and progress tracked
- chronology of events & actions then happened during the period
- participants

It is important to have sharing sessions of the issues and build a culture of learning. Google describes this as {{< link_target_blank href="https://sre.google/workbook/postmortem-culture/" title="Postmortem" >}} sessions. In short, it is:

> a learning session that discusses the chronological order of actions taken during the incident

The taxonomy was used to build visuals which helped to build knowledge in our monthly cadence - **learning from mistakes**.

![](/img/Incident-dashboard.jpeg "")

## Future of Operations in the bank -- SRE

Ben Treynor Sloss, Google's VP for 24/7, coined the term SRE - `reliability is critical, a system isn’t very useful if nobody can use it!`. Hence, SRE is focused on finding ways to improve the design and operation of systems to make them more scalable, more reliable, and more efficient. 

##### The problem we started to face
We built squads with domain boundaries - which meant, each squad is responsible for building & operating. Each squad was doing ROTA in pairs (with 2 weeks schedules) and the pair on ROTA have the flexibility to choose their working hours for the schedule they are operating. 
With the increasing number of customers and including some of the investigational mundane tasks, we realised the need for a squad which I call: `the first line of defense` (it is debatable whether they exactly qualify to be called an SRE). The intention was to have the domain squads focus on feature development and operability of the product, while we have a dedicated squad (cutting across all) as the first defense for production. Eventually, this squad will evolve towards becoming a true SRE.

#### Is SRE similar to Platform Engineering?
I often got this question, aren't Platform Engineers and SRE doing similar things, why do you need to have 2 separate squads. Platform Engineering and SRE have different purposes for their existence, although, they both are successors of traditional operations teams, and bring the discipline of software engineering to different aspects of operations. 

> Platform Engineering as defined [here]({{< relref "2022-01-05-platform-engineering.md#the-team-that-manages-platform-components" >}}) apply engineering principles to accelerate software delivery

> SRE apply engineering principles for the reliability of the product

Additionally, the squad is built with a different mindsets of engineers. SRE thrives on crisis management and system outages while Platform Engineers are typical software engineers working on solving complex problems to enable productivity in all aspects of the software delivery lifecycle.

---
This article brings an end to the 5 article series to build a Financial Services Product organisation with a focus on bleeding-edge Engineering practices. 

