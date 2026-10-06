# Retention checks

Whether users come back, and what happens when they don't. Production consent in SKILL.md covers every query here. Record aggregates only, never individual users' return dates.

### Can the product tell that a user came back?

**Question:** Does the product or tracking distinguish a returning user from a first-time one, tied to a stable identity across sessions?
**Where to look:** Tracking — an identify call keyed by a stable user id (not a device or session id) with a `first_seen`/`last_seen` or session-count property. Database — a `last_active_at` or `last_login_at` column, or a sessions table keyed by user id. Code — how a session resumes (cookie, token) and whether it ties back to one user id across devices. Ask — whether sign-in is passwordless in a way that could fragment identity (different email clients, link forwarding).
**A finding looks like:** Sessions are cookie-scoped with no server-side `last_active_at` update; two visits ten days apart from the same user are indistinguishable from a first visit in the data available.

### What share of each cohort returns in week 1 and week 4?

**Question:** For users grouped by sign-up week, what fraction return at least once in week 1, and again in week 4?
**Where to look:** Tracking — any event with a user id and timestamp, grouped into weekly sign-up cohorts and checked for a later-week event. Database — timestamped rows in any table as a fallback signal of activity. Ask — an export of user id and event timestamps if no query access exists.
**A finding looks like:** Of the cohort that signed up in the exported range's first full week, 9 of 22 (below the 30-user floor for a rate) had any event in week 4.

### What brings users back, and is each one actually sent?

**Question:** What lifecycle messages (email, push, reminders) exist to bring a lapsed or scheduled user back, and does the code path for each one actually fire?
**Where to look:** Code — the scheduled job, cron or worker behind each message type, and the template or push call it sends. Tracking or provider logs — delivery or open events (an email-provider webhook, a push-provider receipt) in the last 30 days. Ask — the builder's own list of what's supposed to send, to check against what code confirms.
**A finding looks like:** The only lifecycle message is a welcome email sent at sign-up; no job, cron or worker sends anything to a user who has been inactive for any length of time.

### What happens when a user misses a session or returns after a long gap?

**Question:** Does the product treat a lapsed return differently from a normal session (a bonus, an easier restart, a repair offer), or identically?
**Where to look:** Code — any branch keyed on days-since-last-active or a broken-streak flag. Database — a streak or consecutive-days column, and whether it resets silently or offers a repair. Tracking — an event fired specifically on a lapse-return, distinct from normal session-start. Ask — whether this has been designed at all.
**A finding looks like:** `streak_count` resets to 0 on any gap over 24 hours with no code path offering a repair or grace day; a returning user sees the same session-start screen as a daily one.

### What happens at cancellation or downgrade, and is a reason captured?

**Question:** When a user cancels or downgrades, does the flow ask why, and is that reason stored anywhere?
**Where to look:** Code — the cancellation or downgrade handler, and any form or reason-select rendered before it completes. Billing — the cancellation webhook (e.g. Stripe `customer.subscription.deleted`, Polar's equivalent) and its payload. Database — a `cancellation_reason` column or a feedback table. Ask — whether reasons are collected outside the product (support email, a survey tool).
**A finding looks like:** The cancel button calls the billing API directly with no confirmation or reason step; the `subscription.deleted` webhook handler only updates `status`, storing no reason.
