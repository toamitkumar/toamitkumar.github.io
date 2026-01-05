---
showonlyimage: true
title:      "Guardrail-ed Autonomy"
subtitle:   "Instill gurad-rails for team autonomy"
excerpt: "Instill gurad-rails for team autonomy"
description: ""
date:       2021-01-30
author:    Amit Kumar
image: "img/guard-rail-autonomy.jpg"
draft: false

tags:
    - team autonomy
    - guard-rail
    - engineering organisation
    - product engineering
    - organisation structure

categories: [ Tech ]
URL: "/2021/01/30/guardrail-ed-autonomy/"
---

I haven’t written much in recent years, at least not through blog posts. I thought 2021, would be a good time to start penning some of my thoughts & learnings I have had in the recent past years.

Team formation, functioning, reporting are the most common challenges every organisation have. Lately, I have been involved in discussions related to Team Autonomy. Hence, this article.

[Autonomy](https://en.wikipedia.org/wiki/Autonomy) has different meaning based on context: political, medical, HR, organisation. Narrowing our focus to an Organisation, it has a wide spectrum from highly-organised (CMM levels or SixSigmas) to an Anarchical setup (a budding startup). I have never been a fan of being at the edge of the spectrum, it has its own consequences.

Having said that, in an Engineering setup,
> **Autonomy again has different meaning based on context: team v/s individual, process autonomy, technology autonomy etc...**

## Rationale

To cite an example to explain it better. In an engineering setup, **autonomy** will relate to team or individual choice of technology stack/tools/ processes - Java or Javascript or .NET or Go or Ruby or Python, Kafka or Rabbit or you name it, monitoring tools, alert notification tools, Agile Management tools (Jira vs Pivotal vs Git Issues, Excel vs Asana etc), Kanban vs Scrum vs Lean etc... the spectrum is quite broad. Hence, choosing the stack/ process/ toolchain has to be done carefully keeping in mind various parameters: *use-case, talent availability, org-culture* etc.. the cost of changing the stack/ process/ tool is very high. For e.g.: [Airbnb switched from ReactNative to Native](https://softwareengineeringdaily.com/2018/09/24/show-summary-react-native-at-airbnb/) after doing heavy investment in RN. It doesn't mean Airbnb took wrong decisions (it was the choice that was deemed fit when they did it). When you're starting up, it is natural to pick what works best for solving the problem. But as the organisation grows, the liberty (read autonomy) to pick a tech stack, a language or a framework or a process will have different consequences and might come out very expensive especially when you've interconnected dependencies.

Hence, the term 
> **Guradrail-ed Autonomy** 

it means define boundaries for stack/ language/ framework/ tools/ processes and let the team have the autonomy to choose within those defined boundaries.

## What are the benefits?

After we adopted guardrail-ed autonomy, there are many benefits team found some of which are:

- as you scale, managing evolution/ upgrades/ security improvements in tech stack can be controlled easier if the boundaries are well defined
- hiring for specified boundaries of tech-stack (one can counter-argue that we should hire generalists who can learn any tech stack/frameworks)
- you will never be in a situation where an application or a system was written in a language or stack with no one to maintain or support

## Ok, I understand it, now, how do I do it?

Following steps can be used for defining the guard-rails for team autonomy:

- Define guard-rails to identify various options that fit into your organisation based on: existing talent pool, ease of hiring, business use-case, existing architectural patterns, planned architectural changes in your Org, supportability etc..
- Put effort to develop boiler-plate code for standardising the seeds, configs, templates, cross-cutting-concerns
- Socialise the standardisation effort and take bottom-top (or top-down whichever deems fit into your org-culture) approach for adoption.
- Monitor and measure the adoption
- Make sure to define Metrics for measuring and optimise the standardised platform/ tool/ process/ stack

## Summary

We want our teams to move fast and have the freedom to find creative solutions. As our culture evolves, team autonomy (with guardrails) allows us to harness that diversity, so that we can still iterate & scale fast — but with defined boundaries, too.