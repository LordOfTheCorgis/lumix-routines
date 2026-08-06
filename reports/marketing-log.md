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

## 2026-07-23 (Thursday) — SEO & Keywords

**Note:** `/services` (reviewed in Tuesday's copy pass) now 404s — the site
appears to have been restructured since Tuesday. Homepage now also lists
Palworld and BeamMP as hosting options, which weren't mentioned in any prior
run. Flagging as a site change for Tuesday's next copy-review rotation to
pick up; not itself an SEO finding. `/game-hosting` still 404s (same as
Monday).

**Method:** Pulled homepage + `/spotlight` (title tags, meta description,
headings), then searched the actual queries a prospect would type —
"fivem server hosting," "cheap minecraft server hosting," "terraria server
hosting," "discord bot hosting node.js python" — to see which competitor
pages/URLs show up and how they're titled.

### Findings (max 3)

1. **Every page's `<title>` tag is keyword-empty.** Homepage title is
   "Lumix | Lumix Solutions LLC"; `/spotlight` is "Spotlight | Lumix
   Solutions LLC." Neither contains a single hosting or game keyword. Every
   competitor ranking in this run's searches leads with the keyword in the
   title itself: "FiveM Server Hosting | Shockbyte," "Terraria Server
   Hosting | 24/7 Support | BisectHosting," "FiveM Server Hosting |
   RocketNode." Title tag is the single heaviest on-page ranking signal —
   right now Lumix's title could describe any company in any industry.
   → *Action:* Rewrite the homepage `<title>` to something like "Lumix
   Solutions | FiveM, Minecraft & Terraria Server Hosting + Bot Hosting."
   One tag, no redesign.

2. **No meta description exists on any page checked** (homepage,
   `/spotlight` — same absence Google's own crawler would see). Without
   one, Google auto-generates the search snippet from body text, which for
   Lumix's homepage is a vague engineering tagline ("Infrastructure built
   by engineers") rather than a keyword-rich, click-worthy summary.
   → *Action:* Add a one-line meta description per page, e.g. homepage:
   "FiveM, Minecraft, Terraria, and Discord bot hosting with DDoS
   protection and sub-10ms latency. Deploy in under 60 seconds."

3. **No dedicated landing page targets any single high-intent keyword.**
   Every competitor found in this run's searches has its own URL per game —
   `shockbyte.com/games/fivem-server-hosting`, `bisecthosting.com/terraria-
   server-hosting`, `rocketnode.com/game-server-hosting/fivem`. Lumix has
   no equivalent: `/services` and `/game-hosting` both 404, and everything
   lives on one homepage that can't simultaneously rank for "fivem server
   hosting," "minecraft server hosting," and "discord bot hosting" as
   separate searches. This is the structural reason Lumix won't surface for
   any of these terms regardless of title/meta fixes above.
   → *Action:* Stand up one dedicated page per core product (FiveM,
   Minecraft, Terraria, Bot Hosting) at a keyword-matching URL, even as a
   thin first pass (specs + price + CTA) — this is a bigger lift than
   today's items, worth scoping as its own task.

### Do this today (<1 hour)
Rewrite the homepage `<title>` tag from "Lumix | Lumix Solutions LLC" to a
keyword-inclusive version, e.g. "Lumix Solutions | FiveM, Minecraft &
Terraria Server Hosting + Bot Hosting." Single highest-leverage SEO fix
available in under an hour — every competitor checked already does this.

---

## 2026-07-24 (Friday) — Social & Community

**Note:** First Friday run for this track — no prior entry to rotate from,
so everything below is a first-pass baseline, not a re-check. Lumix's own
footer links five social channels (Discord, TikTok, YouTube, X, Instagram —
confirmed live via homepage fetch), which is more than most competitors
checked expose in one place. The gap found this run is not "we're missing
channels," it's that the channels don't appear to be doing anything.

**Method:** Searched for competitor TikTok/YouTube/Discord content
(BisectHosting, Shockbyte, RocketNode) and cross-checked engagement
patterns against Lumix's own linked accounts (`tiktok.com/@lumix.solutions`,
`youtube.com/@officiallumixsolutions`, `x.com/LumixSolutions`,
`instagram.com/lumixsolutionsllc`).

### Findings (max 3)

1. **Lumix's TikTok and YouTube accounts return no discoverable content,
   while every competitor checked has a real, indexed content trail.**
   BisectHosting has an active `#bisecthosting` TikTok tag with tutorial
   videos ("How to Setup a Server in Bisect Hosting," "How to Use Bisect
   Hosting Server") pulling real engagement. Shockbyte runs a dedicated
   YouTube Tutorial channel, split off from its main channel specifically
   to centralize support content. Targeted searches for Lumix's exact
   handles (`@lumix.solutions`, `@officiallumixsolutions`) surfaced nothing
   — no videos, no follower signal, nothing indexed. (Caveat: TikTok/X
   blocked this run's fetch tools from rendering profile pages directly —
   X returned 402, Instagram 429 — so this is an indirect signal via
   search, not a confirmed follower/post count. Someone with account
   access should log in and confirm directly.)
   → *Action:* Have someone log into the Lumix TikTok and YouTube accounts
   directly and check post count/dates. If they're empty or dormant, either
   commit to a minimal weekly cadence or pull the dead-looking links from
   the footer — a linked-but-empty account reads worse to a prospect than
   no link at all.

2. **The competitor content that actually works is community-sourced, not
   brand-produced.** RocketNode's own marketing blog states its FiveM
   promotion strategy explicitly: "encourage your community to share
   gameplay clips" on TikTok/YouTube Shorts, plus Discord-hosted Q&As and
   contests to keep servers active between posts. BisectHosting's real
   TikTok output is plain tutorial/UGC-style clips, not polished ads. Lumix
   has an active, Discord-centered community (per this routine's own
   framing) that isn't being tapped for any of this.
   → *Action:* Post a standing call in Discord inviting FiveM/Minecraft
   server owners hosted on Lumix to share clips or screenshots of their
   servers, with the best ones reposted to Lumix's own (currently idle)
   TikTok/YouTube. Zero production cost — it reuses content the community
   is already generating.

3. **Lumix's Discord support answers are an untapped tutorial-content
   source.** Shockbyte's split-off Tutorial channel exists because
   "how do I configure X" content is exactly what search and TikTok
   surface competitors for (see finding 1's exact tutorial titles). Lumix's
   support channel almost certainly fields the same recurring questions —
   FiveM artifact updates, Minecraft server IP setup, bot deployment — but
   none of those answers exist anywhere as short-form video.
   → *Action:* Pick the single most-repeated support question from the
   last month of Discord history and record a 30-60 second screen capture
   answering it, posted to TikTok/YouTube Shorts. Repeatable format once
   proven — turns support labor Lumix is already paying for into content.

### Do this today (<1 hour)
Post one pinned message in Discord (#general or #support) asking members
to share their best Lumix-hosted server clip or screenshot for a chance to
be featured on Lumix's TikTok/YouTube. No production work required, and it
immediately gives the two dormant-looking accounts flagged in finding 1
something real to post.

---

## 2026-07-25 (Saturday) — Off-Rotation Check-In

**Note:** The day-of-week rotation defined for this routine only covers
Monday–Friday; the underlying schedule fires daily (confirmed: cron
`30 14 * * *`, no weekday restriction), so this run landed on an
unassigned day. Rather than force a full deep-dive under a track that
doesn't apply to Saturday, this was a lightweight check for anything
new or changed since Friday — one did turn up, below.

### Findings (max 3)

1. **Pricing is now live on the Lumix homepage — Tuesday's finding #2
   ("no price visible anywhere on the public site") appears resolved.**
   Current homepage pricing: FiveM $8.99/mo, Minecraft $14.99/mo,
   Palworld $9.99/mo, BeamMP $5.99/mo, Terraria $5.00/mo. This is the
   first run able to compare Lumix's actual numbers against Monday's
   competitor snapshot rather than recommending pricing be added in the
   abstract.
   → *Action:* No further action on visibility itself. Next Tuesday's
   copy review should confirm the price block persists and check
   whether it also appears on `/services` (or wherever that page has
   moved to, per Thursday's note that `/services` now 404s).

2. **Minecraft's $14.99/mo entry price looks high against Monday's
   competitor benchmarks, but can't be confirmed without the spec
   behind it.** Shockbyte and Apex both anchor Minecraft around
   $2.50–3.75/GB (e.g. Apex 2GB = $7.49). If Lumix's $14.99 entry tier
   is 1–2GB, that's roughly 2–4x the competitor $/GB rate; if it's a
   larger allocation (4GB+), it may be in line or cheaper. The headline
   price alone doesn't say which.
   → *Action:* Pull the RAM/slot spec for the $14.99 Minecraft tier
   from the billing portal and compute effective $/GB against Monday's
   competitor table.

3. **Monday's finding #1 (no visible evergreen discount code) is still
   unresolved as of today** — the current homepage pricing block shows
   no promo code or sale banner, same as the baseline. This is 5 days
   old; not yet at the 7-day escalation threshold, but it will cross
   that line at the next Monday run (2026-07-27) if still unfixed then.
   → *Action:* No new action beyond the existing Monday item — flagging
   as "approaching escalation" so next Monday's run knows to escalate
   rather than re-log it fresh if it's still missing.

### Do this today (<1 hour)
Open the billing portal and note the RAM/slot allocation for the
$14.99/mo Minecraft tier and the $8.99/mo FiveM tier. Two numbers,
directly resolves finding #2 above and turns Monday's competitor
$/GB table from a one-sided comparison into a real one.

---

## 2026-07-26 (Sunday) — Off-Rotation Check-In

**Note:** Second unassigned-weekday run (rotation only covers Mon–Fri,
cron fires daily). Checked homepage, `/games`, and `billing.lumixsolutions.org`
for anything new or changed since Saturday, and tried to close out
Saturday's open action item.

### Findings (max 3)

1. **A meta description now exists sitewide, but it's the same vague
   engineering tagline Thursday's finding #2 warned would show up as the
   default snippet — the fix didn't add keywords, it just formalized the
   problem.** Homepage `<meta name="description">` (confirmed via raw HTML
   pull) reads: "Infrastructure built by engineers. Node.js servers, game
   services, voice infrastructure, and enterprise DDoS protection." No
   game names, no "hosting," no price/speed hook — same gap Thursday
   flagged, just now locked into the actual meta tag instead of being
   Google's fallback guess.
   → *Action:* Replace the meta description with the version already
   drafted in Thursday's log: "FiveM, Minecraft, Terraria, and Discord bot
   hosting with DDoS protection and sub-10ms latency. Deploy in under 60
   seconds." One tag, copy-paste from last Thursday's entry.

2. **Homepage `<title>` is still "Lumix | Lumix Solutions LLC"** —
   unchanged since Thursday's finding #1 (now 3 days old). The site
   restructure noted Thursday (`/services` → `/games`) is confirmed
   complete: nav is now Games / Partners / Staff / Status / Contact /
   Careers, with pricing folded into `/games` rather than a separate
   page. That consolidation makes Thursday's finding #3 (no dedicated
   per-keyword landing page) more locked-in, not less — there's now one
   page (`/games`) trying to rank for FiveM, Minecraft, Terraria, Palworld,
   and BeamMP simultaneously.
   → *Action:* Same one-line fix as Thursday, still outstanding — rewrite
   the `<title>` tag. Not yet at 7-day escalation (hits that Thursday
   7/30), but two site edits have shipped since this was flagged (pricing,
   meta description) and the title tag wasn't touched — worth a direct
   nudge rather than just re-logging.

3. **Saturday's "do this today" (pull RAM/slot spec for the $14.99
   Minecraft and $8.99 FiveM tiers) could not be completed from outside —
   confirmed structurally, not just missed.** Fetched `/games` and
   `billing.lumixsolutions.org` directly: neither page lists RAM, CPU, or
   slot counts anywhere for any tier — only tier names ("Starter,"
   "Elite," "Titan"), price, and generic feature bullets (DDoS protection,
   instant deployment, backups, mod support, 24/7 support). This isn't a
   fetch-tool gap like Monday's 403 — the spec data simply isn't rendered
   on any public-facing page, which means Monday's competitor $/GB
   comparison can't be completed without someone with portal/account
   access pulling the number directly.
   → *Action:* Escalate Saturday's item from "pull two numbers" to "the
   numbers aren't public" — whoever has portal access should check
   whether tier specs are shown post-login, and if not, that's a UX gap
   worth its own finding (a prospect can't self-serve "how much RAM do I
   get" pre-purchase either).

**Escalation status:** Monday's finding #1 (no evergreen discount code) is
now 6 days old, still unresolved as of this run (`/games` and billing
portal both re-checked, no code/banner). Per the 7-day rule this crosses
the threshold at tomorrow's Monday run (2026-07-27) — flagging here so
tomorrow's entry escalates rather than re-logs it as new.

### Do this today (<1 hour)
Swap the homepage meta description for Thursday's already-drafted,
keyword-rich version. It's a copy-paste of existing text into a tag that
now exists but currently holds the wrong content — lowest-effort fix on
the board this run.

---

## 2026-07-27 (Monday) — Competitor Pricing & Plans (Week 2)

**Note:** One week to the day since the 2026-07-20 baseline. Re-fetched
Lumix's homepage and `/games` directly, plus fresh searches on all five
baseline competitors (BisectHosting, Shockbyte, Apex Hosting, ZAP-Hosting,
RocketNode). Nothing material changed on the competitor side this week —
all five still run active discount codes and the same pricing structure
observed 2026-07-20. The story this run is that all three baseline
findings are now exactly 7 days old and confirmed still unresolved on
Lumix's side, crossing this routine's escalation threshold simultaneously.

### Findings (max 3) — all escalated (7+ days unresolved)

1. **ESCALATION — still no evergreen discount code, 7 days unresolved.**
   Fresh fetch of the Lumix homepage and `/games` today shows no code,
   voucher, or sale banner anywhere (same as the 2026-07-25 and 2026-07-26
   check-ins). Meanwhile all 5 competitors checked confirmed still active:
   BisectHosting has 8+ live codes (up to 50% off), Shockbyte's `SHOCK10`/
   `TWITTER25` are still live, Apex's `APEX25` is still live, ZAP's ~20%
   voucher is still live, and RocketNode's "Summer Sale" (up to 25% off,
   through Sep 25) is still running. This is now a full week with zero
   movement on the single most consistent conversion pattern across the
   category.
   → *Action:* This needs to stop being a routine finding and become a
   direct ask to whoever owns pricing/marketing: pick one evergreen code
   (e.g. `LUMIX10`) and ship it to `/games` + pin it in Discord this week.
   If there's a reason it hasn't happened (payment processor limitation,
   against current pricing strategy, etc.), that reason itself is worth
   surfacing so this stops re-appearing as an open item.

2. **ESCALATION — FiveM entry-price gap vs. RocketNode, 7 days
   unresolved, and the audit needed to close it is structurally blocked.**
   RocketNode's FiveM entry is still $6.50/mo against Lumix's $8.99/mo.
   Baseline asked for Lumix's effective $/GB to be computed and compared —
   but today's fetch of `/games` confirms (again, same as Sunday's finding
   #3) that no RAM/slot spec is shown publicly for any Lumix tier. Whoever
   owns this can't complete the audit from outside; it needs portal access.
   → *Action:* Someone with billing-portal access should pull the RAM/slot
   allocation behind the $8.99 FiveM tier and compute $/GB against
   RocketNode's and BisectHosting's published rates. Until that number
   exists, Lumix can't tell whether $8.99 is a real gap or a fair price for
   more resources — it's currently just a headline-number comparison.

3. **ESCALATION — DDoS protection still not quantified, 7 days
   unresolved.** Lumix's homepage and `/games` both still describe only
   "enterprise DDoS protection" / "DDoS protection included," no capacity
   number. RocketNode's "17 Tbps" headline was re-confirmed active again
   this week, and ZAP continues to lead with its own hard number as a
   Cfx.re-partner trust signal. This is the one baseline finding that's
   pure copy — no audit or portal access needed to fix.
   → *Action:* Get the actual mitigation capacity (Tbps or Gbps) from
   Lumix's network/infra provider and add one line to `/games`: e.g.
   "DDoS protection up to X Tbps." Lowest-effort of the three escalations.

**Why all three at once:** the baseline and this run are both Mondays,
exactly 7 days apart, so all three findings from 2026-07-20 crossed the
escalation threshold on the same day. This isn't new discovery — it's the
routine's own 7-day rule firing for the first time since this track
started.

### Do this today (<1 hour)
Of the three, #3 is the only one with zero dependencies (no portal access,
no pricing-strategy decision) — get the DDoS mitigation capacity number
from infra and add "DDoS protection up to X Tbps" to `/games`. Ships today
with no one else needed to unblock it.

---

## 2026-07-28 (Tuesday) — Website Copy (Week 2)

**Note:** One week since the 2026-07-21 baseline. Re-fetched homepage,
`/games`, `/contact`, and `/partners` (site nav is now Home / Game Hosting /
Partners / Staff / Careers / Status / Contact / Panel / Billing Portal —
`/services` is fully gone, consistent with the restructure Thursday and
Sunday both flagged).

**Resolved since baseline:** All three 07-21 findings now appear fixed.
(1) Minecraft and Terraria are both named and priced on `/games`, alongside
Palworld and BeamMP. (2) Pricing is live sitewide (confirmed again — FiveM
$8.99, Minecraft $14.99, Palworld $9.99, BeamMP $5.99, Terraria $5.00).
(3) The "bot hosting" vs. "Application Hosting" naming clash is moot — see
finding 1 below, the section itself is gone, not just renamed. **Also
closing out Monday's 7-day-escalated finding #3**: DDoS protection is now
quantified — a stats block on the homepage and `/games` reads "99.99% SLA
Uptime," "10+ Tbps Mitigated," "<10 ms Latency," "12 PoPs Locations." That
escalation can drop off the list.

### Findings (max 3)

1. **Bot/Application hosting — one of Lumix's four core product lines — has
   no product listing, description, or price anywhere on `/games`.** The
   only mention left sitewide is a banner line, "Expanded bot hosting
   capacity — more space, better isolation, smoother deployments," which
   reads as a changelog update, not an offering. There's no way to
   configure or buy Node.js/Python bot hosting from the marketing site at
   all — this is worse than the naming inconsistency flagged 07-21, where
   the product at least had its own section under a confusing label.
   → *Action:* Add a Bot Hosting card to `/games` alongside FiveM/Minecraft/
   Palworld/BeamMP/Terraria, with a starting price and a "Configure" CTA,
   matching the format already used for the other five products.

2. **The FiveM scarcity claim has no number behind it.** Both `/games` and
   `/partners` repeat, verbatim: "Limited FiveM servers stock available —
   intentionally capped to maintain performance and reliability." No cap
   size, no remaining count, no timeframe — it's the exact "claim with no
   proof" pattern this review track exists to catch, just applied to
   urgency/scarcity instead of a quality adjective like "premium." As
   written, a prospect can't tell if 2 slots are left or 200.
   → *Action:* Either publish the actual cap number ("capped at N servers
   per region this month") or drop the scarcity framing — an unquantified
   "limited stock" claim reads as filler, not urgency.

3. **CTA labels are inconsistent across pages for what appear to be the
   same two actions.** Across homepage, `/games`, and `/contact`, six
   distinct CTA strings do the work of what's really "go configure a
   plan" and "talk to a human": "Build Your Server," "Browse Games,"
   "Configure," "View Full Catalog," "Contact Sales," and "Talk to an
   engineer" (the last two both route to the same sales contact, per
   `/contact`). No single primary CTA is used twice in the same wording,
   which makes it harder for a returning visitor to recognize the button
   they want.
   → *Action:* Standardize on one CTA per action — e.g. "Configure" for
   plan setup (drop "Build Your Server" / "Browse Games" / "View Full
   Catalog" as page-specific synonyms) and "Talk to an engineer" for
   sales contact (drop "Contact Sales"). Pure copy/label change, no new
   pages.

### Do this today (<1 hour)
Pick one CTA wording for the sales-contact action and use it everywhere
that action appears — collapse "Contact Sales" into "Talk to an engineer"
(the more distinctive of the two) on the homepage and any other page still
using the generic version. Lowest-effort fix on today's board; the other
two findings need either a new price/spec or a business decision.

**Escalation status:** Monday's finding #1 (no evergreen discount code for
Lumix's own hosting plans) is now 8 days unresolved — still no code or
banner on `/games` or the homepage. Note: the Partners page does show a
promo code (`LSXEM`, 15% off), but it's a third-party partner's discount
(Elite Modification livery/EUP services), not a Lumix hosting code — it
doesn't resolve this finding, and could actually confuse a prospect
scanning the site for a Lumix-specific code. Monday's finding #2 (FiveM
$/GB audit vs. RocketNode) remains blocked on portal access to tier specs,
unchanged since last week.

---

## 2026-07-29 (Wednesday) — Competitor UX Deep-Dive: RocketNode

**Note:** Second UX-track entry — rotating off BisectHosting (07-22) per
that entry's own note. Picked RocketNode over Shockbyte (whose order page
403'd fetch tools on 07-22). Compared RocketNode's FiveM signup→deploy flow
against Lumix's own `/games/fivem` flow — and in the process found Lumix's
flow has changed substantially since the 07-22 baseline, which is itself
this run's biggest finding.

**Flows observed:**
- **RocketNode:** FiveM page → "Deploy FiveM Server" → a 5-step wizard:
  (1) plan tier with RAM/price shown (Starter 2GB=$6.50 up to God
  32GB=$98.50), (2) location (7 regions: Ashburn, Dallas, Salt Lake City,
  London, Singapore, Sydney + one more, each with a named DDoS provider),
  (3) backup slots and transfer assistance, (4) billing cycle
  (monthly→annual, up to 20% off), (5) add-ons (dedicated IP, paid
  individualized support hour). A "Try your 1 Day Free Trial" CTA sits
  right beside the main deploy button. Est. 8-12 total interactions to a
  completed order.
- **Lumix (`/games/fivem`):** now a 3-step wizard (01 Plan → 02 Location →
  03 Billing Cycle) with full CPU/RAM/NVMe/database specs per tier
  (Starter $8.99 = 2 vCores/2GB/35GB NVMe up to Ultimate $52.99 =
  6 vCores/16GB/175GB NVMe), all "Unmetered player slots." "Deploy Server"
  routes to `billing.lumixsolutions.org` with the configuration pre-filled
  into a cart. No free trial offer anywhere in the flow.

**This resolves two previously open items — noting for the record, not as
new findings:** (1) 07-22's core UX gap ("Bisect wizard vs. Lumix flat tier
list") no longer applies — Lumix has its own guided wizard now. (2) The
07-26/07-27 blocker on Monday's FiveM $/GB audit ("spec data simply isn't
rendered on any public-facing page") is resolved — RAM/CPU/storage specs
are now public on `/games/fivem`. See finding 2 below for the audit this
unblocks.

### Findings (max 3)

1. **Lumix's location picker offers only one real choice, while the site's
   headline claim is "12 PoPs."** The `/games/fivem` wizard's step 2 lists
   exactly two locations: Miami, FL ("Currently sold out") and Ashburn, VA
   (available). RocketNode's equivalent step lists 7 live, selectable
   regions. Homepage and `/games` both still advertise "12 PoPs Locations"
   as a trust stat (confirmed present again this run), but a prospect who
   clicks through to actually configure a FiveM server hits a sold-out
   option and exactly one live alternative — a direct contradiction between
   the marketing claim and the purchasable flow, surfaced specifically by
   walking the flow rather than reading the homepage stat in isolation.
   → *Action:* Either open ordering on more of the 12 claimed PoPs so the
   wizard reflects the stat, or caveat the stat near the wizard itself
   (e.g. "additional regions rolling out") so it doesn't read as
   overstated to someone mid-purchase.

2. **FiveM entry-tier $/GB audit (Monday's blocked escalation) is now
   computable, and confirms Lumix is priced above RocketNode at the
   equivalent spec.** Lumix Starter: $8.99/mo for 2GB RAM = $4.50/GB.
   RocketNode Starter: $6.50/mo for 2GB RAM = $3.25/GB. Lumix is ~38%
   more expensive per GB of RAM at the matching entry tier. Lumix's NVMe
   allocation (35GB at Starter) is a possible offsetting differentiator —
   RocketNode's plan page doesn't surface a comparable storage number — but
   nothing on `/games/fivem` currently calls that out.
   → *Action:* This closes out Monday's "blocked, needs portal access"
   status with a real number — worth flagging directly to whoever owns
   FiveM pricing. If the gap is intentional, add one line to `/games/fivem`
   leading with the NVMe/CPU allocation advantage instead of letting RAM
   alone invite the price comparison.

3. **RocketNode offers a free trial directly next to its purchase CTA;
   Lumix's flow has no trial or money-back offer anywhere from homepage
   through checkout.** "Try your 1 Day Free Trial" sits beside RocketNode's
   "Deploy FiveM Server" button — a zero-commitment way to de-risk the
   exact moment of purchase hesitation. Nothing equivalent exists on
   Lumix's homepage, `/games`, or `/games/fivem`.
   → *Action:* Add a short trial or a "not satisfied in 24 hours, full
   refund" line next to the "Deploy Server" CTA on `/games/fivem` (and
   ideally the other game pages) — doesn't require a new product, just a
   guarantee/trial policy and one line of copy at the decision point.

### Do this today (<1 hour)
Add one line of copy next to the sold-out Miami option in the
`/games/fivem` location step — e.g. "Miami: sold out — Ashburn recommended
for East Coast players" — so a prospect mid-configuration sees a clear
next step instead of a dead-looking option with a "12 PoPs" claim
contradicting it one step later.

**Escalation status:** Monday's finding #1 (no evergreen discount code) is
now 9 days unresolved — no code or banner on `/games`, `/games/fivem`, or
the homepage as of this run. Monday's finding #2 (FiveM $/GB audit) is
resolved above, not escalated further.

---

## 2026-07-30 (Thursday) — SEO & Keywords (Week 2)

**Note:** One week since the 2026-07-23 baseline. Re-fetched raw HTML
(title/meta tags) for the homepage, `/games/`, and all five per-game pages
(`/games/fivem/`, `/games/minecraft/`, `/games/palworld/`,
`/games/beammp/`, `/games/terraria/`), plus `robots.txt` and
`sitemap-0.xml`. **Baseline finding #3 (no dedicated per-keyword landing
page) is now fully resolved** — this is the headline change since last
Thursday: all five games have their own URL, each with a unique,
keyword-rich `<title>` (e.g. "Minecraft Server Hosting | Lumix Solutions
LLC," "FiveM Server Hosting | Lumix Solutions LLC") and a genuinely
specific meta description (not boilerplate — e.g. FiveM's reads "Unmetered
slots, dedicated vCores, and NVMe storage on RAID 1..."). All five are
correctly listed in `sitemap-0.xml` and `robots.txt` allows full indexing.
This closes the structural gap Thursday's baseline said blocked ranking
"regardless of title/meta fixes."

### Findings (max 3)

1. **ESCALATION — homepage `<title>` and meta description are still
   exactly what they were on 07-23, now 7 days unresolved.** Raw HTML
   confirms both today: title is still "Lumix | Lumix Solutions LLC," meta
   description is still "Infrastructure built by engineers. Node.js
   servers, game services, voice infrastructure, and enterprise DDoS
   protection." Neither contains a hosting or game keyword. This is no
   longer a capability question — the team clearly can write strong,
   specific title/meta copy, since all five new per-game pages prove it
   this same week — it's specifically the homepage tag that keeps getting
   skipped despite being logged as a one-line fix four runs running
   (07-23, 07-26, 07-28, 07-29).
   → *Action:* Copy the pattern already proven on the game pages directly
   onto the homepage: title → "Lumix Solutions | FiveM, Minecraft,
   Terraria & Bot Hosting"; meta → "FiveM, Minecraft, Terraria, and
   Discord bot hosting with DDoS protection and sub-10ms latency. Deploy
   in under 60 seconds." Two tags, no redesign, same task as last week.

2. **NEW — Bot/Application hosting is now the only one of Lumix's four
   core product lines with zero SEO footprint**, now that the five games
   all have dedicated pages. No `/games/bot`, `/games/apps`, or equivalent
   URL exists (checked and confirmed 404 across likely paths); it's absent
   from `sitemap-0.xml`; and it never appears in any page `<title>` or meta
   description sitewide. Meanwhile this run's search for "discord bot
   hosting node.js python" surfaces real, ranking competitors — YorkHost,
   EmpowerServers, XeroHost, Wispbyte — each with a page built specifically
   around that phrase. This is the SEO-specific edge of the product-listing
   gap Tuesday's copy review (07-28) already flagged; it means Lumix is
   invisible to search for one full quarter of its own product line while
   the other three now rank on dedicated pages.
   → *Action:* Once a Bot Hosting product page exists (per Tuesday's
   07-28 action item), give it the same treatment as the five game pages:
   a keyword title ("Node.js & Python Bot Hosting | Lumix Solutions"), a
   specific meta description, and an entry in the sitemap. This can ship
   as one PR alongside Tuesday's page-creation work rather than as a
   separate task.

3. **NEW — the five new per-game pages carry price and spec data but no
   Product/Offer structured data (schema.org), so none are eligible for
   price-in-snippet rich results.** Checked the JSON-LD on all five pages
   (`/games/fivem/`, `/minecraft/`, `/palworld/`, `/beammp/`,
   `/terraria/`): each ships only the same sitewide `Organization` and
   `WebSite` blocks — no `Product`, `Offer`, or `priceRange` markup, despite
   each page displaying a clear starting price ($8.99, $14.99, $9.99,
   $5.99, $5.00). Price-conscious searches like "cheap minecraft server
   hosting" (checked this run) return results where budget-focused
   competitors can qualify for a price-annotated snippet; Lumix's pages
   currently can't, even though the underlying price data already exists
   on-page.
   → *Action:* Add a `Product` + `Offer` JSON-LD block to each of the five
   game page templates, pulling the price that's already rendered on the
   page. One shared template change (not five one-offs), since all five
   pages share the same layout.

### Do this today (<1 hour)
Fix the homepage `<title>` and meta description now — this is the same
single-page, two-tag edit that's been sitting in this log since 07-23 and
crosses the 7-day escalation line today. Use the copy already drafted in
finding #1 above; no new writing required, just applying it.

**Escalation status:** Baseline finding #1 (homepage title) is now 7 days
unresolved as of today — escalated in finding #1 above. Baseline finding
#2 (homepage meta description, same underlying page) is folded into the
same escalation since both tags live on the same unedited page. Monday's
evergreen-discount-code finding is separately tracked on the pricing track
and remains open per Wednesday's (07-29) entry; not re-logged here since
this is the SEO track.

---

## 2026-07-31 (Friday) — Social & Community (Week 2)

**Note:** One week since the 2026-07-24 baseline. Re-checked the homepage
footer (all five social links unchanged: TikTok `@lumix.solutions`, YouTube
`@officiallumixsolutions`, X `@LumixSolutions`, Instagram
`@lumixsolutionsllc`, Discord invite), re-searched Lumix's TikTok/YouTube
handles, and for the first time pulled Lumix's actual Discord member count
via the invite API rather than relying on search alone. Also checked three
competitors' current social output (BisectHosting, Shockbyte, Apex Hosting,
RocketNode) for anything new since last Friday.

### Findings (max 3)

1. **ESCALATION — Lumix's YouTube channel is no longer just "no
   discoverable content," it now 404s outright, 7 days unresolved.** Last
   Friday's finding was an indirect signal (targeted searches for
   `@officiallumixsolutions` surfaced nothing, with a caveat that fetch
   tools were partially blocked). This run fetched
   `youtube.com/@officiallumixsolutions` directly — hard HTTP 404, not a
   loading/blocking issue — and confirmed via a fresh search that no
   channel by that name is indexed anywhere. TikTok's `@lumix.solutions`
   still isn't blocked but also still returns zero indexed content, same
   as baseline. The footer links to this YouTube handle from the live
   site, meaning a prospect who clicks it today hits a dead page.
   → *Action:* Someone with account access needs to confirm today whether
   the YouTube channel was deleted, renamed, or never existed under that
   handle. If it's gone, pull the dead link from the footer immediately —
   a 404 from a company's own footer is worse than the "empty account"
   problem flagged last week. If it was renamed, update the footer link to
   the correct handle.

2. **NEW — Lumix's own Discord, measured directly for the first time
   (128 members, 24 online via the invite API), is a real but small
   community next to what competitors report investing in theirs.**
   RocketNode's own announcements describe their Discord (10,595 members)
   as central to "hearing direct feedback on their products" — the exact
   community-sourced content flywheel last Friday's finding #2 recommended
   Lumix tap into. Lumix's ~19% online/member ratio suggests genuine
   engagement, not a dead server — the gap is size and content output, not
   activity, which supports going after last week's "repost community
   clips" idea rather than a bigger structural fix.
   → *Action:* No new action beyond last week's still-open item (pin a
   Discord call for community clips/screenshots to repost on TikTok/
   YouTube) — this number is a baseline to track against once that starts,
   not a new task.

3. **NEW — Apex Hosting runs a recurring, low-cost content-and-acquisition
   engine timed to this exact calendar window that Lumix has no
   equivalent of.** Apex's "6th Annual Minecraft Scholarship" ($2,000,
   essay-based, open now) lands right before back-to-school season and
   pairs with a `STUDENT` discount code — it generates entrant
   essays/shares every August at minimal production cost and gives Apex a
   recurring seasonal story instead of one-off promos. Lumix has no
   seasonal or recurring community event of any kind on the books.
   → *Action:* Not a $2,000-scholarship-sized ask, but worth a scaled-down
   version this August: a Discord-only "best back-to-school server setup"
   contest (e.g. a free month of hosting as the prize) — cheap, timely,
   and reuses the same community-content mechanism as finding 2's open
   item instead of requiring a new initiative.

### Do this today (<1 hour)
Log into the YouTube account and confirm whether
`@officiallumixsolutions` still exists. If it's gone, delete that footer
link now — it's an active broken link on the live site, not a
future-facing recommendation like the other items today.

**Escalation status:** Friday baseline finding #1 (dormant TikTok/YouTube)
is now 7 days unresolved and escalated above with a stronger signal (hard
404 on YouTube, not just an unindexed search). Last Friday's "do this
today" (pin a Discord community-clips call) could not be verified from
outside Discord this run — carrying forward as still-open rather than
re-logging as new.

---

## 2026-08-01 (Saturday) — Off-Rotation Check-In

**Note:** Third unassigned-weekday run (rotation covers Mon–Fri only, cron
fires daily). Re-fetched the homepage and `/games/` directly (raw HTML,
not cached) to check anything new or changed since Friday's report, and to
re-verify the log's oldest open items.

### Findings (max 3)

1. **ESCALATION — homepage `<title>` and meta description are still
   completely unchanged, and this is now the most overdue item in the
   entire log.** Raw HTML confirmed again today: title is still "Lumix |
   Lumix Solutions LLC," meta description is still "Infrastructure built
   by engineers. Node.js servers, game services, voice infrastructure, and
   enterprise DDoS protection." First flagged 2026-07-23, formally
   escalated at the 7-day mark on 2026-07-30 — it is now 9 days past that
   escalation (13 days total) with zero change, despite exact ready-to-
   paste replacement copy having been provided twice in this log
   (07-23 and again 07-30). Every other page on the site (`/games/` and
   all five per-game pages) has a proper keyword title — this is now
   specifically and only the homepage tag that keeps getting skipped.
   → *Action:* This should stop being treated as a routine finding. Flag
   directly to whoever has CMS/deploy access that a two-line copy-paste
   fix has been sitting untouched for 13 days: title →
   "Lumix Solutions | FiveM, Minecraft, Terraria & Bot Hosting"; meta →
   "FiveM, Minecraft, Terraria, and Discord bot hosting with DDoS
   protection and sub-10ms latency. Deploy in under 60 seconds."

2. **NEW — a "Coming Soon" section has appeared on `/games/` listing four
   unreleased titles: ARK: Survival Ascended, Rust, Arma Reforger, and
   Squad.** Not present in any prior run's fetch of this page (last
   checked 07-30 for SEO, 07-31 for the games list). No dates, pricing, or
   dedicated URLs exist yet for any of the four — this is a teaser only.
   Thursday's SEO track (07-23, 07-30) established that Lumix's dedicated
   per-game pages are what actually let it rank, and that each existing
   page only started drawing search traffic once it shipped with its own
   keyword-matched URL and title.
   → *Action:* Worth reserving the SEO lead time now rather than at
   launch — stub out `/games/ark-survival-ascended`, `/games/rust`,
   `/games/arma-reforger`, and `/games/squad` (even a simple "notify me"
   page per title) so each has time to get indexed before the product
   itself ships, instead of starting from zero SEO on launch day the way
   the original five titles did.

3. **Evergreen discount code is still missing, now 12 days unresolved.**
   Re-checked both the homepage and `/games/` directly today — no code,
   voucher, or sale banner on either, same as every check since the
   2026-07-20 baseline (escalated 07-27 at 7 days). No change to report
   beyond the day count; carrying forward, not re-analyzing, since
   Monday's pricing-track re-check is the right place for a fresh look at
   this.

### Do this today (<1 hour)
Ship finding #1's homepage title and meta description fix. It is the
single most overdue item in this entire log — 13 days old, flagged twice
with copy already written and ready to paste, zero dependencies, and the
one item that's been "one line away" the longest.

**Escalation status:** Homepage title/meta (finding #1) crosses from
"escalated" to "long-overdue" today — 9 days past its own escalation
point. Evergreen discount code (finding #3) is now 12 days unresolved,
approaching two weeks. YouTube's hard 404 (escalated 07-31) re-confirmed
still broken today via direct fetch — not re-listed as a full finding
since status is unchanged from Friday, but still live and unresolved.

---

## 2026-08-02 (Sunday) — Off-Rotation Check-In

**Note:** Fourth unassigned-weekday run (rotation covers Mon–Fri only,
cron fires daily). Re-fetched the homepage raw HTML, `/games/`, and
`youtube.com/@officiallumixsolutions` directly to check for movement on
the log's longest-running open items since yesterday's report.

### Findings (max 3)

1. **The homepage `<title>` tag finally changed for the first time since
   this finding opened on 2026-07-23 (13 days, 5 prior mentions) — but the
   fix is partial and introduces a new inconsistency.** Raw HTML confirms
   today's title is now `Game Server & VPS Hosting | Lumix Solutions`,
   replacing the old generic "Lumix | Lumix Solutions LLC." That's
   genuine progress: it now contains "Hosting" and reads like a real
   company description. But it doesn't match the copy this log has
   recommended five times ("FiveM, Minecraft, Terraria & Bot Hosting") —
   it names no specific game — and the meta description right next to it
   is byte-for-byte unchanged: still "Infrastructure built by engineers.
   Node.js servers, game services, voice infrastructure, and enterprise
   DDoS protection," still zero keywords. Whoever edited the title didn't
   use the drafted copy sitting in this log and left the paired meta tag
   untouched.
   → *Action:* Finish the job with the already-drafted meta description
   ("FiveM, Minecraft, Terraria, and Discord bot hosting with DDoS
   protection and sub-10ms latency. Deploy in under 60 seconds.") — same
   one-line copy-paste that's been ready since 07-23.

2. **NEW — the new title's "VPS Hosting" claim has zero backing anywhere
   else on the site.** Checked homepage body copy, nav (Home / Game
   Hosting / Partners / Staff / Careers / Status / Contact / Billing
   Portal / Panel), banners, and `/games/` (5 live games + 4 Coming Soon
   teasers) — "VPS" appears nowhere except that one title tag. This is
   the same pattern flagged 07-29 with the "12 PoPs" vs. 2-location
   wizard mismatch: a claim added to trust-signal copy that the rest of
   the site doesn't support yet. A prospect who searches "VPS hosting,"
   clicks through on that exact title, and lands on a page with no VPS
   product, price, or mention anywhere bounces immediately.
   → *Action:* Either drop "VPS" from the title until a real VPS product
   page exists, or — if VPS hosting is actually launching — this is worth
   surfacing directly rather than waiting for Thursday's SEO rotation,
   since right now it's a keyword with nothing behind it.

3. **Evergreen discount code gap is now 13 days unresolved, one day short
   of two full weeks.** Re-checked homepage and `/games/` directly today —
   still no code, voucher, or sale banner on either, unchanged since the
   2026-07-20 baseline and the 07-27 escalation. No new analysis needed;
   flagging the day count since Monday's pricing re-check (which lands
   exactly on day 14) is the right place to decide whether this needs to
   escalate beyond a routine log entry.

**Resolved/unchanged since yesterday:** Yesterday's "Coming Soon" section
(ARK: Survival Ascended, Rust, Arma Reforger, Squad) is unchanged — same
four titles, still no dates or pricing, not re-reported as new.
`youtube.com/@officiallumixsolutions` re-confirmed hard 404 again today —
still broken, still unresolved since 07-31, not re-listed as a full
finding since nothing changed.

### Do this today (<1 hour)
Paste the already-drafted meta description onto the homepage — it's the
second half of finding #1 and the only piece of that 13-day-old fix still
outstanding. Copy is ready, zero new writing: "FiveM, Minecraft, Terraria,
and Discord bot hosting with DDoS protection and sub-10ms latency. Deploy
in under 60 seconds."

**Escalation status:** Homepage title (finding #1, original half) is
resolved as of today after 13 days — first movement since 07-23. Meta
description (the other half of the same original finding) remains
unresolved, now also 13 days old, carried forward under finding #1 rather
than re-opened as separate. Evergreen discount code is 13 days unresolved,
crossing 14 (two weeks) at tomorrow's Monday pricing re-check. YouTube's
404 remains unresolved, unchanged since 07-31.

---

## 2026-08-03 (Monday) — Competitor Pricing & Plans (Week 3)

**Note:** Re-fetched Lumix's homepage, `/games/`, and `/games/fivem` directly,
plus fresh checks on RocketNode's and BisectHosting's live FiveM/Minecraft
pricing pages and searches on ZAP-Hosting. No structural changes on the
competitor side this week — same five providers, same pricing tiers as the
07-20 baseline and 07-27 re-check. The story this run is the discount-code
gap crossing a two-week milestone, plus a new angle on why the gap compounds
right now.

### Findings (max 3)

1. **ESCALATION — evergreen discount code gap is now 14 days unresolved,
   a full two weeks with zero movement.** Re-confirmed today via direct
   fetch of the homepage and `/games/fivem`: still no code, voucher, or sale
   banner anywhere on Lumix's site. Meanwhile every competitor checked this
   run still runs one: RocketNode's FiveM page shows an active "Summer Sale
   — Up to 25% Off" banner plus a "1 Day Free Trial" CTA; BisectHosting's
   Minecraft page shows the same "Summer Sale — Up to 25% Off" plus
   quarterly/semi-annual/annual billing discounts up to 20%; ZAP-Hosting's
   permanent 20%-off voucher is still live per this week's search. This has
   now been logged as open on five straight Monday-or-later checks
   (07-20, 07-25, 07-26, 07-27, 08-01, 08-02, and today) with the same
   concrete action attached each time.
   → *Action:* This needs an explicit answer, not another log line — ask
   whoever owns pricing directly: is there a blocker (payment processor,
   margin, pricing-strategy call) to shipping one evergreen code (e.g.
   `LUMIX10`)? If yes, log that reason so this stops re-appearing weekly;
   if no, ship it this week — it's the single most consistent, lowest-effort
   conversion lever every competitor in this category already uses.

2. **NEW — Lumix's own multi-month billing discounts cap lower than every
   competitor checked this run, compounding the code gap.** Lumix's
   `/games/fivem` billing-cycle discounts top out at 10% (biennial/
   triennial only; quarterly and annual are both 5%). RocketNode offers
   5% quarterly but 12% semi-annual and 20% annual; BisectHosting offers
   10% quarterly, 15% semi-annual, and 20% annual. A prospect comparing
   Lumix and RocketNode side by side at the 1-year commitment sees a 20%
   discount at RocketNode against 5% at Lumix — a gap that exists purely
   in the commitment-discount structure, separate from and additional to
   the missing evergreen code in finding 1.
   → *Action:* Worth a quick gut-check with whoever owns pricing: is a 20%
   annual discount (matching category norm) actually a margin problem, or
   just something that hasn't been revisited since the tiers were set?
   Even matching the 20% annual figure alone (leaving quarterly/semi-annual
   as-is) would close the most visible part of this gap.

3. **NEW — RocketNode's active sale widens the already-known FiveM
   entry-price gap to over 50% for the length of the promo.** The 07-29
   audit established Lumix's Starter ($8.99/2GB = $4.50/GB) runs ~38% above
   RocketNode's Starter ($6.50/2GB = $3.25/GB) at list price. With
   RocketNode's "Summer Sale — Up to 25% Off" now confirmed live on the
   FiveM page itself (not just sitewide), a prospect who applies that
   discount pays as little as ~$4.88/mo for the same 2GB tier — Lumix would
   need to be priced roughly 84% higher than that sale price for the same
   spec. This is a live, time-bound gap, not just the static comparison
   already on record.
   → *Action:* No pricing change needed to act on this today — see "do this
   today" below for the copy-only mitigation.

### Do this today (<1 hour)
Add one line near the Starter tier on `/games/fivem` calling out Lumix's
NVMe/vCore allocation advantage (35GB NVMe / 2 dedicated vCores at Starter,
vs. RocketNode's page not surfacing a comparable storage number) — e.g.
"More dedicated compute & NVMe storage per dollar." This doesn't require a
pricing decision from anyone else and directly blunts finding 3's
raw-price comparison while RocketNode's sale is active, unlike findings 1
and 2 which need an owner decision.

**Escalation status:** Evergreen discount code (finding 1) crosses two full
weeks unresolved today — flagged as needing a direct decision rather than
continued routine logging. Homepage meta description (open since 07-23,
last touched partially on 08-02) and the YouTube hard 404 (open since
07-31) are unchanged since yesterday's check-in; not re-listed since
nothing moved and neither falls on today's pricing track.

---

## 2026-08-04 (Tuesday) — Website Copy (Week 3)

**Note:** One week since the 2026-07-28 baseline. Re-fetched the homepage,
`/games/`, and `/contact` directly. Nothing on the copy track has changed
since 07-28 — all three baseline findings are confirmed still present,
unchanged, exactly 7 days later. No new pages, sections, or copy rewrites
appeared this week outside what Monday's and Sunday's off-track runs
already logged (title tag change, Coming Soon section — neither touched by
this run).

### Findings (max 3) — all escalated (7 days unresolved)

1. **ESCALATION — Bot/Application hosting still has no product listing,
   description, or price anywhere on `/games/`, 7 days unresolved.**
   Re-fetched `/games/` today: five live product cards (FiveM, Minecraft,
   Palworld, BeamMP, Terraria) plus four "Coming Soon" teasers (ARK, Rust,
   Arma Reforger, Squad) — bot hosting appears in neither list. The only
   sitewide mention remains the homepage banner line, "Expanded bot hosting
   capacity — more space, better isolation, smoother deployments," which
   still reads as a changelog note, not something a prospect can configure
   or buy. One of Lumix's four core product lines remains completely
   absent from the page that lists every other product.
   → *Action:* Add a Bot Hosting card to `/games/` in the same
   name/price/spec/CTA format as the other five products. This has now
   been logged unchanged for a full week — worth a direct check with
   whoever owns the `/games/` catalog on whether it's blocked or just not
   yet scheduled.

2. **ESCALATION — FiveM scarcity claim still has no number behind it, 7
   days unresolved.** Both the homepage and `/games/` still repeat,
   verbatim: "Limited FiveM servers stock available - intentionally capped
   to maintain performance and reliability." No cap size, no remaining
   count, no timeframe — unchanged word-for-word from 07-28. This is still
   the exact "claim with no proof" pattern this track exists to catch.
   → *Action:* Publish the actual cap number or drop the scarcity framing.
   Unchanged from last week's recommendation — still a single-line fix,
   still not shipped.

3. **ESCALATION — CTA naming inconsistency is confirmed unresolved and now
   has a third variant, not just two.** 07-28 flagged six inconsistent
   strings across homepage/`/games/`/`/contact` for two actions ("configure
   a plan" and "talk to a human"). Today's direct fetch of `/contact`
   shows that page doesn't use either "Contact Sales" or "Talk to an
   engineer" (both still present elsewhere, per today's homepage and
   `/games/` fetch) — it presents raw "General Inquiries" / "Technical
   Support" email links instead, plus the billing portal and Discord
   links, with no button labeled for sales contact at all. A prospect
   following "Contact Sales" from the homepage lands on a page that never
   uses that phrase or an equivalent CTA.
   → *Action:* Same fix as 07-28 — standardize on one label for the sales-
   contact action sitewide, and make sure `/contact` itself actually
   surfaces that label near the relevant email/link rather than leaving it
   unlabeled.

**Also observed (not counted against the max-3, folds into item 2's
"claim with no proof" pattern):** the homepage's "What we do" section
reads, verbatim: "Reliable compute, game server hosting, voice
infrastructure, and enterprise-grade DDoS protection. No buzzwords, just
infrastructure that works." — the sentence claiming "no buzzwords" sits
directly after the word "enterprise-grade," one of the vaguest terms in
the whole site. This is new this run (not present in any prior fetch's
extracted headline copy) and is the single easiest fix on today's board —
see "do this today."

### Do this today (<1 hour)
On the homepage "What we do" section, replace "enterprise-grade DDoS
protection" with a concrete figure — the site already has one ("10+ Tbps
mitigated," per the homepage's own stats block a few lines away) — so the
sentence reads something like "...and DDoS protection mitigating 10+
Tbps. No buzzwords, just infrastructure that works." Removes a claim that
directly undercuts the sentence right after it, and reuses a number
that's already published elsewhere on the same page.

**Escalation status:** All three copy-track findings from 07-28 cross the
7-day threshold today and are escalated above. Evergreen discount code
(pricing track, 15 days unresolved as of yesterday) and the YouTube hard
404 (social track, open since 07-31) are unchanged and not falling on
today's track; not re-listed.

---

## 2026-08-05 (Wednesday) — Competitor UX Deep-Dive: Apex Hosting

**Note:** Third UX-track entry, rotating to Apex Hosting (previously only
seen in this log via pricing/promo mentions on 07-20, 07-27, 07-31 —
never its own UX-track subject). Shockbyte was the next-in-line candidate
per 07-22's note, but its main site and order page both returned HTTP 403
to fetch tools again this run (same block hit on 07-22 — two runs in a
row now). Apex's own pages also blocked direct fetch (403/503 across
homepage, pricing, and getting-started), so Apex's flow and specs below
are reconstructed from search-indexed content (Apex's own pricing page
text as indexed, plus independent review sites) rather than a live
render — flagging the method since it's weaker than the direct-fetch
comparisons done for BisectHosting (07-22) and RocketNode (07-29).
Lumix's own `/games/fivem` flow was fetched live and directly for
comparison, exactly one week after the 07-29 baseline.

**Flows observed:**
- **Apex Hosting:** Pricing page lists 9 Minecraft RAM tiers (1GB=$4.49
  up to 15GB=$79.99), each with **unlimited storage on every tier** —
  storage isn't a decision variable at all, unlike Lumix's per-tier NVMe
  allocations. Order flow per Apex's own docs and independent reviews:
  pricing page → "Order Now" → a configure screen (add-ons like Dedicated
  IP or Premium Support) → order review screen → billing/payment details
  → "Complete Order," with account creation folded into that final
  billing step (same deferred-signup pattern BisectHosting used). Apex
  operates **18 real datacenters across 6 continents** (confirmed via
  multiple independent sources: 6 in the US plus Canada, Brazil, UK,
  France, Poland, Germany, Israel, Russia, China, Singapore, Australia,
  Turkey) — a live promo code `APEX25` (25% off first invoice, +10%
  extra for quarterly) is already tracked on the pricing track.
- **Lumix (`/games/fivem`):** Unchanged from the 07-29 baseline — still a
  3-step wizard (Plan → Location → Billing Cycle). Location step still
  lists exactly two datacenters: Miami, FL ("Sold Out — Out of
  capacity") and Ashburn, VA. No free trial or discount code field
  anywhere in the flow (re-confirmed live today). Homepage stats block
  still reads "12 PoPs" locations, unchanged.

### Findings (max 3)

1. **ESCALATION — the "12 PoPs" homepage claim vs. the wizard's actual
   2-location (1 sold out) reality is now 7 days unresolved, and this
   week's comparison competitor sharpens the gap rather than closing it.**
   First flagged 07-29 as an internal contradiction on Lumix's own site;
   re-confirmed live today via direct fetch — same two locations, same
   Miami "Sold Out" state, same unchanged "12 PoPs" stat block. Apex
   Hosting, this run's comparison competitor, genuinely operates 18
   datacenters across 6 continents — meaning the category norm this
   claim is implicitly competing against isn't hypothetical, it's a real,
   live, larger footprint at a competitor Lumix is priced near.
   → *Action:* Same fix proposed 07-29, now overdue: either open ordering
   on more of the 12 claimed PoPs so the wizard matches the stat, or
   change the homepage stat itself to something accurate right now (e.g.
   "2 Locations — more rolling out") until it does. A false-sounding trust
   stat on the homepage is a sharper risk than the wizard-level mismatch
   alone.

2. **ESCALATION — no free trial, guarantee, or discount code exists
   anywhere in Lumix's purchase flow, 7 days unresolved.** First flagged
   07-29 against RocketNode's "1 Day Free Trial" CTA; re-confirmed today
   via direct fetch of both `/games/fivem` and the homepage — no trial,
   refund policy, or code field on either. Apex's flow adds a second data
   point in the same direction: its `APEX25` promo is applied inline
   during the billing step of checkout, meaning two of the three
   competitors reviewed on this UX track now (RocketNode, Apex) surface a
   de-risking or discount mechanism at the exact purchase moment, and
   Lumix's flow still surfaces neither.
   → *Action:* Unchanged from 07-29 — add a short trial or a "not
   satisfied in 24 hours, full refund" line next to the "Deploy Server"
   CTA. This is separate from (but reinforces) the still-open evergreen
   discount code finding tracked on the pricing track.

3. **NEW — Apex removes storage as a decision variable entirely; Lumix
   makes a prospect pick a specific storage number at every tier.** Every
   Apex Minecraft plan, from the $4.49 1GB tier to the $79.99 15GB tier,
   includes unlimited storage — one less axis a prospect has to reason
   about when comparing tiers. Lumix's FiveM wizard instead pairs RAM
   with a specific NVMe figure per tier (35GB at Starter up to 175GB at
   Ultimate per the 07-29 baseline, reconfirmed today), meaning a
   prospect has to evaluate two correlated numbers (RAM and storage)
   instead of one. This isn't necessarily wrong — more storage at higher
   tiers is a legitimate differentiator — but it adds a decision step
   Apex's flow skips entirely.
   → *Action:* Low-effort test: add a line under the plan tiers noting
   the practical implication of the NVMe allocation (e.g. "35GB — enough
   for FiveM base install + typical resource/script pack"), so the
   storage number means something to a prospect instead of being a raw
   figure they have to size themselves.

### Do this today (<1 hour)
Change the homepage stats block's "12 PoPs" figure to reflect what's
actually purchasable today — e.g. "2 Locations (more rolling out)" — or
add a footnote/tooltip. This is a smaller copy edit than shipping new
datacenters, closes the sharpest version of finding 1, and is more urgent
than the original 07-29 suggestion (a line near the wizard) since the
false-sounding claim lives on the homepage, not just inside the
configurator.

**Escalation status:** Both 07-29 UX-track findings (12 PoPs vs. 2-location
wizard; no trial/guarantee in the flow) cross 7 days unresolved today and
are escalated above. Evergreen discount code (pricing track, 15+ days
unresolved) and the YouTube hard 404 (social track, open since 07-31) are
unchanged and not re-listed since neither falls on today's track.

---

## 2026-08-06 (Thursday) — SEO & Keywords (Week 3)

**Note:** One week since the 2026-07-30 entry. Pulled raw HTML directly
(title/meta/JSON-LD) for the homepage, `/games/`, `/games/fivem/`,
`/games/minecraft/`, `/games/terraria/`, plus `sitemap-0.xml`, and checked
likely bot-hosting URLs (`/games/bot/`, `/games/bot-hosting/`,
`/games/application/`, `/games/apps/`, `/games/nodejs/`, `/games/node/` —
all still 404). Also ran fresh generic-keyword searches ("fivem server
hosting," "cheap minecraft server hosting," "discord bot hosting node.js
python") to see whether the new per-game pages have started surfacing for
unbranded queries yet. All three findings below are escalations of
already-logged items, not new discoveries — nothing changed structurally
on the SEO track this week beyond the day-count.

### Findings (max 3) — all escalated (7+ days unresolved)

1. **ESCALATION — homepage meta description is now 14 days unresolved,
   the oldest continuously-open item in this entire log.** Raw HTML
   confirms today it is still byte-for-byte the same text flagged on
   07-23: "Infrastructure built by engineers. Node.js servers, game
   services, voice infrastructure, and enterprise DDoS protection." No
   game name, no "hosting," no price/speed hook. The homepage `<title>`
   was partially fixed on 08-02 (now "Game Server & VPS Hosting | Lumix
   Solutions") but whoever made that edit didn't touch the paired meta tag
   sitting right next to it, even though the exact replacement copy has
   been sitting ready-to-paste in this log since 07-23 and been
   re-mentioned five times since (07-26, 07-28, 07-29, 07-30, 08-02).
   → *Action:* Paste the already-drafted description: "FiveM, Minecraft,
   Terraria, and Discord bot hosting with DDoS protection and sub-10ms
   latency. Deploy in under 60 seconds." Zero new writing, one tag, two
   weeks overdue.

2. **ESCALATION — Bot/Application hosting still has zero SEO footprint, 7
   days unresolved.** Re-confirmed today: no `/games/bot/`,
   `/games/bot-hosting/`, `/games/application/`, `/games/apps/`,
   `/games/nodejs/`, or `/games/node/` exists (all checked, all 404);
   `sitemap-0.xml` lists 12 URLs total and still contains no bot-hosting
   entry; the string "bot hosting" appears sitewide only inside the same
   changelog-style banner line flagged 07-28 and 07-30. Generic search for
   "discord bot hosting node.js python" this run surfaces real competitors
   (HYEHOST, LordHosting, OuiHeberg, Kuberns) with dedicated pages —
   lumixsolutions.org does not appear anywhere in those results. This is
   the same product-listing gap Tuesday's copy track has open (still
   unresolved as of 08-04); the SEO consequence compounds every week it
   stays unshipped.
   → *Action:* Unchanged from 07-30 — once a Bot Hosting product page
   exists, give it the same title/meta/sitemap treatment as the five game
   pages. Worth flagging as blocked-on-the-same-thing to whoever owns both
   the Tuesday and Thursday tracks' open items, since it's one build, not
   two separate asks.

3. **ESCALATION — game pages still carry no Product/Offer structured
   data, 7 days unresolved.** Checked JSON-LD on `/games/fivem/`,
   `/games/minecraft/`, and `/games/terraria/` directly today: each ships
   only `Organization` and `WebSite` blocks, identical to 07-30 — no
   `Product`, `Offer`, or `priceRange` markup despite every page rendering
   a clear price ($8.99, $14.99, $5.00). No progress since last week's
   finding.
   → *Action:* Unchanged from 07-30 — add a shared `Product`+`Offer`
   JSON-LD block to the game-page template, pulling the price already
   rendered on-page. One template change covers all five (soon six-plus)
   game pages.

**Also observed (not a new finding, context only):** unbranded searches
this run ("fivem server hosting," "cheap minecraft server hosting") still
do not surface any `lumixsolutions.org` result — only branded queries
("lumix solutions fivem hosting") return the site. Expected this early
(the per-game pages are ~1 week old), not yet actionable, but worth
checking again in another week or two to see whether the title/meta work
already shipped is translating into unbranded ranking.

### Do this today (<1 hour)
Paste the already-drafted homepage meta description (finding #1) — this is
the same one-line copy-paste that has been sitting in this log since
07-23, now 14 days old and the single most overdue item on record. Copy:
"FiveM, Minecraft, Terraria, and Discord bot hosting with DDoS protection
and sub-10ms latency. Deploy in under 60 seconds."

**Escalation status:** Bot-hosting SEO gap and missing Product/Offer
schema (both first logged 07-30) cross 7 days unresolved today and are
escalated above for the first time. Homepage meta description crosses 14
days today (7 days past its own 07-30 escalation). Evergreen discount code
(pricing track) and YouTube 404 (social track) are unchanged and not
re-listed since neither falls on today's track.

---
