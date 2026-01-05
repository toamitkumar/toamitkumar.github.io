---
showonlyimage: true
title:      "From Cheap Code to Real Change: What 2026 Demands"
subtitle:   "Agentic and adoption"
excerpt: "2026 will be about whether we reshaped our systems enough to let it matter."
description: "Code got cheap. The real constraints became visible. 2026 won’t be about discovering agentic AI."
date: 2026-01-03
author: Amit Kumar
image: "img/AIcode-meets-resistance.jpeg"
draft: false

tags:
    - agentic AI
    - cheap code to real change
    - excellence
    - amdahl’s law
    - product engineering
    - enterprise engineering
    - AI in the Enterprise
    - developer productivity
    - organisational change

categories: [ Transformation ]
URL: "/2025/01/03/from-cheap-code-to-real-change-what-2026-demands/"
---

## 2025: When Code Became Cheap — and Everything Else Became Visible

2025 is the year code stopped being the scarce thing.

With agentic development tools: Claude Code, Codex CLI, Gemini CLI, and others - engineers can now generate huge amounts of software: prototypes, migrations, refactors, tests, docs, analysis scripts, and all the glue work we used to put off. The daily experience of programming has shifted. Less time typing, more time directing and reviewing.

But inside a large enterprise, it became clear very quickly that cheap code doesn’t automatically mean faster delivery.

What it really did was expose everything else.

As we move into 2026, the gap is no longer between teams that “use AI” and those that don’t. It’s between organisations that can absorb a surge in change end-to-end, and those that still get stuck in the same old places: reviews, testing, releases, and operational risk.

The bottleneck moved. **Most of our systems didn’t.**

## Coding Got Faster. The System Didn’t.

Once coding speed jumps, the slowest part of the system becomes impossible to ignore.

In practice, throughput is limited by things like **unclear requirements, slow product decisions, review bandwidth, flaky and manual testing, nervous releases**, and what happens when something breaks in production. In 2026, the real difference between engineering organisations won’t be who adopted AI first, it’ll be who managed to raise that ceiling across the whole delivery pipeline.

I used most of the major agentic tools as they came out last year. The shift was obvious. Less `I’m writing code,” more “I’m lining up work, checking outcomes, and steering multiple threads at once.` In some areas, it already feels normal to assume that most new code is AI-generated, with humans setting direction and taking responsibility for what ships.

That’s a big change. And inside a large enterprise, it ripples everywhere.

## Adoption in 2025 Was Real — but Uneven

From the inside, 2025 didn’t feel like a clean, dramatic transformation. It felt messy.

My startup colleagues moved faster because they could. Clean codebases, clear ownership, fewer guardrails. Agents could operate end-to-end without much friction.

Large enterprises (like ours) are different by default.

For us, adoption in 2025 was patchy. Some teams went deep very quickly. Others barely touched it. The reasons weren’t mysterious. There was skepticism about correctness and maintainability. Real fear around security, compliance, and unintended consequences. And plenty of simple unfamiliarity—many engineers didn’t yet know what these tools were genuinely good for.

But the biggest constraint wasn’t mindset. **It was the systems themselves.**

## When Agents Hit Real Enterprise Code

Most of our systems aren't designed to be understood easily, `even by humans`.

Years of growth leave behind tightly coupled services, implicit contracts, shared databases, and “**don’t touch this**” areas guarded by folklore rather than tests. Domain knowledge lives in people’s heads, old tickets, and half-maintained documents. Documentation, when it exists, often describes what the system was supposed to be, not what it is.

*Agents struggle here for the same reason new joiners do.*

They can generate code just fine. What they can’t do—yet—is safely change a system whose boundaries and invariants are invisible. We saw this repeatedly. Agents were brilliant at greenfield work or well-contained components, and far less reliable when pointed at core, legacy flows.

**That wasn’t a failure of the tools. It was a mirror.**

Note: this is Amdahl’s Law, it states that the overall speedup of a system is limited by its slowest component. 

Software delivery obeys this law just as rigidly as any distributed system. If writing code is only a fraction of the end-to-end cycle—and in most large organisations it is—then making it dramatically faster yields only marginal gains unless everything else evolves with it.

## What We Actually Did in 2025

Despite all of this, 2025 wasn’t a year of paralysis. It was a year of pragmatic experimentation.

Inside our organisation, adoption started small and bottom-up. We ran internal AI hack events to lower the barrier to entry and let teams explore without pressure. The goal wasn’t immediate transformation—it was curiosity, confidence, and shared learning.

Most teams started with low-risk, high-value use cases:

* Improving and generating documentation
* Writing unit tests around existing code
* Creating migration scripts and analysis tools
* Refactoring small, well-bounded areas
* Assisting with code reviews
* Prototyping ideas without committing them to production

These weren’t headline-grabbing changes. But they mattered. They fit into existing ways of working, delivered visible value, and—crucially—helped people build trust in the tools.

## Productivity Didn’t Explode — and That’s Honest

By the end of 2025, many engineers felt more productive. But not 10x productive.

That gap makes sense. The tools can generate far more code than our delivery systems can safely process. Reviews still take time. Tests still fail. Releases still need confidence. When those don’t change, output just queues up.

The bigger gains are still ahead.

---

## What 2026 Is For

If 2025 was about exposure, 2026 is about redesign.

The biggest wins will come from work that isn’t glamorous: improving review bandwidth, making tests deterministic and fast, building confidence in releases and rollbacks, clarifying ownership, and speeding up product decisions.

Equally important is making our systems legible — not just to people, but to agents. Clear boundaries, reproducible environments, documentation written for change, and observability that actually tells you what’s going on.

The irony is that agents will help with this work too. They’re very good at pointing out where context is missing.

---

## 2025 Was the Year We Saw the System

From the inside, that’s what 2025 really felt like.

Code got cheap. The real constraints became visible. And instead of pretending otherwise, many large enterprises—including ours—started the slow, necessary work of adapting.

2026 won’t be about discovering agentic AI.

It’ll be about whether we reshaped our systems enough to let it matter.