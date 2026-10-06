# Activation checks

Whether new users reach the product's core action, and how fast. Stop and ask if the core action itself isn't named yet — every other check here depends on it.

### Is the activation moment tracked?

**Question:** Is the first core action defined, and does the product record an event when a user completes it?
**Where to look:** Code — the handler for the core action and any tracking call inside it. Tracking — whether that event appears in exports or queries. Database — the table the core action writes to (its first row per user is a fallback measure). Ask — which action the builder considers the moment a user "gets it".
**A finding looks like:** The core action writes to `expenses` but fires no event, so the share of sign-ups who activate is unmeasured in tracking.

### How many steps, fields and screens between sign-up and the core action?

**Question:** How many steps, form fields and screens sit between completed sign-up and the first core action?
**Where to look:** Code — the route or component sequence from the post-sign-up redirect to the core-action screen, and required fields on the way. Tracking — screen-view or step-completed events between `signed_up` and the core-action event, and drop-off at each step. Ask — the builder's own sense of the heaviest step, if no step-level tracking exists.
**A finding looks like:** Onboarding runs sign-up, plan picker, a three-field profile form, a team-invite screen, then the dashboard — the core action sits five screens in, with no step-level tracking to show where users stop.

### What share of sign-ups reach the core action, and how fast?

**Question:** Of users who sign up, what fraction complete the core action, and within what time?
**Where to look:** Tracking — a `signed_up` event and the core-action event joined by user id, with timestamps for time-to-activation. Database — first-row timestamp per user in the table the core action writes to, as a fallback when no event exists. Ask — the builder's own estimate, labelled reported, if neither exists.
**A finding looks like:** 62 of 340 sign-ups in the last 30 days (from `users.created_at`) have a row in `expenses` — an 18% activation rate — with no event marking the moment, so time-to-activation cannot be measured.

### Where do new users stop (last event before leaving)?

**Question:** For sign-ups who never reach the core action, what is the last event or screen recorded before they stop?
**Where to look:** Tracking — the last event per user id for the cohort that never fires the core-action event, grouped by that event name. Code — whether that screen has a known failure mode (a required field, a slow load, an external redirect). Ask — session recordings or support tickets the builder already has, if no per-user last-event query is possible.
**A finding looks like:** Of sign-ups who don't activate, 41 of 58 last fire `plan_picker_viewed` with no event after it — the funnel stalls at plan selection, not at the core action.

### Does a wall come before any value?

**Question:** Does a wall (sign-up, permission request, paywall) appear before a new user sees or does anything the product is for?
**Where to look:** Code — the first route after landing or install, and whether it is auth-gated, permission-gated (camera, location, notifications) or paywall-gated before any core-product screen renders. Ask — whether a value-first flow was considered and rejected, and why.
**A finding looks like:** The first screen after install requests notification permission before any product content renders; a new user is asked for access before seeing what the product does.

### What does a brand-new account see when it has no data yet?

**Question:** What does the core-action screen show for a user with zero rows of their own data?
**Where to look:** Code — the empty-state branch (or its absence) in the core-action screen's render logic. Database — whether a new account is seeded with sample rows. Ask — whether this has been checked by the builder at all.
**A finding looks like:** The dashboard component has no zero-state branch; a new account renders an empty table with column headers and no explanation of what to do next.
