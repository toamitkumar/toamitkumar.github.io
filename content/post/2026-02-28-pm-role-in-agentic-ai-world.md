---
showonlyimage: true
title:      "The PM Role in the Agentic AI World"
subtitle:   "From Translator to Problem Shaper"
excerpt: "The translation layer between customers and engineers is compressing. When agents can convert well-formed problems into working code, PMs shift from writing specs for engineers to forming intent clearly enough that agents can act directly."
description: "The spec is becoming the product. Understanding the new PM skillset in the age of agentic AI."
date: 2026-02-28
author: Amit Kumar
image: "img/post-bg-coffee.jpeg"
draft: false

tags:
    - agentic AI
    - product management
    - AI agents
    - problem shaping
    - context curation
    - product engineering
    - AI in the Enterprise
    - developer productivity
---

## The Core Transformation: From Translator to Problem Shaper

The translation layer between customers and engineers is compressing. When agents can convert well-formed problems into working code, PMs shift from writing specs for engineers to forming intent clearly enough that agents can act directly. **The spec is becoming the product.**

### The New PM Skillset

**1. Problem Shaping (The Primary Skill)**

- Take ambiguous customer pain and shape it into something agents can act on
- Identify constraints that actually matter
- Articulate what success looks like concretely
- Hold ambiguity longer—explore the solution space before collapsing to a single approach

**2. Context Curation (The Hidden Skill)**

Quality of agent output = quality of context you provide. Maintain context docs with:

- The user, specifically (real details, not personas)
- The problem in their words (direct quotes, not synthesis)
- What good looks like (examples, not descriptions)
- What you've tried and why it failed
- Constraints that shape the solution
- How you'll know it worked (concrete metrics)

**3. Evaluation and Taste**

- Distinguish "technically works" from "actually solves the problem"
- Catch when agents confidently miss the point
- Develop judgment through reps—build, evaluate, iterate
- Determine "good enough to ship" vs "needs more work"

**4. Agent Topology Design**

- Structure agents like you'd structure a company
- Fine-scoped agents over monolithic "access everything" agents
- Insert friction where decisions are costly, reduce it where they're trivial
- Apply Principle of Least Privilege—split tasks so no agent holds the full "Lethal Trifecta"

**5. Risk & Policy Orchestration**

- Build policy agents that gate high-risk actions
- Create cleansing agents that filter inputs before decision-making agents
- Design for testable, independent chunks (Think → Research → Plan → Act)

### The Mental Model Shift

**Old:** PM → spec → engineers build → PM reviews → iterate (weeks)

**New:** PM → builds with agents → evaluates → iterates quickly → engineers make production-ready (hours)

You're not describing what you want and hoping it comes back right. You're shaping it directly in real time. Engineers become collaborators on production-readiness rather than translators of intent.

### The Amplification Reality

AI is a multiplier of existing organizational practices—it amplifies both strengths and weaknesses. When implementation barriers drop, the bottleneck shifts upstream. **The scarce resource isn't engineering capacity anymore. It's knowing what's actually worth building.**

### The Speed of Shipping

The cycle times that used to define product development—quarterly planning, monthly sprints, weekly releases—are compressing into something closer to continuous deployment of ideas. When the implementation barrier drops this fast, the bottleneck shifts upstream.

Every major AI company is shipping at unprecedented pace. The time between "I know what we should build" and "here it is" has collapsed. But the work of knowing what to build didn't get easier. It got more important.

### Getting Started

If you're a PM who hasn't worked this way yet:

1. **Pick a small problem you actually have.** Not an imaginary one. Something that's annoying you right now.

2. **Spend 30 minutes writing context before you prompt.** See the context curation section above for the full list.

3. **Point an agent at it and watch what happens.** Don't expect perfection. Expect a starting point. React to it. Guide it. Iterate.

4. **Do this ten times.** With different problems. Different levels of complexity. You'll develop intuition for what works, what context matters, how to evaluate output.

### Think in Iterations

Let the first version be wrong. Don't try to get it perfect in your head before you start. Give the agent rich context about the problem, then let it take a rough first pass. See what comes out. React. Iterate.

You'll learn more from "that's not quite right because..." than from trying to think through every edge case upfront. Build two or three completely different approaches just to see which one feels right when you use it. That used to be expensive. Now it's a Tuesday afternoon with a few parallel agents.

### What Gets Automated vs What Becomes More Valuable

**Automated:** Translating customer needs into documents for engineers (that's a workflow)

**More Valuable:** Understanding problems so deeply that the right solution becomes obvious to you and the agents you work with

The PMs who thrive will be those who master problem understanding, user empathy, judgment, and taste—these were always part of the job. Now they're becoming the whole job.

### The Question Every PM Should Ask

When the translation layer disappears, what's left?

For the best PMs, the answer is everything that actually mattered. Understanding the problem. User empathy. Judgment. Taste.

If your job was mostly translating customer needs into documents for engineers, that's a workflow. Workflows get automated.

If your job was "understand problems so deeply that the right solution becomes obvious," you're more valuable than ever. Agents amplify that understanding into shipped product faster than any team ever could before.

---

**References:**

[1] [Martin Fowler - Fragments: February 25](https://martinfowler.com/fragments/2026-02-25.html)

[2] [How organizations are currently using AI - Laura Tacho](https://www.youtube.com/watch?v=LOHgRw43fFk)

[3] [Agentic Engineering Patterns - Simon Willison](https://simonwillison.net/2026/Feb/23/agentic-engineering-patterns/)

[4] [Mitigating agentic AI security risks - Korny Sietsma](https://martinfowler.com/articles/agentic-ai-security.html#split-tasks)
