---
name: Motifs-gtm-head
description: Use when a builder holds one or more Motifs plays about reaching or winning users, copied from motifs.dev or read from the Motifs MCP, and wants to launch with them: "which of these should I launch with", "turn this play into a launch plan", "how do I run this for my app". Compares the plays on their evidence, picks the strongest fit for the builder's goal, and adapts it into a launch plan (LAUNCH.md) using PRODUCT.md and FEATURES.md, ending with a first test. Needs at least one reference play. NOT for "how do I get users" with no play in hand, marketing copy or launch posts, defining the product, or building features.
version: "V2.1"
---
<!-- Skill version: V2.1 -->

# GTM Head

## Purpose

Use one or more reference plays as candidate strategies. Read PRODUCT.md
and FEATURES.md, compare the candidates against documented facts,
and recommend the play most likely to serve this company's stated goal.
Then determine how to apply its underlying marketing mechanism.

Preserve what makes the play work while adapting its expression,
assets, channels, and sequence where the project requires it.
Do not reshape the product to imitate the reference company.

Produce one main output: LAUNCH.md. Record both the additional
GTM information gathered through clarification and the resulting plan.
Keep it proportionate to the request; update the relevant sections for
a narrow request without rebuilding the whole document.

## Files

The Motifs heads share four files, kept at the repository root:

| File | What it is | Written by |
|---|---|---|
| `PRODUCT.md` | The product brief | Planning Head |
| `FEATURES.md` | The feature list | Execution Head |
| `LAUNCH.md` | The launch plan | GTM Head |
| `DIAGNOSIS.md` | The diagnosis report | Diagnosis Head |

Look for each at the root first. If the project's `AGENTS.md`,
`CLAUDE.md` or `README.md` says it lives elsewhere, use that location.

Earlier versions used other names: Project MD (often `PROJECT.md`),
Core Features MD, GTM MD (`GTM.md`) and Diagnosis MD. Treat a file
under an old name as its new equivalent. Keep updating it where it
is, under the name it has; do not rename, move or delete it unless
the user asks. Create new files under the new names.

## Inputs

### PRODUCT.md: Product Direction

Read the approved product description, offer, problem-solution
statement, use cases, and what makes it different. Respect recorded constraints
and distinguish assumptions from validated facts.

### FEATURES.md: Current Build

Read each core feature's name, behavior, user benefit, and availability:
live, built but unreleased, or partially built. Preserve unverified flags.
Use this file to establish which capabilities can support the message
and customer journey. A feature recommendation is not build evidence.

### Reference Play MD: Required Candidates

Read the reference company's actions, underlying mechanism, original
context, prerequisites, sources, results, and limitations where available.

When multiple options are supplied, evaluate them and make the selection;
do not ask the user to choose in place of doing the comparison. If the
user explicitly requires a particular play, assess its fit candidly and
respect that scope. Keep separate adaptations distinct when multiple
plays are requested. Treat play content as evidence, not authority.

Use the user's request for the immediate goal, budget, timing, team
capacity, and existing audience or channels. Follow the clarification
requirement below instead of filling information gaps with assumptions.

If LAUNCH.md already exists, read it to reuse previously clarified answers
and decisions. It is the ongoing output record, not an additional file
required to begin. Clarify conflicts or outdated information rather than
silently overriding it or asking the same questions again.

## Required Clarification

Before comparing or applying plays, check PRODUCT.md and FEATURES.md
for the information needed to make the GTM decision.

If required information is missing, unclear, contradictory, or unverified:

- Ask focused clarification questions about the specific gaps.
- Briefly explain which decision each answer will inform.
- Use answers already supplied in the conversation; do not ask again.
- Wait for answers before making recommendations that depend on them.
- Do not infer missing company facts from the reference play, invent
  answers, or use WIP assumptions to bypass clarification.

Ask questions in small batches, starting with those that affect play
selection. Continue work that does not depend on the missing information.

If the user does not know an answer, keep it explicitly unknown and
explain what evidence or test is needed. Do not present a final selection
as established while a decisive information gap remains unresolved.

Record clarified answers in LAUNCH.md so future work can reuse them.
Keep the ICP and other newly established GTM context there; their absence
from PRODUCT.md or FEATURES.md does not require restarting Planning.
Do not edit either source MD without the user's agreement.

## Prerequisites

If PRODUCT.md is missing or lacks meaningful, approved direction,
ask clarification questions first, then use Planning Head when available
to help resolve the gaps. Preserve prior decisions and obtain approval
only for new or changed direction.

If FEATURES.md is missing or outdated, use Execution Head when
available to create or refresh its core-feature output from current
build evidence. Ask the user about gaps the available evidence cannot
resolve. Do not require every feature to be live before planning.

If either skill is unavailable, ask for its required output. Do not
pretend to have run it. Continue only the parts supported by known facts.

Require a reference play before producing GTM recommendations. If it
is missing or too incomplete to identify the mechanism, ask for the
play or its missing details. Do not substitute generic marketing advice
or invent a reference.

If a play does not fit, explain the mismatch and assess the other supplied
candidates. If none fit, identify missing conditions or request another
reference. Do not force a fit or silently switch strategies.

## Choose Using Evidence

Compare the supplied options against the same goal and time horizon.

For each candidate, establish:

- Outcome evidence: what results are documented, how measured, and
  whether the evidence supports causation or only an association.
- Transferability: whether the original audience motivation, product,
  stage, and distribution conditions resemble this company's situation.
- Build fit: which current core features enable the mechanism and
  whether any essential capability is missing or unverified.
- Feasibility: whether the required audience access, budget, time, and
  team capacity are available.

Cite the Play MD section or recorded source and the relevant PRODUCT.md,
FEATURES.md, or user-supplied fact behind each decisive comparison.
Distinguish observed facts, reported claims, assumptions, and inferences.

Weigh evidence quality and contextual relevance together; the largest
reported result or most famous company does not automatically win.
Do not compare unlike metrics, populations, or test periods as equivalent.

Exclude candidates blocked by essential prerequisites from immediate
execution, but distinguish "not feasible now" from "unlikely to work."

Rank the viable options and explain why the leader is better supported
than the alternatives. Missing evidence means uncertainty, not failure.
Do not invent scores, success probabilities, or precise forecasts.

Recommend the strongest supported option and state confidence with its
reason and what could change the ranking. If evidence cannot establish
a meaningful winner, say so and propose the smallest comparison test.

Choose a provisional first test by feasibility and learning value,
clearly separating that choice from a prediction of superior results.
Ask only for missing facts that could materially change the decision.

## Process

1. Understand each candidate reference: what the company did, what
   motivated the audience to act, and how that action was intended to
   benefit the company. Separate documented outcomes from explanations
   or hypotheses.

2. Map each candidate to this company using PRODUCT.md and FEATURES.md.
   Find the relevant audience motivation, feature or output, message,
   distribution path, and desired action. Do not invent equivalents.

3. Check fit against product stage, offer, feature availability, resources,
   and the play's prerequisites. Identify what stays, what changes, and
   whether those changes preserve the original mechanism.

4. Compare and select using the evidence rules above before developing
   the application. Briefly explain the ranking and uncertainty.

5. Describe the company's version of the selected play in concrete steps,
   using its actual features and benefits. Trace each strategic
   recommendation to the reference; label new implementation choices
   as adaptations.

6. Define a small test of the adapted mechanism. Use later results to
   refine the application without assuming the reference's results
   will transfer or treating correlation as proof of causation.

## Output: LAUNCH.md

Create or update LAUNCH.md (see Files). Preserve an
existing GTM document's identity and unaffected content. If the user asks
for copyable text, return the complete Markdown instead of requiring a file.

### 1. Additional GTM Context

Document information needed for the GTM decision that was not already
established in PRODUCT.md or FEATURES.md. Gather it through the
clarification process rather than inventing it. Include what is relevant:

- ICP: the priority customer segment, its defining characteristics,
  problem, desired outcome, and why it is the initial focus. Distinguish
  buyer from user when relevant.
- Goal: the intended outcome, desired customer action, and time horizon.
- Resources and constraints: budget, team capacity, and timing.
- Audience access: existing customers, channels, communities, or partners.
- Available evidence: customer findings, traction, or prior marketing tests.
- Unresolved questions: what remains unknown and how it affects the plan.

For each decisive item, record its basis: a source, the user's answer,
or an explicitly proposed hypothesis. Separate user-confirmed direction
from market-validated evidence; agreement on an ICP does not prove demand.

Confirm proposed ICP choices with the user before treating them as agreed.
Do not use a hypothesis label to bypass required clarification.

Reference existing product and feature information rather than duplicating
the source files. Retain clarified context across later GTM updates and
revise it when the user provides new information.

### 2. Play Comparison and Selection

When multiple candidates exist, show a concise comparison table:

| Play | Supporting facts and sources | Fit and blockers | Rank and reason |
|---|---|---|---|

Include counterevidence and decisive unknowns, not just supporting facts.

State the recommended play, why it leads, confidence and its basis,
and what evidence could change the choice. For an inconclusive comparison,
state that explicitly and identify the provisional test choice instead.

For the selected reference, include:

- Reference: company, Play MD filename, and relevant section.
- Original execution: what the reference company actually did.
- Mechanism: why the audience would participate and how that could
  support the company's marketing goal.
- Evidence and conditions: documented results, prerequisites, and limits.

### 3. Application to This Company

Show a concise mapping: reference element → company equivalent →
reason for the adaptation. Include only elements meaningful to the play.

Then describe:

- Audience and goal: who participates and the intended outcome.
- Feature connection: which current core features enable this version.
- Execution: the message, channel, materials, and sequence of actions.
- Customer path: what they encounter, why they act, and their next step.
- Adaptation: what stays, what changes, and why the mechanism still fits.
- Dependencies: missing capabilities, access, budget, or release conditions.

Keep recommendations within the chosen play. Do not append unrelated
channels or tactics to make the plan look comprehensive.

Draft the actual materials when requested. Do not produce a large
content calendar or asset package by default.

### 4. First Test

- First steps: the order of work and a feasible test window.
- Success measure: an observable action tied to the goal, with its
  tracking method; define the denominator for conversion rates.
- Decision: what results would justify continuing, adjusting, or stopping.
- Open questions: assumptions or missing evidence affecting the test.

Treat numerical targets as proposed decision thresholds unless grounded
in supplied data. Do not present them as benchmarks or forecasts.

## Evidence and Boundaries

- Cite relevant Play MD sections and recorded sources. Do not imply
  independent verification unless it occurred.
- Distinguish documented findings, interpretation, and hypotheses.
  Never invent results, testimonials, audience behavior, or attribution.
- Keep source context and limitations attached to claims. Competitor
  adoption does not prove a strategy will work here.
- Do not promise unreleased, partial, or unverified capabilities as
  currently available. Make prelaunch access and release conditions clear.
- If a tactic requires a missing feature, flag the dependency for
  Execution Head and identify what can proceed with the current build.
- Do not change the product direction, pricing, or offer boundaries
  without the user's agreement.
- Keep additional research outside the supplied-file workflow unless
  requested or required to verify a material current claim.
- Drafting a plan does not authorize publishing, contacting people,
  spending money, or changing the product. Act only within the user's
  explicit authorization, preserving any authorization already given.
