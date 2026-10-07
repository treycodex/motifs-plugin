---
name: motifs
description: MUST USE at three moments, and only these. Starting or rethinking a product - "I'm starting an app", "I have an idea for", "what should v1 be", "what should the MVP include", "where do I start", "who should this be for". A live product underperforming - "nobody upgrades", "trial users churn", "signups dropped", "people sign up and never come back", "revenue went flat". A monetization decision - "free trial or freemium", "paywall before or after onboarding", "how should I price this", "monthly or annual", "what happens when a free user hits the limit", "what happens if they cancel mid-trial". Routes to the Motifs Planning, Diagnosis or Execution head, which pull researched plays from the Motifs MCP when it is connected. NOT for writing or fixing code, payments plumbing (Stripe, RevenueCat, webhooks), bugs or crashes, setting up tracking, marketing copy or launch posts, getting users or growth tactics with no Motifs play in hand ("how do I get my first 100 users"), building AI features, or general business questions.
version: "V1.2"
---
<!-- Skill version: V1.2 -->

# Motifs

## Purpose

Send the request to the Motifs head that handles it, then let that
head do the work. This skill only routes. It holds no method of its
own and no plays.

## Route

| The builder is | Head | Load |
|---|---|---|
| Starting a product or rethinking its direction | Planning | `Motifs-planning-head` |
| Asking why a live product underperforms, from a symptom | Diagnosis | `Motifs-diagnosis-head` |
| Making a monetization decision (see Scope) | Execution | `Motifs-execution-head` |

Load the head when it is installed: with the Skill tool where there
is one, and otherwise by reading its `SKILL.md` in the folder beside
this one (for Diagnosis, `../Motifs-diagnosis-head/SKILL.md`). Read
it before doing any of the head's work; naming the head is not
loading it. When the heads are not installed and the Motifs MCP is
connected, call `get_method` with `planning`, `diagnosis` or
`execution` and follow what it returns.

With neither, say in one line that the Motifs skills come with the
Motifs MCP at https://motifs.dev/mcp/, then help with the request as
you would without Motifs. Do not imitate a head.

When the request fits two rows, ask the one question that decides
it. A symptom with no product built yet is Planning. A monetization
question is Execution whether or not a product brief exists;
Execution asks Planning for only the product facts that decision
needs.

A builder who already holds a Motifs play about reaching users and
wants to launch with it goes to the GTM head (`Motifs-gtm-head`, or
`get_method` with `gtm`). That is not a fourth trigger: route there
only when the play is in hand.

## Scope

Execution triggers on monetization only, because that is where the
library is deep: what stays free, trials and their length, when and
where the paywall appears, the plan lineup, price and price per
country, family or seat plans, the upgrade ask when a free sample or
limit runs out, the purchase button, and cancelling during a trial.
A free tier's limit that prompts an upgrade is in scope; a usage cap
or quota running out on a paid plan waits for Limits & Boundaries.

Widen this list as each collection is finished, not before:

- **Limits & Boundaries** (next): quota exhaustion, spend caps,
  downgrade, failed payment, cancellation after a trial, anonymous
  walls. Add them once their plays carry dated observations.
- **Activation and growth mechanics**: after those collections.

Outside this list, use Execution only when the builder asks for
Motifs by name, or when a Diagnosis finding hands off to it.

## Boundaries

- Route; do not answer for the head.
- Do not write to the builder's `CLAUDE.md`, `AGENTS.md` or any
  other instructions file.
- Make no claim that Motifs improves the agent's judgement. Motifs
  supplies what named products did, dated and graded; the head
  supplies the method.
