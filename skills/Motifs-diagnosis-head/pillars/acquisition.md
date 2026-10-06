# Acquisition checks

Where users come from, and what happens before they sign up. Stop and ask when acquisition numbers live only in an ad platform or analytics tool the session cannot reach — request an export rather than estimate.

### Is where a user came from captured at sign-up?

**Question:** Does the sign-up flow capture UTM parameters, referrer or campaign id, and store them against the new user?
**Where to look:** Code — the sign-up handler and any query-string parsing (`utm_source`, `utm_campaign`, `ref`, `referrer`) written into a session, cookie or the user record. Database — a source/campaign/referrer column on the users or accounts table, or a separate attributions table. Tracking — whether the identify or sign-up event carries these properties. Ask — which channels the builder already tracks by hand (tagged links, a spreadsheet) if none of the above holds.
**A finding looks like:** Sign-up writes `users.id`, `email`, `created_at` only; no code path reads or stores `utm_*` query params, so acquisition channel is unrecoverable after the fact.

### What share of visitors reach sign-up, per entry point?

**Question:** For each entry point (landing page, ad, referral link, store listing), what fraction of visitors complete sign-up?
**Where to look:** Tracking — a page-view or session-start event keyed by entry point, joined to a sign-up-completed event. Database — whether any visitor or session id exists before a user row is created. Code — any per-entry-point landing page or store-listing variant already in the repo. Ask — the builder's own numbers from an ads dashboard if no funnel event exists.
**A finding looks like:** Landing events carry no `entry_point` or `utm_source` property, so only a blended sign-up rate exists — no entry point can be compared to another.

### Does what the public pages promise match what the product does?

**Question:** Do the claims on marketing pages and store listings match the product's actual behavior in code and FEATURES.md?
**Where to look:** Public pages — marketing copy, pricing page text, store description. Code — the feature flag, plan check or config behind each specific claim. FEATURES.md — what is actually built. Ask — the builder, when a claim rests on a manual or off-repo process code can't confirm.
**A finding looks like:** The landing page promises "unlimited exports"; the export handler caps free accounts at 5/month, with no plan-tier qualifier on the claim.

### What can a visitor see or do before creating an account?

**Question:** Is there any product surface (demo, shared output, sample data) a signed-out visitor can use or view, and how far does it go before requiring an account?
**Where to look:** Code — routes not behind an auth guard, and whether they render real product output or only static/sample content. Database — whether a logged-out visit produces any real row, versus none at all. Tracking — a distinct anonymous session id used before sign-up. Ask — whether a public demo exists outside the repo (a hosted sandbox, a video).
**A finding looks like:** Every route under `app/(product)/` redirects an unauthenticated visitor to `/signup`; no page renders real product output pre-account.
