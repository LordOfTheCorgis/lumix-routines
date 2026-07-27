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
