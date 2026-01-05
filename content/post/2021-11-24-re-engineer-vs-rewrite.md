---
showonlyimage: true
title:      "Re-Engineer v/s Rewrite"
subtitle:   "A tale of choices you have to make when taking a decision"
excerpt: "A tale of choices you have to make when taking a decision"
description: ""
date:       2021-11-24
author: Amit Kumar
image: "img/reengineer-rewrite.jpg"
draft: false

tags:
    - refactor
    - re-engineering
    - rewrite
    - product engineering
    - refactor vs rewrite 

categories: [ Tech ]
URL: "/2021/11/24/reengineer-vs-rewrite/"
---

We are engineers (can be safely generalised to humans), who at heart enjoy **building not extending/enhancing/improving**

*Disclaimer: doesn't mean we don't enjoy extending/enhancing. I strongly believe in the philosophy of -- **You touch it, you improve it!***

> This is driven by the fact - programmers think old code is messy as [Joel Spolsky](https://www.joelonsoftware.com/2000/04/06/things-you-should-never-do-part-i/) writes -- It’s harder to read code than to write it

Having said that, programmers use tonne of external libraries & modules to avoid re-inventing the wheel. And yet, if you ask them about the code he/she has inherited, the answer would be a mix of:

> **oh this is legacy code, has code smells, long functions, too many branches, no documentation, less tests, cannot seem to understand why this design was chosen**

Alarmingly, when the same programmer sits to write code, he/she would avoid writing documents in the name of following an Agile process (**no documentation - a mis-understood term**).

In my experience, every product build/ project starts with being fully Agile but as complexity increases, Agility starts to suffer. This leads to the 2nd law of thermodynamics: Entropy. Refer [Software Entropy](https://www.oreilly.com/library/view/the-pragmatic-programmer/9780135956977/f_0020.xhtml) - [@pragdave](https://twitter.com/pragdave) & [@PragmaticAndy](https://twitter.com/pragmaticandy). More on this in a separate post, lets get back to the problem and choices.

## What are the choices

In my experience, re-engineer (or better refactor) v/s re-write is no different than Buy v/s Build decision. Each choice has supporting facts and one must choose based on circumstances. Like [Neal Ford](https://twitter.com/neal4d) in the latest book -> [Software Architecture: the Hard parts](https://www.amazon.in/Software-Architecture-Modern-Tradeoff-Analysis/dp/1492086894) says:

> **every architectural decision involves trade-offs and our primary responsibility is making design decisions that consider those trade-offs.**

In this case, typically you end-up picking one or a combination of:
- build/ rewrite everything from scratch
- re-engineer/refactor the existing system
- rewrite and make two systems run in parallel to eventually strangle the old one

The pragmatic approach is to choose option #3, however, 

- it is slow (initial excitement will be to do a greenfield which eventually starts to get draining)
- always a moving target (although this will be true for big-bang rewrite)
- run two systems in parallel requires a lot of effort including production support

Irrespective, if the choice is to follow option #3 (which is always my default choice), make sure to involve **trusted customers** (for feedback loops and battle test new code), **sprinkle new cool features** (to keep excitement), celebrate the rewrite and avoid treating the team managing existing code as **side job-keepers**. 

## Our story/ What were we trying to do

We had an existing working system which was serving a few hundred thousand customers. It was a working application, however, team had constant complains about a few challenges:

- performance bottlenecks (it was a Java/Springboot based) with VueJS as UI
- new feature would take a lot of time to develop and launch
- had architectural/ design related issues (a lot of offline file exchanges, less driven by API contracts)

All of these can be solved with #3 - being pragmatic. Hence, the option to re-write was not an option.

No surprisingly, the team wanted a full rewrite. Hence, we started with an answer "**NO**" - not to rewrite, but, then, we put all the trade-offs to justify rewrite and eventually we took an org-wide decision to rewrite the system. 

## Why did we choose to rewrite

It is important to understand the choice of rewrite even though everyone was somewhere in agreement to avoid a full rewrite. We took a deeper stock of the challenges team was facing - symptoms of the problem (not how they manifest itself).

> Symptoms are deep-rooted which manifests itself in different ways.

We found that the design of offline batch file exchanges (no direct API integration) was conscious - due to the limitation of first set of customers. Additionally, since, this system was one of our first, it had nuggets of customer identity management, audit-ability, transaction management (which are clear boundaries for components) jumbled into one single module.

After detailing each trade-off and the associated challenges team faced, it was becoming convincing to start (still directionally) with option #3. One of the important design consideration here was Composability - assemble components from other parts of the organisation.

We set ourselves for rewriting (to prove the strong NO, I had initially), because we aligned it will help fix decisions from past, and it would let us move the product forward at the same time - for larger scale.

## How did it go

After the decision was done, we laid down a full scaled plan - time, blue-print of new architecture (although this evolved as we progressed, starting without a blue-print for such big activities always leads to disaster), features (including parity), capacity.

This might sound anti-Agile? (or does it?) but without this level of planning, it becomes fairly difficult to tap the progress and track the direction (moreover, if you were to deviate, without having a plan, deviating the direction becomes a difficult decision). Not surprisingly, with this level of detailed planning, it helped us become more convinced that the other two choices - refactor & strangle, would take more time (at least on-paper).

One of the first thing we did was, ring-fence the team and make them familiar with the design blue-print and product decisions. One of the important goal was to compose the components, reduce silos and build comfort in the engineers on the new system. We introduced cross-pollination among programmers to make sure everyone gets a flavour of all components - including exposing FE specialist with DB schema designs. Even though the team was new - they started to run at fast sustainable pace for months, building existing and new features. The decision to introduce a new set of features kept the team motivated.

> **Did we hit the timeline?**

NO, we were delayed but with the decision to include feedback loops with one existing and and a new customer helped the team. It helped product to re-jig some of their priorities shaping the system as a new avatar of the old (not a remake of the old).

## Summary & learnings

I have been part of 3 (the previous ones were massive) major rewrite and after each I conclude:

> **we should avoid full system re-write and yet been involved in 3 such journeys**

Always and always start with a "**NO**" and challenge yourself/your team to justify a re-write, and do it only when all trade-offs have been considered/ visible. There are many things to keep in-mind for a major re-write, some important tidbits to be aware:

- Complete buy-in from business/product/organisation is extremely crucial otherwise it starts to become a side project which hits team morale. It will be exciting in the beginning but after a while you have to actively deal with the problem of re-building/fixing bugs/no customer feedback till you've chunky stuff ready to launch - it starts to wear off the passion. Make sure internal launches are happening and new system is deployed to production (even though it has not users)
- Do a thorough planning including timelines for delivery. Make sure all aspects - design, functional, non-functional and launch related activities are documented and set as milestones. Track them in a cadence to check the progress. We started with bi-weekly but once in rhythm, can be done monthly. Keep in mind the fundamental principle:

> **there are 3 variables - scope, time, cost**

- Sprinkle some cool features that will keep the team excited. Debate on feature parity, treat this as a version 2 (or version X) of the system (as an upgrade), not just simple re-write.
- Design an alpha program. Engage existing and new customer as trusted members for battle testing on production.
- Make sure you have a ring-fenced team dedicated to work on this. You shouldn't end up changing the planned timeline - have re-write as the highest priority.

You would still run into issues, timeline won't be met - there will be challenging months that you’ll never get back but, hustle through the process, the rewards at the end are satisfying.

In all my 3 experiences, treating re-write as a religious org-wide event has a lot of benefits:

- Massive improvement in architecture of the new system (off-course this should be one of the reason to re-write). Becomes scalable, fault tolerant, highly observable. Infuse of new stack keeps the engineers excited to learn more and attain new personal milestones.
- Improvement in the delivery speed after re-write - Entropy hasn't hit yet. Mindset of legacy doesn't exist anymore. Ownership of the system.
- Engineering team builds trust with rest of the organisation (even though the delivery was delayed). While re-building and creating new features, the close interaction between various functions helped to build bridges.

Will I choose to re-write again, the answer would be "it depends" or rather a "NO". But, if I choose again, I would always look for strategic benefits in a re-write - for the customers, for the organisation and for the team.