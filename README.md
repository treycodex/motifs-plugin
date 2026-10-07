# Motifs for Claude Code

[Motifs](https://motifs.dev) is research-backed product and growth intelligence for
people building a product with a coding agent: what named products do, with graded
evidence and what it does not establish.

This plugin gives Claude Code:

- **The Motifs MCP**, at `https://motifs.dev/api/mcp/`. Any signed-in account can
  search; whole plays and playbooks are for members.
- **A router** (`motifs`) that sends a request to the right skill.
- **Four skills**: Planning, Diagnosis, Execution and GTM.

## Install

```bash
claude plugin marketplace add treycodex/motifs-plugin
claude plugin install motifs@motifs
```

Restart Claude Code, run `/mcp`, choose `plugin:motifs:motifs` and sign in once in
the browser. There is no API key.

If you already added Motifs with `claude mcp add`, remove it first
(`claude mcp remove motifs`), or its tools appear twice.

Update with `claude plugin marketplace update motifs`.

## When it starts

You do not call the skills by name. They start when you describe:

1. **A product you are starting or rethinking** ("I'm starting an app", "what
   should v1 be"). Planning asks a few questions at a time and, once you approve the
   brief, saves it as `PRODUCT.md` at your repository root.
2. **A live product that underperforms** ("nobody upgrades", "trial users churn").
   Diagnosis reads your code, tracking and billing and writes `DIAGNOSIS.md`.
3. **A monetization decision** ("free trial or freemium", "how should I price
   this"). Execution finds researched plays through the MCP, asks only what that
   decision needs to know about your product, and writes `FEATURES.md`.

GTM runs when you already hold a Motifs play and want to launch with it, and writes
`LAUNCH.md`. None of them triggers on writing code, payments plumbing, bugs,
tracking setup, marketing copy or AI features.

To call one directly: `/motifs:motifs`, `/motifs:Motifs-planning-head`,
`/motifs:Motifs-diagnosis-head`, `/motifs:Motifs-execution-head`,
`/motifs:Motifs-gtm-head`.

## About this repository

This is a release copy. The skills are written elsewhere and copied here on each
release, so changes made here are overwritten. Report problems at
[motifs.dev/feedback](https://motifs.dev/feedback/).
