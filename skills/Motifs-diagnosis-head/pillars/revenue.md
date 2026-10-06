# Revenue checks

Where money changes hands: pricing, trials, failed payments and limits. Production consent in SKILL.md covers every query here, billing included.

### Does the free/paid boundary in code match PRODUCT.md?

**Question:** Does the actual gating in code (what's locked, what's free) match what PRODUCT.md states the offer to be?
**Where to look:** Code — the entitlement check gating each feature (`hasAccess`, `isPro`, a plan-tier or feature-flag check). PRODUCT.md — the stated free/paid boundary. Ask — when PRODUCT.md doesn't exist, end this check as can't diagnose — needs PRODUCT.md.
**A finding looks like:** PRODUCT.md states exports are a paid feature; the gating check tests `user.emailVerified` only, with no plan check — free verified users can export.

### Where does the paywall appear, and is a view tracked?

**Question:** At what point(s) does a paywall or upgrade prompt appear, what triggers each, and does a "paywall shown" event fire?
**Where to look:** Code — every route or component that renders a paywall or upgrade modal, and the condition that triggers it (a limit check, a route guard, an onboarding step). Tracking — a `paywall_viewed` event or equivalent, and whether it carries the trigger or placement as a property. Ask — the builder's own mental model of where the paywall shows, to check against what code confirms.
**A finding looks like:** A paywall modal renders from three call sites (an onboarding step, a usage-limit hook, a locked-feature click), but only the onboarding call site fires a tracking event — the other two triggers are invisible in tracking.

### What happens when a trial ends?

**Question:** Is there a defined product state for "trial just ended," and does a reminder go out before the first charge?
**Where to look:** Code — the trial-expiry check and what the user sees at that moment (a specific screen vs. a generic error or blank paywall). Billing — a scheduled reminder or webhook (e.g. Stripe `customer.subscription.trial_will_end`) and whether anything handles it. Tracking or provider logs — delivery confirmation for any pre-charge reminder. Ask — whether a reminder was ever planned.
**A finding looks like:** No handler subscribes to `trial_will_end`; the expiry check only gates access on the next request, with nothing sent before the card is charged.

### What happens when a payment fails?

**Question:** On a failed charge, does the product retry, notify the user, and allow a grace period before cutting access?
**Where to look:** Billing — the failed-payment webhook (e.g. Stripe `invoice.payment_failed`, Polar's equivalent) and what the handler does with it. Code — any grace-period flag or delayed-downgrade logic tied to subscription status. Tracking or email logs — a dunning email actually sent. Ask — whether this path has been tested with a test card.
**A finding looks like:** The `invoice.payment_failed` handler sets `status` to `past_due` and does nothing else — no retry, no email, no grace period before the next access check cuts the user off.

### What happens when a usage limit reaches zero?

**Question:** When a metered limit (seats, exports, messages, credits) hits zero, what does the user see, and can they still use anything?
**Where to look:** Code — the limit-check branch at the point of use, and what it renders at zero. Database — the counter or quota column, and whether it decrements correctly (off-by-one, wrong reset cadence). Tracking — a `limit_reached` event. Ask — whether hitting zero has been manually tested recently.
**A finding looks like:** At zero exports left, the export handler returns a generic "Something went wrong" error with no mention of the limit and no upgrade path.

### What share of trials convert to paid?

**Question:** Of trials started in a given window, what fraction convert to a paid subscription, from billing data?
**Where to look:** Billing — trial-start and subscription-activation records for the same customer or subscription id, over a stated window (subscription status transitions in Stripe, or the equivalent in Polar). Ask — an export of trial starts and outcomes if the billing provider isn't queryable in-session.
**A finding looks like:** 14 of 47 trials started in the last 60 days (from the billing export) converted to paid — too close to the 30-user floor to break down further by plan.
