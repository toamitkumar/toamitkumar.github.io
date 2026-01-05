---
showonlyimage: true
title:      "Infrastructure as a Service"
subtitle:   "Building an Engineering setup in Financial Services - IV"
excerpt: "Fourth article of the series of 5 posts describing the journey to build Product & Engineering for Financial Services"
description: "Fourth article of the series of 5 posts describing the journey to build Product & Engineering for Financial Services"
date:       2022-01-27
author: Amit Kumar
image: "img/cloud-iaas.jpg"
draft: false

tags:
    - product engineering
    - engineering at scale
    - financial services
    - engineering excellence
    - infrastructure as a service
    - platform engineering

categories: [ Tech ]
URL: "/2022/01/27/infrastructure-as-a-service/"
---

The fourth article of the series of 5 articles describes my journey to build an Engineering setup in Financial Services. Read the [preface](/2022/01/02/building-engineering-setup-financial-services/). 

- [Building and scaling Engineering team](/2022/01/03/building-and-scaling-engineering-team/): Principles and practices adopted to build the product and engineering team
- [Technology choices & Engineering practices](/2022/01/04/technology-choice-and-engineering-practices/): We took an outward-in approach to establish the foundation of technology stack, architecture/design choices & engineering practices
- [Platform Engineering](/2022/01/05/platform-engineering/): A team responsible for architecture reference, engineering tools/ practices, cross-cutting-concerns, DevOps processes, playbooks. Provide platform-as-service to the internal product team.
- **Infrastructure**: The core principle was IAC (Infrastructure as Code). We built a service-oriented structure with Infrastructure as Service
- [Operations - keep the lights ON aka DevOps](/2022/02/02/infrastructure-as-a-service/): Traditionally, financial services have a dedicated operations team. Following DevOps principle, we followed -- _You build it, you run it!_
---

{{< link_target_blank href="https://en.wikipedia.org/wiki/Infrastructure" title="Infrastructure" >}} is at the foundation level for any product or service platform. It starts from the lowest level i.e. bare metal to servers to storage to networking.
In a cloud setup, all of these {{< link_target_blank href="https://www.redhat.com/en/topics/cloud-computing/what-is-cloud-infrastructure" title="resources are abstracted" >}} and you treat the resources as service components served through either console or APIs. Hence, it becomes easy to apply all the {{< link_target_blank href="https://12factor.net/" title="best practices" >}} of software development to build your Infrastructure.

The infrastructure team was formed following our core guiding principle - [_X-as-a-service_]({{< relref "2022-01-02-building-engineering-financial-services.md#5-build-x-as-a-service-mindset" >}}). They are service providers to our feature development squads, platform engineering squads, marketing squads, security/compliance squads, and to themselves. I don't think the **term IaaS team** requires an introduction, but let me propose my definition.

## Infrastructure as a Service

> A team that abstracts the complexities of Infra operability (networking, computing, storage, monitoring/ observability, scalability, high-availability), provides on-demand self-serve capability to bootstrap new Infra components, and responsible for Infrastructure support for all environments with a pre-defined SLA & Uptime.

### Guiding principles
- **Infrastructure as Code**: all infra components should be built using a combination of Terraform & Ansible, in short treat all Infra components as a code. _Good coding practices will be applied on Infra code through **code-linters**. Read this {{< link_target_blank href="https://martinfowler.com/bliki/InfrastructureAsCode.html" title="article from Martin Fowler" >}}.
- **Infrastructure should be testable**: make sure to write modular and testable Infra code. This has been one of the areas difficult to achieve given the lack of tools that help measure the quality of scripts. Additionally, not all cloud platforms support using libraries like {{< link_target_blank href="https://terratest.gruntwork.io/" title="Terratest" >}}. Once we migrated to GCP, it is now easier to bring test coverage to terraform code.
- **Created through a CI pipeline and managed through idempotent states**: Infra shouldn't be created manually or through scripts run from any machine (including local machine). Use CI pipelines and manage the state of Infra as a versioned code artifact.
- **Zero trust policy**: by default Infra shouldn't be accessible (especially for any changes manually); apply global access policies to RBAC through IAM policies.
- **Design for scale**: make sure Infra clusters are designed for high availability and scale. Test for DR with backup/restore.
- **Design for high observability**: make sure Infra components have proactive monitoring (threshold limits) and alerts enabled.
- **Follow SLAs**: the infrastructure team will work as a well-oiled internal service provider will clear SLAs

## Birth of Snipers
I like initiatives and teams having their names (attractive ones) based on the context and responsibilities they do. I have observed the following benefits:
- helps align a sense of purpose and associated objectives 
- members can identify themselves with the name
- will have Org-wide visibility for members and seekers to celebrate

This is in alignment with **Project Aristotle**, a research done by Google to discover the secrets of effective teams. They tried to find reasons behind: **What makes a team effective at Google?**

> Great teams are not driven by free lunches, benefits, or wonderful salaries. Psychological safety, Dependability, Structure & clarity, Meaning and, Impact are the {{< link_target_blank href="https://rework.withgoogle.com/print/guides/5721312655835136/" title="5 traits highly effective team" >}}.

Infrastructure is one of the core pillars of engineering (find ways to link to org structure) setup in DKatalis both architecturally and by design. Hence, the name of the team should reflect a set of specialists who are highly skilled in what they do (doesn't undermine the specialisation of other teams). 

{{< link_target_blank href="https://dictionary.cambridge.org/dictionary/english/sniper" title="Snipers" >}}, as the name suggests, are highly skilled and dependable on the job they do. This led to the formation and naming of a team of highly skilled systems engineers who would deliver building cloud-native & highly reliable infrastructure for the bank.

## The array of cloud providers
When we started, one of the important considerations was data center and hosting bank products/ services (this was early 2019). Based on my experience, I was clear to avoid building a physical data center in Jakarta (Indonesia). Unfortunately, the only cloud provider available in Indonesia then was {{< link_target_blank href="https://id.alibabacloud.com/" title="Alibaba Cloud" >}} but none of us had previous experience working on the AlibabaCloud platform. AWS & GCP were on their path to establish their regional setup in Indonesia but it was unclear when operations would start for us to build our data center on their platform.

#### AWS Outposts or GCP Anthos with our own hardware were good options
It was lucrative to consider {{< link_target_blank href="https://aws.amazon.com/outposts/" title="Outposts">}} as it falls between having a DC and a cloud-native setup. This would also help make regulators comfortable given we were building for a highly regulated entity - a bank (a full cloud setup of a bank in this region is still a BIG thing). But, Outposts wasn't ready by the time we started to ship their hardware. 
Similarly, {{< link_target_blank href="https://cloud.google.com/anthos" title="Anthos" >}} with having our hardware, was another option for us to consider but there were too many unknowns. With clear intention to not have a physical data center, the only option left was AlibabaCloud.

#### It was AlibabaCloud
With some back-n-forth and with scale in mind, we settled for AlibabCloud as our hosting setup. The guiding principles were indicators on how the team was going to operate. From a cloud provider perspective, Alibabacloud is similar to AWS (at least the cloud platform APIs) and hence it was relatively similar (given some of us had exposure to AWS) to build the cloud platform.

##### Challenges with AlibabaCloud
Given the similarity with AWS and the availability of {{< link_target_blank href="https://registry.terraform.io/providers/aliyun/alicloud/latest/docs" title="TF Aliyun provider" >}}, it was a quick start to build IAC. However, AlibabaCloud is not a widely penetrated service in the Indonesia Region, hence, many expected feature-set like `internal DNS service wouldn't work by default` (but it is not documented). After hours of debugging, we concluded the service is not enabled in the Indonesia region. Raising a ticket with the Aliyun service desk sorted it in a day. The story was similar for a few other services as well. 

## Designing for failure (and hence scale)
While designing the network topology and scale for Infrastructure, it was important to keep in mind learnings from the past. The guiding principles for Infrastructure design were as follows:

- **Clear separation of all environments**: design each environment as a separate VPC (with CEN sharing), it enables for least impact and maximizing productivity. This helps to treat servers as disposable resources instead of fixed components. 
- **Three-layered subnet - private, protected, public**: private (storage), protected (service catalog), public (public SLBs & NATs)
- **Clear role and access management**: all roles and access are mapped to GSuite. The default policy will disable any access. No direct access to DB, use log events to debug.
- **Performance test environment should be _almost_ replica to production**: have a scientific measure to scale infrastructure components/cluster. Map anticipated traffic to concurrency and user load. Load test in PT environment to understand the Infra scale and extrapolate them on Production. 
- **Idempotent state management & immutable infrastructure**: TF is best at managing state for Infrastructure. Keep Infra code and configuration as an automated and repeatable process, either when deploying resources to new environments or increasing the capacity of the existing system to cope with the extra load.
- **Avoid single point of failure**: introduce automated recovery and reduce disruption at each layer of the system. Introduce redundancy (AZs & multi-datacenter), detection, and data durability (for integrity). 
- **Post-mortem your failures**: drive post-mortems from all infrastructure events and failures. Have sharing cadence across teams and through the entire organisation.


## Compliance & regulatory requirements
{{< link_target_blank href="https://www.mckinsey.com/business-functions/risk-and-resilience/our-insights/a-best-practice-model-for-bank-compliance" title="Compliance requirements" >}} are one of the important concerns for financial service institutions. The traditional compliance model was designed in a different era and with a different purpose in mind that doesn't work in the current expectation of digital setup, however, this has imposed bigger unknown risks at the same time. This article does not cover is limited to some of the compliance & regulatory requirements for a bank from and **infrastructure engineering** lens.

- **Auditable & loggable**
- **User, access, password management**
- **Integration with on-prem components**
- **Capacity management**
- **Secure and hardened Infrastructure**
- **VA & Pentest**
- **Disaster Recovery drills with status reports**
- **Change management process**
- **Backup & Restore**
- **Data in-transit, storage, security, protection, encryption**

## The Mega Cloud Migration
We launched the Bank Platform on AlibabaCloud. But, as I said, other global players were footing themselves in Indonesia. Although, Aliyun was good enough for us, for longevity, stability, and strategic partnership we wanted to migrate out to Google Cloud Platform. Any migration activity requires meticulous planning for: 

> service components, data (integrity, storage, logs, backups, migration, protection, encryption), business drivers, integration to internal & external services, traffic routing, security and threat coverage, performance, scalability, high-availability, zero downtime, rollbacks, avoid vendor lockin, compliance & regulatory approvals, checklists, rebuild infrastructure components, runbooks, war-rooms, automation (avoid any manual process or step), testing, fail in lower environment, customer communication

The keywords above are very important to keep in-mind when planning for migration. Hence, migrating a running bank with transacting customers was a massive undertaking. Jeevan has summarised the whole process in a wonderful {{< link_target_blank href="https://medium.com/dkatalis/migrating-bank-from-one-cloud-to-other-4a8bdcfa2969" title="article" >}} - a must-read.

Sniper team played a lynchpin role to anchor the migration activity. A new set of TF scripts: providers, provisioners, and service migration (w.r.t. GCP) was re-written and migration activity was carried out in a span of ~6 months. This included making sure all system components are monitored and alerts are generated in the new cloud setup. 

> **Cloud migration of the bank was completed in less than 6 months with almost no customer impact and no P1 tickets (keep in mind, this was an operational bank with customers transacting on the platform)**

## The service mindset
The majority of product development is happening in the era of SaaS-first, hence, it is important to build a SaaS mindset (both internally and externally). Having a [_X-as-a-service_]({{< relref "2022-01-02-building-engineering-financial-services.md#5-build-x-as-a-service-mindset" >}}) as our guiding principle, we wanted to have Sniper team develop this paradigm since their inception. 

For Snipers, the customers were all internal (stakeholders who work within your company and require assistance from another individual or department to get their job done) product development squads, business/marketing squads, and compliance/risk/security squads. All of these squads need Infrastructure components to run their development/operational responsibilities - their success metrics is closely linked to how effectively Sniper provides capabilities to them. 

Some learnings building the service mindset:
- **Acknowledge and follow-up** :thumbsup: - this is one of the important criteria for an **as-a-service** mindset. When a problem is reported, it should be acknowledged and accordingly follow-up on the issue till closure. 
- **Clear autonomy of team members** :thumbsup: - we follow Agile ceremonies for managing backlog for Sniper team. This includes any internal development or external issues or tickets. All efforts spent by the team are captured in the backlog. The tickets are open for anyone to pick based on their availability. This has helped build an autonomous environment with clear ownership of work.
- **Define SLAs and align internally** :thumbsup: - Sniper team is driven by OKRs. We have yearly high-level OKRs that is further qualified into quarterly OKRs for the team. This also includes some of the operational metrics like: **MTTR, MTTA, Uptime score**.
- **Define clear pairs of ROTA cycles** :thumbsup: :thumbsdown: - we have the Sniper members participate in each incident (be it for lower or production environment) in pairs. This helps to build team-work across other squads that Sniper supports. It is also becoming challenging many-a-times where a member has to be available but then no incident is reported. We are trying to sort and make it manageable by forming an SRE team - as the first line of defence.
- **Not my problem** :thumbsdown: - this has been one of the outliers for us. Quite often we are faced with the situation where an incident is classified as an Infrastructure issue without much investigation. This leads to man-hours wasted to investigate the issue from scratch to discover it has no relation to Infra.
- **Celebrate successes** :thumbsup:
- **Feedback loop** :thumbsup: - in most cases, a CSAT score is calculated for external customers. This needs to be done even for internal customers. Do an internal survey to find out areas for improvement. So far, we have found doing regular internal retros help collect feedback for the team.

## Journey continues
The journey to build a true IaaS provider to the internal customer continues. We are working on streamlining learnings and improvising the team. 