# Lumix Solutions — Marketing & Competitive Review Log

This log tracks findings from the recurring competitive/marketing review routine.
Each entry is dated and tagged with the day's focus area. Findings are only
repeated across runs if they remain unfixed after 7+ days (escalation).

---

## 2026-07-20 (Monday) — Competitor Pricing & Plans

**Note:** First run of this routine — no prior log existed, so this is the
baseline entry. `lumixsolutions.org` returned HTTP 403 to automated fetch
tools (likely bot/Cloudflare protection), so our own current pricing/copy
could not be pulled programmatically this run — findings below are
competitor-side only; someone should eyeball our pricing page manually
against these (see "do this today").

**Competitors checked:** BisectHosting, Shockbyte, Apex Hosting, ZAP-Hosting, RocketNode

**Snapshot:**
- **BisectHosting** — flat ~$3/GB across all games (BisectOne plan), *unlimited player slots*, built-in txAdmin, free shared MySQL + phpMyAdmin, swap games anytime at no charge.
- **Shockbyte** — Minecraft only, ~$2.50/GB (Dirt tier $2.50 @ 1GB up to Titan $40 @ 16GB), unlimited NVMe storage & slots. Visible coupons: `TWITTER25` (25% off), `SHOCK10` (10% off for life).
- **Apex Hosting** — Minecraft only (no FiveM/RedM), ~$3.75/GB (2GB=$7.49, 8GB=$29.99). Code `APEX25` = 25% off first invoice on any billing cycle, +10% extra for quarterly.
- **ZAP-Hosting** — FiveM from ~$8.57/mo (slot-based, ~10¢/slot). Official Cfx.re/CFX partner (API access to artifacts, launcher listing priority). Permanent 20%-off voucher (full duration, not just first month).
- **RocketNode** — FiveM from $6.50/mo (cheapest entry point found) up to $62.50/mo; Minecraft RAM-tiered, mid-range pricing. Headline trust signal: "RocketGuard" DDoS protection quantified at up to 17 Tbps. One-click ESX/QBCore installers.

### Findings (max 3)

1. **Every competitor checked runs a visible, named discount code** — Shockbyte (`TWITTER25`, `SHOCK10` lifetime), Apex (`APEX25` + quarterly stacking), ZAP (permanent 20% voucher). A named code appears to be a category-standard trust/conversion cue, not just a discount mechanism.
   → *Action:* Confirm whether Lumix has a standing promo code visible on the pricing page and pinned in Discord. If not, add one evergreen code (e.g. `LUMIX10`) rather than relying on ad-hoc sales.

2. **RocketNode undercuts on FiveM entry price** ($6.50/mo) and **BisectHosting standardizes on flat $3/GB with unlimited slots** as its headline FiveM differentiator. Both give a customer an easy, legible number to compare against.
   → *Action:* Audit Lumix's FiveM plan's effective $/GB and whether slots are capped. If Lumix is priced above RocketNode's entry tier or has a slot cap where Bisect doesn't, either reprice the entry tier or reframe the comparison (e.g. lead with a spec/perf advantage instead of raw price).

3. **ZAP and RocketNode both quantify DDoS protection** (RocketNode: "17 Tbps") as a specific, citable trust signal rather than a vague "DDoS protected" claim.
   → *Action:* If Lumix has DDoS mitigation in place, get the actual capacity number from the infra/network provider and add it to the plan comparison table. If no hard number exists, that's worth flagging to the team as a gap.

### Do this today (<1 hour)
Open `lumixsolutions.org/pricing` side-by-side with BisectHosting's and RocketNode's FiveM pages and check three things: (a) is there a visible discount code, (b) what's the effective $/GB and is there a slot cap, (c) is DDoS protection quantified anywhere. Note any "no" — feeds directly into Tuesday's site-copy review.

---

## 2026-07-20 (Monday, same-day re-check) — Competitor Pricing & Plans

**Note:** This run fired a second time on the same calendar day as the baseline
above (hours apart). Nothing material changes on competitor pricing pages in
that window, so this entry is intentionally short — spot-checks only, no
repeat of the full snapshot.

- **`lumixsolutions.org` is still unreachable to automated fetch tools** —
  same known issue as the baseline run (bot/CDN protection resets the TLS
  handshake before any content loads; confirmed via WebFetch and raw curl
  through the proxy, both blocked at the TLS layer). Not new, but still
  unresolved — see escalation note below since it blocks every future
  Tuesday copy-review and every "check our own pricing" step until someone
  fetches it manually or allowlists this tooling.
- **RocketNode's DDoS figure re-checked and confirmed accurate**: the FiveM
  product page itself only surfaces "2 Tbps" (a single scrubbing-center
  figure), but their dedicated DDoS page and site-wide messaging confirm the
  headline "17 Tbps" total capacity cited in the baseline still stands — no
  correction needed to Monday's finding #3.
- **RocketNode also runs an active sitewide promo** ("Summer Sale," up to
  25% off, running through Sep 25) plus multiple standing coupon codes
  (`25OFF`, others). Baseline's finding #1 listed Shockbyte/Apex/ZAP as the
  competitors with visible codes; RocketNode should be added to that list —
  it's now confirmed 5/5 of the competitors checked run a visible discount
  mechanism. This strengthens (doesn't change) baseline finding #1; no new
  action needed beyond what's already logged.

**Escalation:** None yet — the site-fetch-blocked issue is still under a day
old (first observed this morning). Per the 7-day rule, this only gets
escalated as a standing blocker if it's still blocking automated review by
2026-07-27.

No new findings above the 3 already logged this morning. No action items
beyond the existing "do this today" from the baseline entry, which is still
outstanding.

---
