# Referral checks

Whether users can bring other users in, and whether that path is tracked end to end. Never trigger a payout or credit path yourself; ask the builder to test it and report back.

### Can users share anything, and what does a recipient see?

**Question:** Is there a share action anywhere in the product, and does the shared thing open for a recipient without an account, or hit a login wall first?
**Where to look:** Code — a share button, share-link generator, invite or export route, and whether the route it opens is behind an auth guard. Database — a shares or invites table, or a shareable-resource id embedded in generated links. Ask — whether sharing exists at all outside the repo (a manually copied screenshot, a link pasted by hand).
**A finding looks like:** `POST /api/share` generates a link to `/shared/:id`, which redirects a signed-out visitor to `/login?next=/shared/:id` — the recipient cannot see the shared thing before creating an account.

### Are shares tracked end to end?

**Question:** Does tracking connect a share event to whether it was opened, and whether the opener went on to sign up?
**Where to look:** Tracking — a `share_created` event, a visit event on the shared-link route carrying the originating share id, and whether the resulting sign-up event captures that id. Database — a referrer or inviter foreign key on the users table. Ask — an export of share links and resulting sign-ups if no such join is queryable.
**A finding looks like:** Share links are generated and logged, but the route they open fires no event, and sign-up captures no referring-share id — no share can be connected to a resulting sign-up.

### Do invite or referral rewards exist, and do they fire?

**Question:** Is there a reward (credit, unlock, discount) for a successful invite, and does the code path that grants it actually run?
**Where to look:** Code — the handler meant to grant a reward on a referred sign-up or conversion, and what triggers it. Database — a credits or rewards ledger, and whether any rows exist tagged with a referral source. Billing — a coupon or credit applied through the billing provider's API, if the reward is monetary. Ask — whether a reward was ever promised in marketing copy without a matching code path.
**A finding looks like:** Marketing copy promises "invite a friend, get a free month"; no code path grants a credit on a referred sign-up, and the credits table has zero rows tagged with a referral source.

### Do free outputs carry attribution back to the product?

**Question:** Does anything a free user produces and shares outside the product (an export, a public page, a generated file) carry a visible mark or link back to the product?
**Where to look:** Code — the export or render path for any shareable output, and whether it stamps a watermark, footer link or attribution string. Ask — whether removing attribution is meant to be a paid feature, and whether that's enforced in the same code path.
**A finding looks like:** Exported PDFs carry no footer, watermark or link back to the product on any plan, free or paid.
