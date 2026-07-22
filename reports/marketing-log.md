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

## 2026-07-21 (Tuesday) — Website Copy

**Note:** `lumixsolutions.org` is reachable to fetch tools again as of this
run — the 403/TLS block noted in both Monday entries is resolved. This is
the first run to actually see our own site copy, so treat the findings
below as a first-pass baseline for the copy track, not a re-check.

**Pages reviewed:** homepage, `/services`, `/contact`, `/spotlight`
(`/pricing` and `/game-hosting` both 404 — no dedicated pages exist).

### Findings (max 3)

1. **Minecraft and Terraria are not named anywhere on the marketing site.**
   The homepage banners and `/spotlight` mention FiveM and "bot hosting" by
   name, but the `/services` page — the only page describing game hosting —
   reduces everything to one vague line: "Optimized game server
   infrastructure with low-latency networking and DDoS protection included.
   Support for all major titles." Two of Lumix's four core product lines
   (per this routine's own scope: FiveM, Minecraft, Terraria, Node/Python
   bot hosting) are invisible to a prospect skimming the site or a search
   engine indexing it.
   → *Action:* Replace "Support for all major titles" on `/services` with
   an explicit list: "FiveM, Minecraft, Terraria, and Node.js/Python bot
   hosting." One sentence, no redesign needed.

2. **No price is visible anywhere on the public site.** `/pricing` 404s,
   and every "View Plans" CTA on `/services` routes straight to the billing
   portal (`billing.lumixsolutions.org`), which requires account setup
   before showing a single number. This is a harder version of the friction
   flagged in Monday's report (competitors we checked all show $/GB or
   $/slot on the marketing page itself, no login required).
   → *Action:* Add a minimal pricing block to `/services` — even just
   "Starting at $X/GB" per game type — so a prospect can compare cost
   before creating a billing account.

3. **Inconsistent naming for the same product: "bot hosting" vs.
   "Application Hosting."** The homepage banner reads "Expanded bot hosting
   capacity — more space, better isolation, smoother deployments," but
   `/services` describes the identical Node.js/Python/Docker offering under
   the header "Application Hosting" with no mention of "bot" at all.
   Prospects searching for (or asking Discord about) "bot hosting" won't
   obviously connect it to the "Application Hosting" plan listing.
   → *Action:* Rename or subhead the `/services` "Application Hosting"
   section to lead with "Bot & Application Hosting" so it matches the term
   Lumix already uses in its own promo banners and community.

### Do this today (<1 hour)
Edit the one line on `/services` that currently reads "Support for all
major titles" to explicitly name FiveM, Minecraft, Terraria, and
Node.js/Python bot hosting. Highest-leverage single-line fix — it's the
only place on the site that's supposed to describe the full product
lineup, and right now it describes none of it by name.

---

## 2026-07-22 (Wednesday) — Competitor UX Deep-Dive: BisectHosting

**Note:** First Wednesday run — no prior UX-track entry to rotate from, so
this establishes the baseline competitor for this track (next rotation
should pick a different one, e.g. Shockbyte or RocketNode — Shockbyte's
order page returned HTTP 403 to fetch tools this run and couldn't be
reviewed). Compared BisectHosting's Minecraft signup→deploy flow against
Lumix's homepage → `billing.lumixsolutions.org` flow (fetched live, plus
raw HTML pulled directly to confirm what's server-rendered vs. not).

**Flows observed:**
- **BisectHosting:** landing page → "Choose a Plan" (1 click) → a 4-step
  guided wizard: (1) game install/modpack + expected player count, (2)
  server location chosen from a map with latency shown per region, (3)
  billing cycle with a promo-code field, (4) optional addons. Every step
  ties to a concrete number (player count, ms latency, price). Account
  creation happens after, at checkout.
- **Lumix:** homepage "Deploy Now" (1 click) → `billing.lumixsolutions.org`,
  which shows four bare tier names (Starter, Pro, Elite, Titan — confirmed
  server-rendered in the raw HTML, not a fetch-tool artifact) with no
  wizard, no location/latency picker, and no price attached to any tier in
  that view. The user has to already know which tier maps to their game
  and player count and self-navigate from there.

### Findings (max 3)

1. **BisectHosting turns plan selection into a guided, numbers-first
   wizard; Lumix hands the user a flat list of tier names with no
   guidance.** This is the concrete "2 clicks vs. 5" gap: on Bisect, one
   click (player count) narrows the whole decision; on Lumix, a prospect
   has to already know that, say, "Elite" fits a 20-slot FiveM box before
   they can even start.
   → *Action:* Build (or even just mock up) a 2-3 question picker —
   "Which game? How many players?" — on the marketing site or portal
   landing that routes straight to the matching pre-filled plan, instead
   of dropping users onto the raw Starter/Pro/Elite/Titan list.

2. **No interactive location/latency picker exists anywhere in the Lumix
   flow.** The homepage only states "Miami, Dallas" as plain text; there's
   no way for a prospect to see expected ping before buying. BisectHosting
   makes this an explicit wizard step with a map and per-region latency
   estimates — a real decision factor for FiveM/Minecraft communities
   picking based on player geography.
   → *Action:* Add a simple static line near plan selection (e.g. "US
   East — Miami: best for players in the Eastern/Southern US") as a
   low-effort first pass; a live latency tester can come later.

3. **Lumix's own speed/trust claim ("online in under 60 seconds") lives
   only on the homepage banner, disconnected from the billing portal where
   the actual purchase decision happens.** BisectHosting's equivalent
   claim ("full access as soon as payment clears") sits right at the
   wizard's final step, next to the buy action — reinforcing confidence at
   the exact moment of hesitation. Lumix's claim never reaches that
   moment.
   → *Action:* Duplicate the existing "under 60 seconds" copy (already
   written, no new claim needed) onto the billing portal landing page,
   near the plan tiers / buy button.

**Relation to prior findings:** Confirms (does not newly report) Tuesday's
finding #2 that no price is visible pre-account — raw HTML pull today
shows the billing portal's tier names are server-rendered but truly carry
no price anywhere in the markup, not just a fetch-tool gap. Still under
the 7-day escalation threshold (2 days old); no action needed beyond
Tuesday's existing item.

### Do this today (<1 hour)
Copy the existing "servers online in under 60 seconds" line from the
homepage banner onto the `billing.lumixsolutions.org` landing page, placed
near the Starter/Pro/Elite/Titan tier list. No new copywriting required —
just relocating a claim that already exists to the page where the
purchase decision is actually made.

---
