---
showonlyimage: true
title:      "Agility and Component Driven Development"
subtitle:   ""
excerpt: "iterative, self-evolving incremental development that demands high collaboration and flexibility to change"
description: ""
date:       2012-05-30
author:    Amit Kumar
image: "img/home-bg.jpg"
draft: false

tags:
    - team autonomy
    - guard-rail
    - engineering organisation
    - product engineering
    - organisation structure

categories: [ Agile Development ]
URL: "/2012/05/30/guardrail-ed-autonomy/"
---

Agile development has become the backbone of modern software development process. In a nutshell, it can be defined as - **iterative, self-evolving incremental development that demands high collaboration and flexibility to change**. Component driven development on the other hand augments to building reusable and testable components that be plugged together to form application foundation for delivering business functionality.

In our current engagement with Firm Account, they have started providing IT tools/solutions to their clients supplementing the strategic solutions they have been providing so far. They wanted to deliver the solution with rapid-prototyping and rapid-delivery.

## Challenges
The challenge was to deliver the solution in quick 2-3 months iterative cycles. The working software was to be delivered and handed over to IT department of the client. This meant the software has to be of high quality and maintainable with least amount of support

## Approach
Each application we were building had certain common components. For eg:

```
- Authentication 
- Work flow process
- Data upload process
- Data crunching and cleansing 
- Data export
- User Management with corporate level security
- Background processing for data manipulation
- etc.
```

This problem can be easily solved with Service Oriented Design Pattern. But since most of the deliverables were ‘leave behind’, we started to observe an evolving pattern of Component Driven Development. There was two approach to establish a pool of commonly required components.

> 1. Staff a team that is responsible for building common components
> 2. **Tax** teams to contribute 'components', if they use any from the components library.

The first seems more common but does not align with the paradigm of Agile Software Development. One team should not be responsible for building and maintaining the software. Over time this leads to quality compromises and delays in deliverables.

Extracting common components from existing applications and taxing teams (who want to use from pool) to contribute to common pool did the magic. Initially leap was a little difficult. It took sometime for us to institutionalize the mind-set of building component -based software that can be contributed back to pool. Once the team was adept with this working process, the pool expanded and became rich.

## Impact and Benefits

- **Redundant work, development time**: Developing every system from scratch means redundant development of many of these re-usable components. These can be shared shared across multiple applications reducing development time.
- **Time to market**: Each application goes through rigorous process of QA and Security Assurance. This meant a lot of time was wasted testing the components that can be built and tested once. Using re-usable components reduced the time to market by ~40%.
- **Expertise sharing**: Software reuse supports the sharing of knowledge naturally. This helps in learning from peers and improves the quality of deliverables
- **Focus on solving the actual business problem**: Teams can focus on solving the business problem rather than spending time building the components that are common
- **Rapid prototyping support**: Reusable components can provide an effective basis for quickly building a prototype of a software system. This provides the opportunity to get customer feedback early in the life cycle, thus supporting the conception of requirements.
- **Maintenance costs**: Fewer defects can occur when proven components have been used, and less of the software system must be maintained.
- **High quality**: Error fixes occur from reuse to reuse. This yields higher quality for a reused component that would be the case for a component that is developed and used only once.

```
What do you think?
```