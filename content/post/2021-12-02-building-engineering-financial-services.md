---
showonlyimage: true
title:      "Building an Engineering setup in Financial Services"
subtitle:   ""
excerpt: "A series of 5 posts describing the journey to build Product & Engineering for Financial Services"
description: "A series of 5 posts describing the journey to build Product & Engineering for Financial Services"
date:       2021-12-02
author: Amit Kumar
image: "img/home-bg.jpg"
published: true

tags:
    - product engineering
    - engineering at scale
    - financial services
    - engineering excellence
    - infrastructure as a service
    - platform engineering

categories: [ Tech ]
URL: "/2021/12/02/building-engineering-setup-financial-services/"
---

I have been part of building Product & Engineering teams and Digital Transformation setup for almost more than a decade. 

My first experience was during the build of MDL (McKinsey Digital Labs) by our leaders: {{< link_target_blank  href="https://www.linkedin.com/in/sattybhens" title="Satty Bhens" >}} and {{< link_target_blank href="https://www.linkedin.com/in/bijubhaskar/" title="Biju Bhaskar" >}}. 
They both are strong believers of garage-like setup and gave full support to establish guard-rails in protecting the culture.
We built a solid team of 150+ engineers globally following {{< link_target_blank  href="https://en.wikipedia.org/wiki/Spoke%E2%80%93hub_distribution_paradigm" title="hubs-spokes" >}} model knitted together with an Engineering Mindset & connected via various communication tools.

In my last journey, I have been part of Digital Transformation for {{< link_target_blank  href="https://www.btpn.com/en" title="Bank BTPN" >}}. 
The whole transformation (Technology, Agile & People) journey in the bank is a long story _for another post_. But, it was great to replicate building a garage-like-setup (although it was not a global setup) - ring-fenced teams dedicated for each digital product offerings in the bank. Core principles of an Engineering setup - customer journey focussed squads, development practices, 

From an Engineering lens, during this journey, we faced many challenges (nothing surprising), describing a few:

- attracting and retaining [**digital talent**](https://www.gartner.com/en/human-resources/insights/talent-in-digital) to work in a bank is challenging. Majority of them enjoy working with Fintechs or other start-ups
- implementing engineering innovation within boundaries of a bank (_a highly regulated entity_) is challenging. Simple things like automated deployment (_without manual intervention_) requires compliance/regulatory approvals or using monitoring tools like NewRelic required a lot of back-n-forth (cloud or cloud based SaaS in a bank is a NO-NO)
- infrastructure (bare metal) becomes hinderance for rapid scale. You need native cloud setup to enable Infrastructure scale with flexible cost. {{< link_target_blank href="https://aws.amazon.com/outposts/" title="Outpost (AWS)" >}}, {{< link_target_blank href="https://aws.amazon.com/outposts/" title="Anthos (GCP)" >}}, {{< link_target_blank href="https://aws.amazon.com/outposts/" title="Stack (Azure)" >}} are good solutions in this direction. _We used Openshift for a cloud native setup - story for another day_

There are other challenges as well - customer acquisition, GTM strategy, regional growth, to name a few... hence, in the new journey of building a technology based Financial Services - {{< link_target_blank href="https://dkatalis.co" title="DKatalis" >}} (Digital Katalis, Katalis is a Sanskrit word which means Catalyst), we setup as an Engineering organisation to provide services to a Bank (in Jakarta, Indonesia). I am writing down a series of posts that explains the journey of building Product & Engineering setup outside (or at arms-length) from the highly regulated entity. 

The posts covers:

#### 1. Engineering team & practices
#### 2. Technology choices and architectural setup
#### 3. Infrastructure
#### 4. Operations - keep the lights ON aka DevOps
#### 5. Platform Engineering

It will be great to hear your thoughts, ideas - if you've been on a similar journey.