---
showonlyimage: true
title:      "Building an Engineering setup for a Financial Service Institution"
subtitle:   "A series of 5 posts describing the journey to build Product & Engineering for Financial Services"
excerpt: ""
description: ""
date:       2022-01-02
author: Amit Kumar
image: "img/home-bg.jpg"
draft: false

tags:
    - product engineering
    - engineering at scale
    - financial services
    - engineering excellence
    - infrastructure as a service
    - platform engineering

categories: [ Tech ]
URL: "/2022/01/02/building-engineering-setup-financial-services/"
---

I have been part of building Product & Engineering teams and Digital Transformation setup for almost more than a decade. 

My first experience was during the build of MDL (McKinsey Digital Labs) by our leaders: {{< link_target_blank  href="https://www.linkedin.com/in/sattybhens" title="Satty Bhens" >}} and {{< link_target_blank href="https://www.linkedin.com/in/bijubhaskar/" title="Biju Bhaskar" >}} - a startup-like setup (for both engineering and business building) inside a large organisation.
Both strongly believe in a garage-like setup and gave full support to establish guard-rails in protecting the culture of working as a startup.
Together, we built a solid team of 50-70 engineers (today MDL is more than 200 globally) following the {{< link_target_blank  href="https://en.wikipedia.org/wiki/Spoke%E2%80%93hub_distribution_paradigm" title="hubs-spokes" >}} model knitted together with an **Engineering Mindset** & connected via various communication tools.

### Last life
Fast forward, in my last journey, I have been part of Digital Transformation for {{< link_target_blank  href="https://www.btpn.com/en" title="Bank BTPN" >}}. 
The whole transformation (Technology, Agile & People) journey in the bank is a long story **_for another post_**. But, it was great to **replicate building a garage-like-setup** (although it was not a global setup) - with ring-fenced teams dedicated for each digital product offerings in the bank. The setup was driven by guiding principles: _customer focussed squads, solid development practices for building products, devops mindset, infrastructure as a service (with IAC), observability-enabled systems_, to name a few. I had the opportunity to work with like-minded leaders: {{< link_target_blank href="https://www.forbes.com/profile/jerry-ng/?sh=26604e5b4641" title="Jerry Ng" >}}, {{< link_target_blank href="https://www.linkedin.com/in/djemi-suhenda-1b8657a/" title="Djemi Suhenda" >}}, {{< link_target_blank href="https://www.linkedin.com/in/maya-kartika-52b2a2131/" title="Maya Kartika" >}}, {{< link_target_blank href="https://www.linkedin.com/in/karim-siregar-40170140/" title="Karim Siregar" >}}, {{< link_target_blank href="https://www.linkedin.com/in/peterjan-van-nieuwenhuizen-7142092/" title="Peterjan van Nieuwenhuizen" >}}, {{< link_target_blank href="https://www.linkedin.com/in/arief-harris-0a0730a/" title="Arief Harris" >}}, {{< link_target_blank href="https://www.linkedin.com/in/anika-faisal-a4813749/" title="Anika Faisal" >}} to name a few. I must also thank {{< link_target_blank href="https://www.linkedin.com/in/preethimadhu/" title="Preethi Madhu" >}} and the crew from {{< link_target_blank href="https://www.greyamp.com/" title="Greyamp Consulting" >}}.

From an Engineering lens, during this journey, we faced many challenges (nothing surprising), listed below some of them:

- attracting and retaining [**digital talent**](https://www.gartner.com/en/human-resources/insights/talent-in-digital) to work in a bank is challenging. A majority of them enjoy working with Fintechs or start-ups
- implementing engineering innovation within the boundaries of a bank (_a highly regulated entity_) is challenging. Simple things like automated deployment (_without manual intervention_) requires compliance/regulatory approvals or using monitoring tools like NewRelic required a lot of back-n-forth (not to mention cloud or cloud-based SaaS providers)
- infrastructure (bare metal) becomes a hindrance for rapid scale. You need a native cloud setup to enable Infrastructure scale with flexible cost. _We used Openshift for a cloud-native setup - story for another day_. {{< link_target_blank href="https://aws.amazon.com/outposts/" title="Outpost (AWS)" >}}, {{< link_target_blank href="https://aws.amazon.com/outposts/" title="Anthos (GCP)" >}}, {{< link_target_blank href="https://aws.amazon.com/outposts/" title="Stack (Azure)" >}} help solve these problems to provide a more cloud-friendly environment.

There were other challenges as well - customer acquisition, GTM strategy, regional growth, to name a few... 

### What I have been doing

The journey from BTPN continued with the same leadership but in a different setup: {{< link_target_blank href="https://dkatalis.co" title="Digital Katalis" >}}. This was a new journey of building a technology-based Financial Services having an Engineering mindset that would provide services to a Bank (in Jakarta, Indonesia). 

I am writing down a series of posts explaining various aspects of the journey in building a Product & Engineering setup outside (or at arms-length) from the highly regulated entity (i.e. a bank).

When you’re starting afresh or plan to start a transformation journey, it is extremely crucial to put guiding principles in place. This is similar to **creating a blueprint** of the near-end state of the system architecture before you start to write the code or more closer analogy would be **writing tests before writing code**. 

> As the {{< link_target_blank  href="https://hbr.org/sponsored/2017/10/guiding-principles-for-closing-the-gap-between-strategy-design-and-delivery" title="HBR post" >}} explains, guiding principles are extremely important to make sure you have a reference point always during execution.

These principles might change over a period of time and **probably it would** but it helps to have a reference end-state. For DKatalis, we had the following 7 guiding principles which is the basis of our scale:-

###### 1. Waste repellent learning culture
Culture is an outcome of practices you follow in your setup - although I think, this can be generalised to any industry. 
Being lean & learnability should be at the center of any practice. **If it ain't work, optimise or else throw it away.** 

###### 2. Be hands-on, responsibilities define seniority 
Establish very clear expectations for engineers - no matter the number of years of experience, the person needs to be hands-on. More on this [here](/2022/01/03/building-and-scaling-engineering-team/)

###### 3. Single source of truth 
Have one single source of truth - multiple sources create process mess - agile backlog, source code, customer identity are just a few examples.

###### 4. Be Predictable
Predictability is one of the biggest challenges I have seen in software build. There are two parts to predictability:
- code should do what it looks like it does (when you read the code or read the tests). It should be deterministic and observable
- feature releases should be visible. Questions like, when will this feature be ready for production, is very common. It is a hard problem to solve, however, without predictability, it becomes difficult for other functions in the organisation — Sales or GTM or compliance, to plan for releases. It becomes imperative to make sure we build the setup **as transparent and as predictable** as possible. 

###### 5. Build X-as-a-service mindset
Invest in building the mindset of internal service providers. This is an extension of the {{< link_target_blank href="https://api-university.com/blog/the-api-mandate/" title="Jeff Bezos API Mandate" >}} where he declared that all communication between teams should happen using APIs. Enforce teams to build components that can be reused or consumed as a service. This is deeply related to one of the DK Values: **Customer Centricity**.

###### 6. You touch it, you improve it!
This has been my own mantra of life - as a professional, it is very important to make sure anything you touch, makes it better. Be it code that you modified, be it a test case that you fixed, be it a design change, be it a process that you were working or be it a production incident. Do the right thing, avoid taking shortcuts, the cost of fixing it later is very high.

###### 7. Make processes measurable
**You can manage and optimise only when you can measure**. Define metrics to make processes measurable. More on this in the upcoming post.

The series of posts cover:

- [Building and scaling Engineering team](/2022/01/03/building-and-scaling-engineering-team/): Principles and practices adopted to build the product and engineering team
- [Technology choices & Engineering practices](/2022/01/04/technology-choice-and-engineering-practices/): We took an outward-in approach to establish the foundation of technology stack, architecture/  design choices & engineering practices
- [Platform Engineering](/2022/01/05/platform-engineering/): A team responsible for architecture reference, engineering tools/ practices, cross-cutting-concerns, DevOps processes, playbooks Provide platform-as-service to the internal product team.
- [Infrastructure](/2022/01/27/infrastructure-as-a-service/): The core principle was IAC (Infrastructure as Code). We built service-oriented structure with Infrastructure as Service
- [Operations - keep the lights ON aka DevOps](/2022/02/02/infrastructure-as-a-service/): Traditionally, financial services have a dedicated operations team. Following DevOps principle, we followed -- _You build it, you run it!_
---

It will be great to hear your thoughts, ideas - if you've been on a similar journey.