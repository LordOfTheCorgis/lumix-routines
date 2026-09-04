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

## 2026-08-07 (Friday) — Social & Community (Week 3)

**Note:** Two weeks since the 07-24 baseline, one week since the 07-31
hard-404 escalation. Re-fetched the homepage footer (all five social links
unchanged), re-checked `youtube.com/@officiallumixsolutions` directly,
re-pulled Lumix's Discord member count via the invite API (same invite,
`uaNYBJQtvn`), re-searched for any indexed TikTok content, and checked
whether either competitor content item flagged last week (RocketNode's
community-clip strategy, Apex's back-to-school scholarship) has moved.

### Findings (max 3)

1. **ESCALATION — YouTube footer link is still a hard 404, now 7 days
   unresolved as a confirmed dead link (21 days since first flagged as
   dormant on 07-24).** Direct fetch of
   `youtube.com/@officiallumixsolutions` today returns the same HTTP 404
   confirmed last Friday — no rename, no restoration. This is now the
   second consecutive weekly check with zero movement on last week's "do
   this today" (log in and confirm/fix), and it remains a broken link
   live in the site's own footer.
   → *Action:* Since this has gone two full weeks with no visible change,
   treat it as not going to get fixed by another reminder alone — either
   someone confirms today whether the account is recoverable, or the
   footer link should just be removed this week pending a real relaunch.
   A dead link in month two looks worse than no YouTube icon at all.

2. **NEW — Discord membership is flat week-over-week (128→130 members,
   presence 24→19) despite two straight Fridays recommending a
   community-clips call-to-action.** If that pinned ask went up, it isn't
   showing in growth or in the online count, which actually dipped. This
   is the first real signal (not just "still open") that either the
   action wasn't taken or isn't moving the number by itself.
   → *Action:* Confirm directly whether the Discord community-clips post
   from either prior week's "do this today" was actually published. If it
   was and members are still flat, the ask needs a concrete incentive
   (see finding 3) rather than just a pinned message — reposting a few
   clips to the dormant TikTok/YouTube is what was supposed to close the
   loop, and that hasn't happened either per finding 1.

3. **NEW — the back-to-school marketing window flagged last week is now
   closing, and a second competitor is inside it.** Apex's Minecraft
   Scholarship closed its submission window in late July with winners
   drawn in early August — that seasonal moment is now essentially over
   for Apex. Meanwhile BisectHosting is currently running a live "Student
   Discount — 10% off all hosting plans" promo (confirmed via August 2026
   coupon listings), explicitly riding the same back-to-school timing.
   Last week's suggested scaled-down Discord contest is still unstarted,
   and the seasonal relevance that makes it timely (not just a generic
   contest) has maybe 1-2 weeks left before "back to school" stops being
   a live hook.
   → *Action:* If the Discord back-to-school contest from last week's
   report is going to happen, this week is the last realistic window —
   launch it now rather than carrying it forward a third week.

### Do this today (<1 hour)
Post the Discord back-to-school contest call now (e.g. "best back-to-school
server setup," free month of hosting as the prize) — it's the one item on
this list that gets materially less valuable the longer it waits, since the
seasonal hook closes in the next 1-2 weeks and BisectHosting/Apex are both
already inside it.

**Escalation status:** YouTube 404 (first flagged 07-24, hard-404 confirmed
07-31) crosses its second consecutive unresolved week today and is
escalated above with a stronger recommendation (remove the link, not just
"check it"). Discord community-clips ask (open since 07-24) is not
escalated on its own but is reframed above now that a week of flat
membership data suggests the ask alone isn't sufficient.

---

## 2026-08-08 (Saturday) — Off-Rotation Check-In

**Note:** Fifth unassigned-weekday run (rotation covers Mon–Fri only, cron
fires daily). Re-fetched raw HTML for the homepage, `/games/`, and
`/games/fivem/` directly, re-checked `youtube.com/@officiallumixsolutions`,
and re-pulled the Discord invite API to check for movement since Friday's
report.

### Findings (max 3)

1. **NEW — the `/games/fivem/` page now contradicts itself in real time:
   its own scrolling ticker banner claims Miami is live while the location
   picker two scrolls down still marks it sold out.** Raw HTML confirms a
   ticker item reading "Miami datacenters are now live - choose your
   region for lower latency" cycling on the exact same page where the
   location step still shows "Miami, FL — Sold Out — Out of capacity" next
   to Ashburn as the only available region (unchanged since 07-29). This
   is a sharper version of the "12 PoPs" mismatch this log has tracked
   since 07-29/08-05 — that one required comparing a homepage stat against
   a different page's wizard; this is the same page telling a prospect in
   one breath to "choose your region" for Miami and blocking that exact
   choice in the next.
   → *Action:* Either update or remove the "Miami datacenters are now
   live" ticker line until Miami capacity actually reopens, or change its
   wording to something accurate (e.g. "Ashburn now live — Miami capacity
   full"). This is separate from, and more urgent than, the standing "12
   PoPs vs. 2 locations" homepage-stat finding, since this one actively
   misdirects a prospect mid-purchase rather than just overstating a trust
   stat elsewhere on the site.

2. **Evergreen discount code gap is now 19 days unresolved** (baseline
   07-20, escalated 07-27 at 7 days, flagged as needing a direct owner
   decision 08-03 at 14 days). Re-confirmed today via raw HTML on the
   homepage, `/games/`, and `/games/fivem/` — still no code, voucher, or
   sale banner anywhere. No new analysis; carrying the day count forward
   for Monday's pricing-track re-check, which is the right place for this
   to get a real decision rather than another log line.

3. **Homepage meta description is now 16 days unresolved** — still
   byte-for-byte "Infrastructure built by engineers. Node.js servers, game
   services, voice infrastructure, and enterprise DDoS protection" (raw
   HTML re-confirmed today). The homepage `<title>` half of this same
   finding was fixed 08-02; the meta description half has had ready-to-
   paste replacement copy sitting in this log since 07-23 and has now been
   re-mentioned in nine separate entries without being touched.

**Unchanged since Friday (not re-listed as findings):**
`youtube.com/@officiallumixsolutions` still hard-404s. Discord membership
is flat (129 members, 21 online, vs. Friday's 130/19) — consistent with
Friday's finding that the community-clips ask alone isn't moving the
number. The homepage's "enterprise-grade... No buzzwords" line (08-04's
"do this today") and the FiveM Starter NVMe/vCore callout (08-03's "do
this today") are both also still unshipped, but neither is new this run.

### Do this today (<1 hour)
Fix or remove the "Miami datacenters are now live - choose your region for
lower latency" ticker banner on `/games/fivem/` — it's actively telling a
prospect to pick a location the same page's wizard has marked sold out.
Highest-leverage item today: it's a live, self-contradicting statement on
the exact page where a purchase decision gets made, not a slow-burn
backlog item like the other two findings above.

**Escalation status:** Evergreen discount code (pricing track) crosses 19
days unresolved today. Homepage meta description (SEO/copy track) crosses
16 days unresolved today. Neither is newly escalated this run — both were
already past threshold — carried forward with updated day counts ahead of
Monday's pricing re-check.

---

## 2026-08-09 (Sunday) — Off-Rotation Check-In

**Note:** Sixth unassigned-weekday run (rotation covers Mon–Fri only, cron
fires daily). Re-fetched raw HTML for the homepage and `/games/fivem/`
directly, re-checked `youtube.com/@officiallumixsolutions`, and re-pulled
the Discord invite API to check for movement since Saturday's report.
Nothing structurally new this run — this is a quiet continuation day, day
counts only.

### Findings (max 3)

1. **Saturday's Miami ticker/wizard contradiction is confirmed still live,
   unfixed one day after being flagged as the "do this today" item.** Raw
   HTML re-pull of the homepage and `/games/fivem/` today shows the ticker
   still cycling "Miami datacenters are now live - choose your region for
   lower latency" while the location step on the same FiveM page still
   marks Miami, FL as "Sold Out — Out of capacity" with Ashburn, VA as the
   only available region — byte-for-byte the same contradiction reported
   08-08. Not yet at the 7-day escalation threshold (1 day old), but it's
   the one open item on the board that was explicitly called zero-effort
   and highest-leverage yesterday and still hasn't moved.
   → *Action:* Same fix as yesterday — update or remove the "Miami
   datacenters are now live" ticker line until Miami capacity actually
   reopens, or reword it to something accurate (e.g. "Ashburn now live —
   Miami capacity full").

2. **Evergreen discount code gap is now 20 days unresolved** (baseline
   07-20, escalated 07-27 at 7 days, flagged as needing a direct owner
   decision 08-03 at 14 days). Re-confirmed today via raw HTML on the
   homepage and `/games/fivem/` — still no code, voucher, or sale banner
   anywhere. This is now the single oldest continuously-open item in the
   entire log, just under three full weeks with zero visible movement or
   an on-record reason why. No new analysis; carrying the day count
   forward for tomorrow's Monday pricing-track re-check.

3. **Homepage meta description is now 17 days unresolved** — still
   byte-for-byte "Infrastructure built by engineers. Node.js servers, game
   services, voice infrastructure, and enterprise DDoS protection" (raw
   HTML re-confirmed today). Ready-to-paste replacement copy has been
   sitting in this log since 07-23 and has now been re-mentioned in ten
   separate entries without being touched.

**Unchanged since Saturday (not re-listed as findings):**
`youtube.com/@officiallumixsolutions` still hard-404s, footer link
unchanged. Discord membership is flat (129 members, 18 online, vs.
Saturday's 129/21) — consistent with the flat trend noted 08-07/08-08. The
homepage hero's "enterprise-grade DDoS protection. No buzzwords, just
infrastructure that works" self-contradiction (08-04's "do this today") is
also still unshipped — re-confirmed present in today's raw HTML — now 5
days old, not yet at the 7-day threshold but worth watching for Tuesday's
copy-track re-check.

### Do this today (<1 hour)
Same as yesterday, still outstanding: fix or remove the "Miami datacenters
are now live - choose your region for lower latency" ticker banner on the
homepage and `/games/fivem/`. It's a live, self-contradicting statement on
the exact page where a purchase decision gets made — a full day older than
when it was first flagged as the single highest-leverage item on the
board, with zero dependencies blocking it.

**Escalation status:** Evergreen discount code (pricing track) crosses 20
days unresolved today. Homepage meta description (SEO/copy track) crosses
17 days unresolved today. Neither is newly escalated this run — both were
already past threshold — carried forward with updated day counts ahead of
tomorrow's Monday pricing re-check (Week 4).

---

## 2026-08-10 (Monday) — Competitor Pricing & Plans (Week 4)

**Note:** Three weeks since the 07-20 baseline. Re-fetched Lumix's homepage
and `/games/fivem` directly (raw content, not cached). RocketNode and
BisectHosting fetched live and directly; Apex, ZAP-Hosting, and Shockbyte
all blocked direct fetch again this run (403/404, consistent with prior
weeks' intermittent blocks), so those three were re-confirmed via search
instead. No structural change on the competitor side this week — same
five providers, same tier structures and discount mechanics observed on
07-20, 07-27, and 08-03. The story this run is the discount-code gap
crossing three full weeks with no owner decision on record, and the
billing-cycle-discount gap (new 08-03) crossing its first 7-day threshold
today.

### Findings (max 3)

1. **ESCALATION — evergreen discount code gap is now 21 days unresolved,
   three full weeks, with no decision on record since 08-03 explicitly
   asked for one.** Re-confirmed today via direct fetch: still no code,
   voucher, or sale banner anywhere on the homepage or `/games/fivem`.
   Meanwhile all five competitors checked this run still run active
   discount mechanisms: ZAP-Hosting's permanent 20%-off voucher (code
   `Keishin-a-8710`) is still live; Apex's `APEX25` (25% off first
   invoice, all billing cycles) still verified working; Shockbyte has
   multiple live codes (`LAUNCH` 25% off any plan, `SHOCK10` 10% off for
   life); RocketNode's "Summer Sale — Up to 25% Off" is confirmed still
   running through Sep 25; BisectHosting's billing-cycle discounts (10%
   quarterly / 15% semi-annual / 20% annual) are unchanged. This is now
   the ninth straight check (07-20, 07-25 through 08-09, and today) with
   the same finding and the same requested action.
   → *Action:* This should not appear as a tenth log line next Monday.
   Whoever owns pricing needs to give a yes-or-no answer this week: either
   there's a real blocker (payment processor, margin, strategy) worth
   recording so this stops re-surfacing, or `LUMIX10` (or equivalent)
   ships to `/games/` and gets pinned in Discord.

2. **ESCALATION — Lumix's billing-cycle discount ceiling crosses 7 days
   unresolved today, first flagged as a new gap 08-03.** Re-fetched
   `/games/fivem` today: still 5% quarterly, 5% semi-annual, 5% annual,
   10% biennial/triennial only — byte-for-byte unchanged from 08-03.
   RocketNode's FiveM page, re-confirmed today: 5% quarterly, 12%
   semi-annual, 20% annual. BisectHosting, re-confirmed today: 10%
   quarterly, 15% semi-annual, 20% annual. At the one-year commitment
   point — the most common comparison a prospect makes — Lumix offers 5%
   against a 20% category norm at both competitors checked directly this
   run.
   → *Action:* Same ask as 08-03, now overdue for a response: confirm
   whether a 20% annual discount is a real margin problem or just an
   unrevisited number. Matching the annual figure alone (leaving
   quarterly/semi-annual as-is) would close the most visible part of this
   gap without touching the evergreen-code question in finding 1.

3. **RocketNode's FiveM tiers and specs are confirmed byte-for-byte
   unchanged since the 07-29 audit (Starter $6.50/2GB = $3.25/GB up to
   God $98.50/32GB), and its "Summer Sale" has a known end date (Sep 25)
   that's still six weeks out.** This means the ~38% list-price gap and
   the deeper sale-driven gap flagged 08-03 aren't closing on their own
   anytime soon — this is a stable, multi-week pricing pressure point,
   not a short-lived promo Lumix can simply wait out.
   → *Action:* No new action beyond finding 1 and 2 — noting the timeline
   so it's clear this isn't a "check back in a week" situation on the
   competitor side.

### Do this today (<1 hour)
Ship the FiveM Starter NVMe/vCore differentiation line drafted 08-03
("More dedicated compute & NVMe storage per dollar," near the Starter
tier on `/games/fivem`) — it's the one pricing-track action item on the
board with zero dependencies while findings 1 and 2 both need an owner
decision. It's been sitting unshipped for a full week; today crosses that
threshold too.

**Escalation status:** Evergreen discount code (finding 1) crosses 21 days
(three weeks) unresolved today — the oldest continuously-open item in the
entire log. Billing-cycle discount ceiling (finding 2) crosses its first
7-day escalation today. Off-track items unchanged since yesterday, not
re-listed: homepage meta description (SEO/copy track) is 18 days
unresolved; the Miami ticker/wizard contradiction (first flagged 08-08) is
now 3 days old, still unfixed, not yet at the 7-day threshold; YouTube's
hard 404 (social track) remains unresolved since 07-31.

---

## 2026-08-11 (Tuesday) — Website Copy (Week 4)

**Note:** One week since the 08-04 entry, three weeks since the 07-21
baseline. Re-fetched the homepage, `/games/`, `/games/fivem`, and `/contact`
directly (plus a raw HTML pull of the homepage `<head>` to cross-check
title/meta, which sits on the SEO track but is relevant context here).

**Resolved since 08-04:** The homepage "What we do" section has been
rewritten. The old text — "Reliable compute, game server hosting, voice
infrastructure, and enterprise-grade DDoS protection. No buzzwords, just
infrastructure that works." — is gone. It now reads: "Lumix Solutions
provides infrastructure services for businesses and developers who need
reliability without the corporate overhead. We specialize in Node.js
application hosting, game server infrastructure, voice communication
servers, and DDoS mitigation." This closes 08-04's "do this today" item
(the "enterprise-grade... no buzzwords" self-contradiction) — but see
finding 1 below, the replacement isn't clean either.

### Findings (max 3)

1. **NEW — the rewritten hero copy fixed one vague claim but introduced
   another: "reliability without the corporate overhead" has no referent.**
   "Corporate overhead" is never defined or contrasted anywhere else on the
   site — there's no "here's what we cut" list, no pricing/support-speed
   comparison, nothing that tells a prospect what "corporate overhead"
   would have looked like. It reads as the same genre of unproven claim
   the old "no buzzwords" line was, just relocated to a different sentence
   in the same paragraph.
   → *Action:* Replace with something concrete Lumix can actually back up —
   e.g. if support response time or a flat org structure is the real
   differentiator, say that number/fact directly instead of "without the
   corporate overhead."

2. **NEW — the homepage ticker now includes a claim with zero proof
   attached: "Production and development are better than ever - faster
   builds, cleaner systems, and improved stability."** "Better than ever"
   has no baseline (better than what — last month? last year?) and none of
   "faster," "cleaner," or "improved" are attached to a number. This is the
   exact pattern this track exists to catch (per 07-21's original framing:
   claims like "premium" with nothing backing them), just showing up in the
   ticker rotation rather than the hero this time.
   → *Action:* Either attach a real number (e.g. "builds Nx faster since
   [date/change]") or cut the line — a vague self-congratulatory claim in a
   ticker that also carries real operational info (Miami capacity, bot
   hosting capacity) dilutes the ticker's credibility for the claims that
   *do* matter.

3. **ESCALATION — Bot/Application hosting still has no product listing on
   `/games/`, now 14 days unresolved (first flagged 07-28).** Re-fetched
   `/games/` today: same five product cards (FiveM, Minecraft, Palworld,
   BeamMP, Terraria) plus the same four Coming Soon teasers — no Bot
   Hosting card in either list. The only sitewide mentions remain ticker/
   banner lines ("Expanded bot hosting capacity...") and, as of this week's
   hero rewrite, the phrase "Node.js application hosting" in the "What we
   do" paragraph — still nowhere a prospect can see a price, spec, or CTA
   for it. Two full weeks with no visible movement on a fix this log has
   now logged four times (07-28, 07-30, 08-04, 08-06 on the SEO track).
   → *Action:* This has been "no update" for a full month combined across
   tracks — worth a direct, non-routine ask to whoever owns the `/games/`
   catalog: is a Bot Hosting card blocked on something (pricing not
   finalized, product not ready) or just not scheduled? If blocked, that
   reason is worth recording so this stops re-appearing weekly.

### Do this today (<1 hour)
Cut or fix the ticker line "Production and development are better than
ever - faster builds, cleaner systems, and improved stability" (finding 2)
— it's the single unproven claim on the site with no dependency on anyone
else's decision (unlike findings 1 and 3, which need a copywriting call or
a product-catalog owner). Lowest-effort fix on today's board.

**Escalation status:** Bot/Application hosting listing gap (finding 3)
crosses 14 days unresolved today. Also still open, not re-listed since
unchanged from last check and off today's track: FiveM scarcity claim with
no cap number (first flagged 07-28, 14 days) and CTA naming inconsistency
("Contact Sales" on the homepage still doesn't match any label on
`/contact`, first flagged 07-28, 14 days) — both confirmed still present in
today's fetch, carrying forward rather than re-analyzed since neither
changed. Evergreen discount code (pricing track) is unchanged at 22 days.
Homepage meta description (SEO track) is unchanged, still the same
"Infrastructure built by engineers..." text, now 19 days unresolved — raw
HTML re-confirmed today. Miami ticker/wizard contradiction (off-track, first
flagged 08-08) is unchanged, now 4 days old, not yet at the 7-day
threshold.

---

## 2026-08-12 (Wednesday) — Competitor UX Deep-Dive: ZAP-Hosting

**Note:** Fourth UX-track entry, rotating to ZAP-Hosting (tracked on the
pricing track since 07-20 but never its own UX-track subject). Shockbyte
was attempted again first — its order/knowledgebase pages returned HTTP 403
to fetch tools for a third consecutive attempt (07-22, 08-05's note, and
again today), so it's being skipped again this cycle. ZAP's dedicated
`rent-a-fivem-server` page was fetched live for comparison. While pulling
Lumix's own `/games/fivem` for the comparison, this run found a
substantially more urgent problem than any competitor gap — see finding 1.

**Flows observed:**
- **ZAP-Hosting:** FiveM page lists 8 selectable regions (Dallas, Los
  Angeles, and Ashburn in the US; Frankfurt/Eygelshoven, Germany; Montreal;
  Singapore; Sydney; London), starting at $9.08/mo, headlined "Online in 5
  minutes." No location shown as sold out or unavailable.
- **Lumix (`/games/fivem` and `/games/minecraft`, both re-fetched live
  today):** Both pages' location step now show **Miami, FL and Ashburn,
  VA — the site's only two datacenters — as "Sold Out — Out of capacity —
  no new deployments."** The wizard states outright: "Every region is at
  capacity right now, so this game cannot be deployed," and directs
  prospects to "Ask in Discord for an ETA." There is currently no location
  a new customer can select for either product.

### Findings (max 3)

1. **NEW, CRITICAL — Lumix's FiveM and Minecraft signup flows are
   completely non-purchasable right now: zero deployable locations on
   either product.** This is new since yesterday's check (08-11's entry,
   and every prior check back to 08-08, described Ashburn as the one
   available region with only Miami sold out). As of today's direct fetch,
   Ashburn has also flipped to sold out on both `/games/fivem` and
   `/games/minecraft` — the site's only two datacenters are both full, and
   the wizard tells prospects outright the product "cannot be deployed,"
   pointing them to Discord for an ETA instead of a self-service path.
   Two of Lumix's four core product lines currently cannot be sold to a
   new customer through the website at all, regardless of any copy or UX
   fix — this is a revenue-blocking capacity outage, not a marketing
   finding.
   → *Action:* This needs to go to whoever owns infra/capacity today, not
   wait for next week's log — confirm whether this is a real, hard sellout
   or a stale/misconfigured capacity flag, and get a real ETA. Until
   capacity reopens, the wizard's dead-end state should at minimum collect
   an email/Discord handle for a waitlist instead of just "ask in
   Discord" — right now an interested prospect who lands here has no way
   to be recontacted when a slot opens.

2. **The standing "Miami datacenters are now live" ticker claim (open since
   08-08) is now actively false, not just contradictory.** The ticker on
   `/games/fivem` still reads "Miami datacenters are now live - choose
   your region for lower latency" — but as of finding 1, Miami is sold
   out and so is the only other region, so there is no region to choose at
   all. What was a same-page contradiction for the last 4 days is now a
   claim with zero truth behind it during an active outage.
   → *Action:* Pull this ticker line immediately (see "do this today") —
   it's actively misleading a prospect into thinking a purchase path exists
   when it doesn't, which is worse than the standing "12 PoPs" trust-stat
   overstatement it was already flagged alongside.

3. **ZAP-Hosting's FiveM flow offers 8 live, selectable regions across
   three continents with a "5 minutes" speed claim front and center, the
   sharpest version yet of the standing capacity/footprint gap this track
   has tracked since 07-29 (RocketNode) and 08-05 (Apex).** Both prior
   UX-track entries compared Lumix's claimed "12 PoPs" against a 2-location
   reality; today's comparison competitor has more live, orderable regions
   (8) than Lumix has datacenters at all (2), and right now Lumix has zero
   usable ones. This isn't a "match the category norm" gap anymore — it's
   the difference between a working purchase flow and a dead end.
   → *Action:* Once finding 1 is resolved and capacity reopens, this is
   the same recommendation as 07-29/08-05, now with more urgency: either
   grow real capacity toward the claimed "12 PoPs," or stop claiming a
   PoP count the live wizard can't currently back up in any way.

### Do this today (<1 hour)
Two things, both zero-dependency copy fixes: (1) remove or reword the
"Miami datacenters are now live" ticker line on `/games/fivem` — it's now
false, not just contradictory, per finding 2; (2) replace the wizard's
dead-end "cannot be deployed... ask in Discord" state with a one-line
capacity-waitlist form (even a mailto: or a Discord invite link framed as
"get notified") so a prospect hitting the sold-out state today has
somewhere to go besides leaving the site. Escalating the actual capacity
shortage (finding 1) to infra/ops is the more important action but isn't a
marketing-side task completable in an hour.

**Escalation status:** Miami ticker/wizard contradiction (first flagged
08-08) crosses 5 days today, now subsumed by and reported as part of
findings 1–2 above rather than as a standalone re-log. Evergreen discount
code (pricing track) is unchanged at 23 days. Homepage meta description
(SEO track) is unchanged at 20 days. Bot/Application hosting listing gap
(copy/SEO tracks) is unchanged at 15 days. Shockbyte remains blocked to
fetch tools for a third straight UX-track attempt — worth trying a
different access method (e.g. a non-automated manual check) if it's still
blocked at the next rotation.

---

## 2026-08-13 (Thursday) — SEO & Keywords (Week 5)

**Note:** One week since the 08-06 entry. Pulled raw HTML directly (title,
meta description, JSON-LD) for the homepage, `/games/fivem/`,
`/games/minecraft/`, and `/games/terraria/`; re-fetched `sitemap-0.xml`;
re-checked the same six likely bot-hosting URLs (all still 404); and ran
fresh unbranded searches ("fivem server hosting," "cheap minecraft server
hosting," "discord bot hosting node.js python") plus a new `site:
lumixsolutions.org` search to see what Google is actually showing
searchers right now, not just what's live in the HTML.

**Still active from yesterday's UX-track run, not re-analyzed here:** the
08-12 finding that both of Lumix's datacenters (Miami and Ashburn) show
"Sold Out — Out of capacity" on `/games/fivem/` — re-confirmed via raw
HTML today, still true, now day 2. The homepage ticker still reads "Miami
datacenters are now live - choose your region for lower latency," which
remains actively false. This is a revenue-blocking capacity issue outside
this track's scope to analyze further, but it directly undercuts today's
SEO findings below (there's little point ranking for "fivem server
hosting" if the page a searcher lands on can't sell them a server) — see
escalation status.

### Findings (max 3)

1. **NEW — Google's live search results for the homepage still show the
   pre-08-02 title, 11 days after the on-page tag changed.** A fresh
   `site:lumixsolutions.org` search today returns the homepage with the
   title "Lumix | Lumix Solutions LLC" — the original generic title this
   track first flagged 07-23. The raw HTML confirms the live tag has read
   "Game Server & VPS Hosting | Lumix Solutions" since 08-02, so the fix
   genuinely shipped — but nothing in this log has checked whether Google
   picked it up until today. It hasn't, 11 days later. The same search
   shows `/games/` and `/games/terraria/` already indexed with their
   correct, current titles, so indexing itself isn't broken sitewide —
   specifically the homepage's cached snippet is stale. Anyone finding
   Lumix by searching its own name right now still sees the keyword-empty
   title this log has been trying to get fixed for three weeks.
   → *Action:* Submit the homepage URL for re-indexing via Google Search
   Console's URL Inspection tool (if no Search Console account exists,
   that's a bigger gap worth its own note — this log has been assuming a
   passive wait for re-crawl this whole time with no verification it's
   happening at all).

2. **ESCALATION — homepage meta description is now 21 days unresolved,
   still the oldest continuously-open item in this log.** Raw HTML
   confirms it is still byte-for-byte "Infrastructure built by engineers.
   Node.js servers, game services, voice infrastructure, and enterprise
   DDoS protection" — unchanged since 07-23, despite ready-to-paste
   replacement copy sitting in this log for three weeks and being
   re-mentioned in twelve separate entries. Combined with finding 1, this
   means the homepage's actual search-facing footprint (both the live meta
   tag and Google's cached title) is fully unfixed on every axis this
   track measures.
   → *Action:* Paste the already-drafted description: "FiveM, Minecraft,
   Terraria, and Discord bot hosting with DDoS protection and sub-10ms
   latency. Deploy in under 60 seconds." Same one-line fix logged since
   07-23.

3. **ESCALATION — Bot/Application hosting still has zero SEO footprint, now
   14 days unresolved (second consecutive weekly escalation).** Re-checked
   today: `sitemap-0.xml` now lists 18 URLs (up from 12 on 08-06 — new
   entries are `/career/`, `/career/application/`, `/ccpa/`, `/changelog/`,
   `/status/`, `/terms/`, none game- or keyword-related), still with no bot
   hosting entry; the same six likely URLs (`/games/bot/`,
   `/games/bot-hosting/`, `/games/application/`, `/games/apps/`,
   `/games/nodejs/`, `/games/node/`) are all still 404. This week's fresh
   search for "discord bot hosting node.js python" again surfaces only
   competitors (YorkHost, LordHosting, XeroHost, ABR Hosting, Wispbyte) —
   lumixsolutions.org appears nowhere. One of Lumix's four core product
   lines remains invisible to search a full month after this gap was first
   logged (07-28/07-30).
   → *Action:* Unchanged — once a Bot Hosting product page exists (open on
   the copy track since 07-28, now also 14+ days), give it the same
   title/meta/sitemap treatment as the five game pages.

### Do this today (<1 hour)
Two small, connected actions on the homepage: (1) paste the already-drafted
meta description (finding 2) — zero new writing, three weeks overdue; (2)
immediately after, submit the homepage through Google Search Console's URL
Inspection → "Request Indexing" so the title fix that shipped 08-02 and
today's meta fix both actually reach Google's index instead of waiting on a
passive re-crawl that hasn't happened in 11 days. Five minutes combined,
directly closes findings 1 and 2 together.

**Escalation status:** Homepage meta description (finding 2) crosses 21
days unresolved today. Bot/Application hosting SEO gap (finding 3) crosses
14 days, second escalation. Product/Offer JSON-LD schema gap (first flagged
07-30, escalated 08-06) is unchanged — still no `Product`/`Offer` markup on
`/games/fivem/`, `/games/minecraft/`, or `/games/terraria/` per today's raw
HTML — now also 14 days, not re-analyzed in full since nothing moved.
Evergreen discount code (pricing track) is unchanged at 24 days. **The
capacity outage found 08-12 (both Miami and Ashburn sold out on FiveM,
Minecraft affected too) is unresolved and now on day 2** — flagging again
here since it directly undercuts this track's entire purpose and has not
been logged as resolved on any track since it appeared.

---

## 2026-08-14 (Friday) — Social & Community (Week 4)

**Note:** Three weeks since the 07-24 baseline. Re-fetched the homepage
footer (all five social links unchanged), re-checked
`youtube.com/@officiallumixsolutions` directly, re-pulled the Discord
invite API (`uaNYBJQtvn`), re-fetched `/games/fivem` for ticker/capacity
status, and searched for movement on last week's two open items: the
back-to-school Discord contest and competitor back-to-school promos.

### Findings (max 3)

1. **ESCALATION — YouTube footer link is still a hard 404, now a full
   month since first flagged (07-24) and the fourth consecutive Friday
   with zero movement.** Direct fetch of
   `youtube.com/@officiallumixsolutions` today returns the same HTTP 404
   confirmed on 07-31, 08-07, and every check since. Three straight
   "do this today" asks (07-31, 08-07, and implicitly since) to either
   confirm/restore the account or pull the link have not been acted on.
   → *Action:* Stop asking whoever owns the account to check it — just
   remove the YouTube icon from the footer this week. A month-old dead
   link in a hosting company's own footer is a worse trust signal than
   having one fewer social icon, and this item has proven a reminder
   alone won't fix it.

2. **NEW — Discord membership shows its first real growth in three weeks
   (130→133 members since last Friday), but there's no way to confirm
   from outside whether the back-to-school contest that was supposed to
   ship 08-07 ever launched.** Member count moved from 128 (07-31) to 130
   (08-07) to 133 today — a modest but real +3 net gain after two
   consecutive weeks of being flat or dipping (129/130 range, online
   count oscillating 18-24). Presence is at 19 online, in the same range
   as prior weeks. This is a positive signal, but 08-07's report said the
   back-to-school seasonal window had "1-2 weeks left" and needed to
   launch that week or lose relevance — today is exactly at that
   boundary, and this run has no visibility into Discord message history
   to confirm the contest was actually posted.
   → *Action:* Confirm directly whether the back-to-school Discord post
   went out. If it did, this growth may be early signal it's working —
   worth a follow-up post pointing to any submissions before the window
   fully closes. If it didn't go out, the seasonal hook is now gone;
   don't carry it forward as a live action item next week.

3. **The standing FiveM/Minecraft capacity outage (both Miami and Ashburn
   sold out, first found 08-12) is still unresolved on day 3, and it
   directly undercuts this week's core recommendation.** Re-fetched
   `/games/fivem` today: both locations still read "Sold Out — Out of
   capacity — no new deployments," and the ticker still claims "Miami
   datacenters are now live - choose your region for lower latency" —
   still false. This isn't a new finding (already logged 08-12, 08-13 on
   other tracks), but it's directly relevant here: any push to grow
   Discord/TikTok/YouTube engagement this week is driving prospects
   toward a signup flow that currently can't sell FiveM or Minecraft to a
   new customer at all.
   → *Action:* Until capacity reopens, frame any community content
   (including finding 2's contest) around existing customers only — e.g.
   "show off your server" rather than anything implying new signups are
   open — so social effort isn't spent driving prospects into a dead end.

### Do this today (<1 hour)
Remove the YouTube icon/link from the site footer (finding 1). It's been
a confirmed dead link for a full month across four separate check-ins
with no fix — the lowest-effort, zero-dependency action left on this
item, and the one this log will stop re-logging if it's finally done.

**Escalation status:** YouTube 404 (first flagged 07-24) crosses one full
month unresolved today, its fourth consecutive weekly escalation. FiveM/
Minecraft capacity outage (cross-track, first flagged 08-12) is unchanged
on day 3 — re-flagged here due to direct relevance to this week's social
findings, not re-analyzed. Evergreen discount code (pricing track) and
homepage meta description (SEO track) are both unchanged since Thursday's
check-in; not re-listed since neither falls on today's track.

---

## 2026-08-15 (Saturday) — Off-Rotation Check-In

**Note:** Seventh unassigned-weekday run (rotation covers Mon–Fri only,
cron fires daily). Re-fetched raw HTML for the homepage, `/games/fivem/`,
and — for the first time this week — `/games/minecraft/` directly, to
specifically check whether the 08-12 capacity outage (both flagged
products) had moved. Also re-checked `youtube.com/@officiallumixsolutions`
and the Discord invite API for movement since Friday's report.

### Findings (max 3)

1. **RESOLVED — the FiveM/Minecraft capacity outage first flagged 08-12 is
   fixed as of today, on both affected products.** Raw HTML for both
   `/games/fivem/` and `/games/minecraft/` now shows Miami, FL and
   Ashburn, VA as selectable, unlabeled location options — no "Sold Out,"
   "Out of capacity," or "no new deployments" text anywhere on either page
   (confirmed by direct grep of the raw markup, not just a rendered read).
   Miami is even the pre-selected default option on the FiveM builder. This
   closes a critical, revenue-blocking finding that sat open for 3 days
   across three log entries (08-12, 08-13, 08-14) and, as a side effect,
   makes the "Miami datacenters are now live" ticker line accurate again —
   it was flagged 08-12 as actively false during the outage, and is simply
   true again now that capacity has reopened.
   → *Action:* None needed on the capacity fix itself. Worth a one-line
   confirmation from whoever owns infra that this was a real re-provision
   (not a flag flipped back on stale capacity) so it doesn't silently
   recur — otherwise no further tracking required on this track.

2. **Evergreen discount code gap is now 26 days unresolved** (baseline
   07-20, escalated 07-27 at 7 days, flagged as needing a direct owner
   decision 08-03 at 14 days). Re-confirmed today via raw HTML on the
   homepage and `/games/fivem/` — still no code, voucher, or sale banner
   anywhere. This is now the single oldest continuously-open item in the
   entire log, closing in on four full weeks with no on-record decision
   either way. No new analysis; carrying the day count forward for
   Monday's pricing-track re-check (Week 5).

3. **The YouTube footer link is still live and still hard-404s, 22 days
   after first flagged (07-24) and 8 days after the direct ask (08-14) to
   simply remove it rather than keep asking someone to check the
   account.** Direct fetch of `youtube.com/@officiallumixsolutions` today
   returns the same 404 confirmed every check since 07-31. The footer on
   today's homepage fetch still links to it. Four consecutive "do this
   today" asks (07-31, 08-07, 08-14, and this one) have now targeted this
   exact one-line fix without it shipping.
   → *Action:* Same as last three runs — remove the YouTube icon/link from
   the site footer. No dependency on anyone confirming account status
   first; that ask has already gone unanswered for three weeks.

**Unchanged since Friday (not re-listed as findings):** Homepage meta
description is still byte-for-byte "Infrastructure built by engineers...,"
now 23 days unresolved. Discord membership is flat (133 members, 17
online, vs. Friday's 133/19) — no movement to report either way on the
back-to-school contest's effect. No Bot Hosting card exists on `/games/`
(unchanged, 18+ days). The "Limited FiveM servers stock available"
scarcity-claim ticker line (no cap number, first flagged 07-28) is still
present, unchanged.

### Do this today (<1 hour)
Remove the YouTube icon/link from the site footer (finding 3). It's the
one item on today's board that's a pure zero-dependency copy/markup edit
with three prior asks already on record — the capacity fix (finding 1)
already shipped and the discount code (finding 2) needs an owner decision,
not a marketing-side edit.

**Escalation status:** Evergreen discount code (pricing track) crosses 26
days unresolved today, still the oldest open item in the log. YouTube 404
(social track) is unchanged at 22 days, now past its fourth consecutive
"do this today" ask. Homepage meta description (SEO track) is unchanged at
23 days. The FiveM/Minecraft capacity outage (cross-track, first flagged
08-12) is resolved as of today — dropped from the escalation list.

---

## 2026-08-16 (Sunday) — Off-Rotation Check-In

**Note:** Eighth unassigned-weekday run (rotation covers Mon–Fri only, cron
fires daily). Re-fetched raw HTML for the homepage and `/games/fivem/`,
re-checked `/games/` for the product catalog and Coming Soon section,
re-checked `youtube.com/@officiallumixsolutions` directly, and re-pulled
the Discord invite API. Nothing new or changed turned up this run — every
open item is exactly where Saturday's check-in left it, one day older.

### Findings (max 3)

1. **Evergreen discount code gap is now 27 days unresolved** (baseline
   07-20, escalated 07-27 at 7 days, flagged for a direct owner decision
   08-03 at 14 days). Re-confirmed via raw HTML on the homepage and
   `/games/fivem/` — still no code, voucher, or sale banner anywhere. Four
   full weeks unresolved as of tomorrow. No new analysis; carrying forward
   for Monday's pricing-track re-check (Week 6).

2. **YouTube footer link is still a hard 404, now 23 days unresolved and
   9 days past the direct ask (08-14) to simply remove it.** Direct fetch
   of `youtube.com/@officiallumixsolutions` today returns the same 404
   confirmed on every check since 07-31. The footer on today's homepage
   fetch still links to it. Five consecutive "do this today" asks
   (07-31, 08-07, 08-14, 08-15, and this one) have now targeted this exact
   one-line fix without it shipping.
   → *Action:* Same as the last four runs — remove the YouTube icon/link
   from the site footer. No dependency on anyone confirming account status
   first; that ask has gone unanswered for over three weeks.

3. **Homepage meta description is unchanged, now 24 days unresolved.**
   Raw HTML confirms it is still byte-for-byte "Infrastructure built by
   engineers. Node.js servers, game services, voice infrastructure, and
   enterprise DDoS protection" — unchanged since 07-23, despite ready-to-
   paste replacement copy sitting in this log for over three weeks.
   Homepage `<title>` remains "Game Server & VPS Hosting | Lumix
   Solutions" (unchanged since 08-02, still missing specific game
   keywords).

**Unchanged since Saturday (not re-listed as findings):** The FiveM/
Minecraft capacity fix (resolved 08-15) holds — both Miami and Ashburn
remain selectable, unlabeled options on `/games/fivem/`, no "Sold Out"
text present. Discord membership dipped slightly (132 members, 17 online,
vs. Saturday's 133/17) — within normal day-to-day noise, not a trend.
No Bot Hosting card exists on `/games/` (unchanged, 19+ days). The
"Limited FiveM servers stock available" scarcity-claim ticker line (no cap
number, first flagged 07-28) is still present, unchanged. The Coming Soon
section (ARK: Survival Ascended, Rust, Arma Reforger, Squad) is unchanged
from 08-01.

### Do this today (<1 hour)
Remove the YouTube icon/link from the site footer (finding 2). Zero
dependencies, copy-paste-simple, and now the single most-repeated unmet
ask in this log (five separate runs have flagged it as today's top
zero-effort item).

**Escalation status:** Evergreen discount code (pricing track) is at 27
days, one day short of a full four weeks. YouTube 404 (social track) is at
23 days. Homepage meta description (SEO track) is at 24 days. No item
crossed a new escalation threshold today — all three are continuations of
already-escalated findings, not new discoveries.

---

## 2026-08-17 (Monday) — Competitor Pricing & Plans (Week 5)

**Note:** Direct fetch worked this run for Lumix's homepage and
`/games/fivem`, plus RocketNode and BisectHosting's FiveM pages. ZAP-Hosting,
Apex Hosting, and Shockbyte all blocked direct fetch again (404/403,
consistent with recent weeks) and were re-confirmed via search instead. No
structural change on either side this week — same five competitors, same
tier structures, same discount mechanics as every prior check since 07-20.
The story this run is two prior findings crossing new day-count milestones,
not anything new.

### Findings (max 3)

1. **ESCALATION — evergreen discount code gap hits 28 days today, a full
   four weeks unresolved with no owner decision ever recorded.** Re-fetched
   Lumix's homepage and `/games/fivem` directly today: still no code,
   voucher, or sale banner anywhere. Meanwhile all five competitors checked
   this run still run live discount mechanisms: ZAP-Hosting's permanent
   20%-off voucher (`Keishin-a-8710`) reconfirmed active; Shockbyte has
   multiple live codes (`TWITTER25`, `SHOCK10` 10% for life, `LAUNCH` 25%
   off); Apex's `APEX25` reconfirmed; RocketNode's "Summer Sale — Up to 25%
   Off" is still running (through Sep 25, now ~5.5 weeks out); BisectHosting's
   billing-cycle discounts are unchanged. This is now the tenth-plus
   consecutive check-in (every Monday since 07-20, plus most off-rotation
   Sat/Sun runs) logging the identical gap with the identical requested
   action.
   → *Action:* This needs a yes-or-no from whoever owns pricing this week,
   not another log line next Monday: either there's a real blocker worth
   recording, or `LUMIX10` (or equivalent) ships to `/games/` and gets
   pinned in Discord. If no decision lands by next Monday, this crosses
   five full weeks unresolved.

2. **ESCALATION — billing-cycle discount ceiling hits 14 days unresolved
   today** (first flagged 08-03, escalated at 7 days on 08-10). Re-fetched
   `/games/fivem` today: still 5% quarterly, 5% semi-annual, 5% annual, 10%
   biennial/triennial — byte-for-byte unchanged. RocketNode, re-confirmed
   live today: 5% quarterly, 12% semi-annual, 20% annual. At the one-year
   commitment point, Lumix still offers 5% against a 20% category norm.
   → *Action:* Same ask as 08-03 and 08-10, now two weeks overdue: confirm
   whether a 20% annual discount is a real margin problem or just an
   unrevisited number. Matching the annual figure alone would close the
   most visible part of this gap without touching finding 1.

3. **No new competitor pricing moves to report this week.** RocketNode's
   FiveM tiers (Starter $6.50/2GB up to God $98.50/32GB) and Lumix's own
   tiers ($8.99/2GB Starter up to $52.99/16GB Ultimate) are both unchanged
   from prior audits — the ~38% list-price gap at the entry tier stands as
   logged 08-03/08-10, not worsening or improving on its own.
   → *Action:* None beyond findings 1 and 2 — noted so this week's entry
   isn't mistaken for a fresh audit finding a new gap.

### Do this today (<1 hour)
Get a yes/no from the pricing owner on the evergreen discount code
(finding 1). It's the single oldest, most-repeated open item in this log
(28 days, every check-in since the baseline) and the one action that
unblocks itself the moment someone answers it — no research or design work
left to do, the code name and placement have been proposed since 07-20.

**Escalation status:** Evergreen discount code (pricing track) crosses 28
days (four full weeks) unresolved today — still the oldest continuously-open
item in the log. Billing-cycle discount ceiling (pricing track) crosses 14
days today. Off-track items not re-checked this run (pricing-track day):
YouTube 404 (social track) was at 23 days as of 08-16; homepage meta
description (SEO/copy track) was at 24 days as of 08-16.

---

## 2026-08-18 (Tuesday) — Website Copy (Week 5)

**Note:** One week since the 08-11 entry. Re-fetched the homepage (raw HTML,
not just rendered), `/games/`, and `/contact` directly to check the three
08-11 findings for movement and confirm nothing new appeared on the pages
this track covers.

**Confirmed unchanged since 08-11 (verified via raw HTML, not just a
rendered read):** The hero "What we do" copy is byte-for-byte identical —
"Lumix Solutions provides infrastructure services for businesses and
developers who need reliability without the corporate overhead. We
specialize in Node.js application hosting, game server infrastructure,
voice communication servers, and DDoS mitigation." The four ticker lines
are unchanged. `/games/` still lists the same five priced product cards
(FiveM, Minecraft, Palworld, BeamMP, Terraria) plus the same four Coming
Soon teasers, no Bot Hosting card. One small, unprompted change: the old
"Talk to an engineer" CTA string no longer appears anywhere on the
homepage — only "Contact Sales" remains as the sales-contact CTA, which
happens to resolve half of 07-28's CTA-naming-inconsistency finding on its
own (not worth a new finding slot, but note it since that finding has been
carried forward for three weeks).

### Findings (max 3) — all escalated (7+ days unresolved)

1. **ESCALATION — the "corporate overhead" claim (08-11's finding 1) hits
   7 days unresolved today, still with no referent anywhere on the site.**
   Raw HTML confirms the sentence is unchanged: "...reliability without the
   corporate overhead." Checked the full homepage, `/games/`, and `/contact`
   again for any list, comparison, or stat that defines what "corporate
   overhead" means or what Lumix cut to avoid it — still nothing. This is
   the same unproven-claim pattern this track has caught repeatedly
   (07-21's "premium," 08-04's "no buzzwords / enterprise-grade"
   self-contradiction) recurring in the same paragraph a second time.
   → *Action:* Replace with a concrete, checkable fact — e.g. actual
   support response time, a flat/small-team structure, or a specific
   process Lumix skips that larger hosts don't — instead of the
   undefined "corporate overhead" contrast.

2. **ESCALATION — the ticker's unproven "better than ever" claim (08-11's
   finding 2 and "do this today" item) hits 7 days unresolved, unfixed
   despite being flagged as the single lowest-effort item on last week's
   board.** Raw HTML confirms the exact line is still live: "Production and
   development are better than ever - faster builds, cleaner systems, and
   improved stability." No baseline, no number, sitting in the same ticker
   rotation as real operational claims (Miami capacity, FiveM stock) that
   this dilutes.
   → *Action:* Same ask as last week, now overdue — either attach a real
   number/date to the claim or delete the ticker line entirely. Zero
   dependencies; this is a one-line content edit, not a design or product
   decision.

3. **ESCALATION — Bot/Application hosting listing gap hits 21 days
   unresolved (first flagged 07-28, three prior escalations: 08-04, 08-06,
   08-11).** `/games/` re-confirmed today: same five product cards, no Bot
   Hosting card, no price, no CTA. The only sitewide mentions remain a
   ticker line ("Expanded bot hosting capacity...") and the "Node.js
   application hosting" phrase in the hero paragraph — still nowhere a
   prospect can actually configure or price this product, which this
   routine's own scope treats as one of Lumix's four core product lines.
   → *Action:* This has now gone unaddressed across four consecutive
   Tuesday copy-review entries and the SEO track in parallel — worth
   treating as a standing, named backlog item rather than a recurring log
   line: get a yes/no from whoever owns the `/games/` catalog on whether a
   Bot Hosting card is blocked (pricing, product readiness) or simply
   unscheduled, and record the answer so this stops re-appearing weekly
   with no new information.

### Do this today (<1 hour)
Cut the ticker line "Production and development are better than ever -
faster builds, cleaner systems, and improved stability" (finding 2). It's
the same zero-dependency, no-decision-needed edit flagged as today's item
exactly one week ago and still hasn't shipped — the fastest way to clear
one of today's three findings outright.

**Escalation status:** Findings 1 and 2 above both cross their first 7-day
escalation today (both first flagged 08-11). Bot/Application hosting
listing gap (finding 3) crosses 21 days, third escalation. Also still open,
not re-listed as findings since unchanged and off today's specific checks:
FiveM scarcity claim with no cap number (07-28, 21 days) and the remaining
half of the CTA-naming inconsistency — "Configure" vs. "Build Your Server"
vs. "Browse Games" vs. "View Full Catalog" for plan setup (07-28, 21 days,
unaffected by today's "Talk to an engineer" removal, which only touched the
sales-contact side of that finding). Evergreen discount code (pricing
track) is at 29 days per yesterday's Monday entry, not re-checked here.
Homepage meta description (SEO track) was at 24 days as of 08-16, not
re-checked here since it's off today's track.

---

## 2026-08-19 (Wednesday) — Competitor UX Deep-Dive: BisectHosting (Week 5)

**Note:** Shockbyte was attempted first — `shockbyte.com` (root, `/hosting/minecraft`,
and a knowledgebase order-flow article) returned HTTP 403 to fetch tools
again today, a fourth consecutive blocked attempt (07-22, 08-05, 08-12, and
now 08-19). Its own published order-flow knowledgebase article was reachable
only via search-result excerpt, not direct fetch, so it's cited below as a
secondary source, not verified live. Rotated back to BisectHosting instead —
the longest-stale UX-track subject (last checked 07-22, the baseline entry)
— and re-fetched `bisecthosting.com/minecraft-server-hosting` live, plus raw
HTML for Lumix's `/games/fivem` and `/games/minecraft` (both now a real
plan → location → billing-cycle configurator, not the bare tier list from
07-22). Pulled the FiveM and Minecraft pricing JSON directly from the page
markup to check per-cycle discount math exactly rather than reading rendered
percentages.

**Flows observed:**
- **BisectHosting:** plan page → "Choose a Plan"/"HELP ME DECIDE" → guided
  selector at `/selector`: game version, RAM tier, then a **21-location**
  map-style picker ("Pick the best spot for you"), then modpack (2,300+
  options or vanilla), then billing cycle (Monthly / Quarterly -10% /
  Semi-annually -15% / Annually -20%, clean and monotonic), then optional
  BisectBoost add-on. Checkout claims "full 24/7 access to your server as
  soon as your payment clears."
- **Lumix (`/games/fivem`, `/games/minecraft`):** both now a single-page
  configurator — plan, then a 2-location picker (Miami, Ashburn — no
  latency/ms data), then billing cycle — that hands off via a `Deploy
  Server` button straight into a pre-filled WHMCS cart (`skipconfig=1`,
  skipping the normal upsell/config-options page). This is a real,
  unprompted improvement since the 07-22 baseline, which flagged Lumix as
  having no wizard and no location picker at all — both gaps are now
  closed in a reduced form (2 locations vs. Bisect's 21, no latency
  estimates either way).

### Findings (max 3)

1. **CHANGED — Lumix's location step has gone from "doesn't exist" (07-22)
   to "exists but offers only 2 of Bisect's 21 locations, still with no
   latency/ms data."** This closes half of 07-22's finding 2 outright (a
   picker now exists) but the underlying comparison gap persists in a
   smaller, still-real form: a FiveM/Minecraft community picking a host by
   expected player ping has nothing to go on beyond two US city names on
   either site.
   → *Action:* Original 07-22 recommendation still stands and is now
   easier to scope down: add one static line per location ("Ashburn, VA —
   best for Northeast US, Midwest, Canada, Europe" — this text already
   exists as location-card subtext per today's fetch) directly into the
   picker's visible copy rather than requiring a click to see it, and don't
   treat 2-vs-21 as parity just because a picker UI now exists.

2. **NEW — the "Annually" billing cycle is priced worse than "Semi-Annually"
   on two specific SKUs: Advanced FiveM Server and the Minecraft "Standard"
   plan (marked Most Popular).** Pulled from the live pricing JSON, not
   rendered percentages: Advanced FiveM Server effective rate is
   $25.00/mo at semi-annual, $26.00/mo at annual, back down to $25.00/mo at
   biennial. Minecraft Standard is $26.00/mo semi-annual, $27.00/mo annual,
   $26.00/mo biennial. On both SKUs, a customer committing to a full year
   pays a **worse** rate than one committing to just six months — the
   opposite of every other plan on both pages, which discount monotonically
   with commitment length (confirmed by pulling all 7 tiers on each page).
   This reads as a data-entry error on exactly two "Annually" cells, not a
   pricing strategy — and it's actively discouraging the annual commitments
   that are worth more to Lumix than semi-annual ones.
   → *Action:* Flag to whoever owns the WHMCS product pricing config: fix
   the Annually price on Advanced FiveM Server (pid 22) and Minecraft
   Standard (pid 26) to land around the same ~7% curve as their neighbors
   (roughly $291 and $312 respectively) instead of the current $311.99 /
   $323.99.

3. **NEW/REGRESSION — Lumix's concrete "servers online in under 60 seconds"
   claim (present on the homepage as of 07-22, and the subject of that
   entry's "do this today" recommendation to duplicate it onto checkout)
   has been removed from the site entirely, not relocated.** Direct grep of
   today's homepage and `/games/fivem` raw HTML finds zero instances of
   "second" or "minute" anywhere; the only remaining speed claim is an
   unbacked "Instant setup" bullet with no number. Meanwhile both of this
   week's comparison points state something concrete: BisectHosting's
   checkout says "full access as soon as your payment clears," and
   Shockbyte's own order-flow knowledgebase article states servers are
   "created automatically within 1–2 minutes." Lumix is now the vaguest of
   the three on the one claim shown to matter most at the moment of
   purchase.
   → *Action:* Confirm today's actual average provisioning time with
   whoever owns infra, then either restore a real number to the site (ideally
   nearer the configurator, per 07-22's original recommendation, not just
   the homepage) or drop "Instant setup" if no number can be backed up
   anymore.

### Do this today (<1 hour)
Get the actual current provisioning time from infra (finding 3) — a single
question, no research or design work on the requester's side — so the
vague "Instant setup" bullet can either become a real, checkable number or
get pulled. It's the one action here that doesn't wait on a pricing-config
change (finding 2) or picker-UI work (finding 1).

**Escalation status:** Shockbyte remains blocked to fetch tools for a
fourth straight UX-track attempt (07-22, 08-05, 08-12, 08-19) — worth a
manual (non-automated) check next time it comes up in rotation. Evergreen
discount code (pricing track) is at roughly 30 days per Monday's entry, not
re-checked here. Billing-cycle discount ceiling on Standard FiveM Server
(pricing track, a separate low-ceiling issue from today's finding 2) is at
roughly 16 days, not re-checked here. Bot/Application hosting listing gap
(copy/SEO tracks) is at roughly 22 days, not re-checked here. Homepage meta
description (SEO track) and YouTube 404 (social track) were last verified
08-16 at 24 and 23 days respectively — roughly 27 and 26 days today,
neither re-checked since they're off this track.

---

## 2026-08-20 (Thursday) — SEO & Keywords (Week 6)

**Note:** One week since the 08-13 entry. Pulled raw HTML (title, meta
description, canonical, headings, JSON-LD) for the homepage, `/games/`, and
all five per-game pages; re-fetched `robots.txt` and `sitemap-0.xml`;
re-checked fifteen candidate URLs for bot hosting, VPS, and the four
"Coming Soon" titles (all 404); ran a fresh `site:lumixsolutions.org`
search plus an unbranded long-tail search. Sitemap is unchanged at 18 URLs
since 08-13. This run measured two things this track had never checked
before — on-page heading structure and FiveM framework-level keyword
coverage — and both turned up something new.

### Findings (max 3)

1. **NEW — the FiveM page targets the head term and nothing below it: zero
   mentions of QBCore, ESX, vRP, roleplay, or server.cfg anywhere in the
   markup.** Direct grep of `/games/fivem/` raw HTML: "QBCore" 0, "ESX" 0,
   "vRP" 0, "roleplay" 0, "framework" 0, "Cfx" 0 — "txAdmin" appears exactly
   once. Meanwhile a fresh search for "qbcore server hosting" returns a full
   page of hosts who built content specifically for it: ZAP-Hosting ships a
   "FiveM servers with QBCore framework now available" page, Evolution Host
   runs "FiveM Roleplay Server Hosting — Optimized for QBCore & ESX," and
   Kinetic Hosting has a QBCore setup guide. This matters because nearly
   every serious FiveM buyer is running a roleplay framework — they search
   the framework name, not the generic term, and the generic term
   ("fivem server hosting") is the most contested keyword in the category.
   Lumix's page is competing only where competition is hardest and is absent
   where intent is highest.
   → *Action:* Add one short section to `/games/fivem/` naming the
   frameworks the platform actually supports — e.g. "Runs QBCore, ESX, and
   vRP out of the box, with txAdmin included on every plan" — and work
   "roleplay" into the existing body copy. Pure copy, no new page needed.
   If it draws traffic, a dedicated `/games/fivem/qbcore/` page is the
   natural follow-up.

2. **ESCALATION + NEW DETAIL — the homepage's three primary on-page signals
   are all keyword-thin at once, and Google is still serving the pre-08-02
   title 18 days after it changed.** Three things measured today: (a) the
   meta description is byte-for-byte unchanged at 28 days — still
   "Infrastructure built by engineers. Node.js servers, game services, voice
   infrastructure, and enterprise DDoS protection"; (b) newly measured this
   run, the homepage `<h1>` is "Infrastructure built by engineers" — no
   hosting or game keyword, while every game page has a textbook H1 ("FiveM
   Server Hosting," "Minecraft Server Hosting"); (c) a fresh
   `site:lumixsolutions.org` search still returns the homepage titled
   "Lumix | Lumix Solutions LLC" — the pre-08-02 title — meaning 08-13's
   finding 1 is now 18 days stale and 7 days past the re-index ask, with no
   evidence anyone submitted it. `/games/` and `/games/terraria/` are
   indexed with their correct current titles, so crawling works sitewide;
   it is specifically the homepage that is both unfixed on-page and stale
   in the index.
   → *Action:* Do all three in one pass: paste the already-drafted meta
   description ("FiveM, Minecraft, Terraria, and Discord bot hosting with
   DDoS protection and sub-10ms latency. Deploy in under 60 seconds."),
   change the H1 to lead with what Lumix sells (e.g. "Game server and bot
   hosting, built by engineers" — keeps the existing voice, adds the
   keyword), then submit the homepage for re-indexing in Search Console. If
   no Search Console property exists, say so — this log has assumed passive
   re-crawl for 18 days with no verification it is happening.

3. **ESCALATION — no `Product`/`Offer` structured data on any of the five
   game pages, 21 days unresolved (second escalation).** Confirmed again
   today by parsing JSON-LD on all five: every page ships only the sitewide
   `Organization` and `WebSite` blocks, no `Product`, `Offer`, or
   `priceRange` — despite each page rendering a clear starting price
   ($8.99 FiveM, $14.99 Minecraft, $9.99 Palworld, $5.99 BeamMP, $5.00
   Terraria) and full CPU/RAM/NVMe specs the markup could feed straight
   into an `Offer`. Price-annotated snippets are exactly what wins
   price-led searches like "cheap minecraft server hosting," and Lumix's
   pages remain ineligible for them while holding all the data required.
   → *Action:* Unchanged from 07-30 and 08-06 — one shared template change
   (all five pages use the same layout), not five one-offs.

### Do this today (<1 hour)
Add the framework line to `/games/fivem/` (finding 1): name QBCore, ESX,
vRP, and txAdmin in the page copy and work "roleplay" into the existing
body text. It is the only item on today's board that is genuinely new, has
zero dependencies on anyone else, and targets buyer intent no Lumix page
currently reaches — the homepage fixes in finding 2 have been on this list
for four weeks and need whoever holds CMS access, not another log line.

**Escalation status:** Homepage meta description crosses 28 days (four full
weeks) unresolved today — fourth consecutive weekly escalation on this
track. Stale homepage title in Google's index (first flagged 08-13) crosses
its first 7-day escalation today, folded into finding 2 since both are the
same page. Product/Offer JSON-LD gap crosses 21 days, second escalation.
**Bot/Application hosting SEO footprint is unchanged at 21 days** — the
same six candidate URLs still 404, still absent from the sitemap, and the
only sitewide mention is still the ticker line "Expanded bot hosting
capacity"; not given a finding slot this week because nothing about it has
changed since 08-13, but it remains open in parallel on the copy track. The
four "Coming Soon" titles (ARK: SA, Rust, Arma Reforger, Squad, first
flagged 08-01) still have no stub URLs — all four 404 today, 19 days after
the recommendation to reserve indexing lead time. Off-track items not
re-checked this run: evergreen discount code (pricing track, ~31 days as of
Monday) and the YouTube 404 (social track, ~27 days as of 08-16).

---

## 2026-08-21 (Friday) — Social & Community (Week 5)

**Note:** One week since the 08-14 entry. Re-fetched the homepage footer
(all five social links unchanged), fetched `youtube.com/@officiallumixsolutions`
and `tiktok.com/@lumix.solutions` directly, re-pulled the Discord invite API
(`uaNYBJQtvn`), and searched for any new competitor community content since
last Friday.

### Findings (max 3)

1. **ESCALATION — YouTube footer link hits 28 days (four full weeks)
   unresolved today, the seventh consecutive ask with zero action.** Direct
   fetch of `youtube.com/@officiallumixsolutions` today returns the same
   HTTP 404 confirmed on every check since 07-31. This is now the single
   most-repeated "do this today" item in the entire log — 07-31, 08-07,
   08-14, 08-15, 08-16, and this entry have all asked for the same one-line
   fix (delete the footer link) and none has shipped. The fix requires no
   research, no design decision, and no product/pricing tradeoff — it is
   the lowest-effort open item on the board and also the oldest.
   → *Action:* Stop logging this as a research finding — it's a known,
   confirmed, zero-ambiguity fix that six prior asks haven't moved. Escalate
   directly to whoever holds footer/CMS access as a standing to-do, not
   another recurring line item, until it's actually removed.

2. **NEW — last week's Discord growth ("first real growth in three weeks")
   did not continue; membership is flat and presence is down.** Invite API
   today: 135 members / 14 online, vs. 08-14's 133/19 and 08-16's 132/17.
   Net member change over the full week is +2 (essentially flat after
   08-14's +3 spike), and online presence has dropped roughly 26% from
   08-14's reading. Combined with finding 3 below, there's no evidence any
   community-facing content (contest, repost call, tutorial clip) has
   actually gone out since this track first recommended one on 07-24 —
   four straight Friday entries have proposed community content and none
   has been confirmable from outside Discord.
   → *Action:* Get a direct yes/no on whether the back-to-school contest
   (recommended 07-31, status unconfirmed 08-14) or any other community
   post has shipped. If nothing has gone out in four weeks, the gap isn't
   which idea to run — it's that no one owns posting it. Assign a single
   person to post the standing "share your server clip" call from 07-24's
   original recommendation this week, even without a contest wrapper.

3. **The back-to-school seasonal window flagged 07-31 (Apex's scholarship
   promo, recommended as a scaled-down Lumix contest) has now closed
   unused.** Most US schools are back in session by this date, and no
   confirmation ever surfaced that Lumix's version launched (see finding 2).
   This is the second time-bound recommendation from this track that
   appears to have lapsed without shipping before its relevance window
   closed — the first was the "empty account" fix window this track flagged
   before YouTube went from dormant to a hard 404 between 07-24 and 07-31.
   → *Action:* No recovery action for the missed window itself, but future
   seasonal/timely recommendations from this track should get a specific
   named owner and date at the point they're logged, not an open-ended
   action item — otherwise they'll keep expiring the same way.

### Do this today (<1 hour)
Remove the YouTube icon/link from the site footer (finding 1). Seventh
consecutive ask, zero dependencies, and now the oldest unresolved item of
any kind in this log at 28 days.

**Escalation status:** YouTube 404 (social track) crosses 28 days (four full
weeks) unresolved today, its fifth consecutive Friday-or-off-rotation
escalation. Evergreen discount code (pricing track) was at ~31 days as of
Monday, not re-checked here. Homepage meta description (SEO track) crossed
28 days as of Thursday, not re-checked here since it's off today's track.

---

## 2026-08-22 (Saturday) — Off-Rotation Check-In

**Note:** Ninth unassigned-weekday run (rotation covers Mon–Fri only, cron
fires daily). Re-pulled raw HTML (via direct curl, not the summarizing
fetch tool, to get exact `<title>`/meta bytes and the live pricing JSON) for
the homepage, `/games/fivem`, and `/games/minecraft`; re-fetched
`youtube.com/@officiallumixsolutions` directly; re-pulled the Discord invite
API; and re-checked all four "Coming Soon" slugs for stub pages. Nothing
genuinely new turned up — every open item is exactly where Friday's report
left it, now 1–3 days older. Also re-verified Wednesday's (08-19) two-SKU
annual-pricing bug is still live, with the same numbers.

### Findings (max 3)

1. **Evergreen discount code gap is now 33 days unresolved** (baseline
   07-20, escalated 07-27, flagged for a direct owner decision 08-03, still
   undecided as of Monday's 08-17 entry). Raw HTML confirms today: no code,
   voucher, or sale banner on the homepage or `/games/fivem`. This crosses
   five full weeks unresolved at Monday's next pricing-track re-check
   (08-24) if still unfixed then — no new analysis this run, carrying the
   day count forward.
   → *Action:* Unchanged from every prior entry — get a yes/no from the
   pricing owner. Code name and placement have been proposed since 07-20;
   nothing left to design.

2. **YouTube footer link is still a hard 404, now 29 days unresolved and
   the eighth consecutive ask with zero action.** Direct fetch of
   `youtube.com/@officiallumixsolutions` today returns the same 404
   confirmed on every check since 07-31 (07-31, 08-07, 08-14, 08-15, 08-16,
   08-21, and this one have all asked for the identical one-line footer
   edit). Homepage footer still links to it.
   → *Action:* Same as the last seven runs — remove the YouTube icon/link
   from the site footer. Zero dependencies, zero ambiguity.

3. **Homepage meta description is unchanged, now 30 days unresolved.** Raw
   `<meta name="description">` pull today confirms it is still
   byte-for-byte "Infrastructure built by engineers. Node.js servers, game
   services, voice infrastructure, and enterprise DDoS protection" —
   unchanged since 07-23. The `<title>` tag is also unchanged since 08-02
   ("Game Server & VPS Hosting | Lumix Solutions") — still missing any game
   or "FiveM/Minecraft/Terraria" keyword, and still doesn't match the
   ready-to-paste copy this log has carried since 07-23.
   → *Action:* Unchanged from every prior SEO/copy entry — paste the
   already-drafted meta description onto the homepage. One tag, no design
   work.

### Do this today (<1 hour)
Remove the YouTube icon/link from the site footer (finding 2). Eighth
consecutive ask, zero dependencies, and still the single cheapest fix on
the board relative to how long it's been open.

**Unchanged since Friday (not re-listed as findings):** The FiveM/Minecraft
capacity fix (resolved 08-15) still holds — no "Sold Out" text on either
page's raw HTML. Wednesday's (08-19) two-SKU annual-pricing bug is
re-confirmed present at 3 days old (sub-threshold, not yet escalation-worthy):
Advanced FiveM Server (pid 22) is still $311.99/yr ($26.00/mo) vs.
$149.99/semi-annual ($25.00/mo); Minecraft Standard Plan (pid 26) is still
$323.99/yr ($27.00/mo) vs. $155.99/semi-annual ($25.998/mo) — both annual
rates remain worse than semi-annual, unchanged from Wednesday's numbers.
Discord membership is flat-to-noisy (133 members / 21 online, vs. Friday's
135/14) — no trend either direction. The four "Coming Soon" slugs
(`/games/ark-survival-ascended`, `/rust`, `/arma-reforger`, `/squad`) are
still all 404, now 21 days since first flagged (08-01). Bot/Application
hosting listing gap, billing-cycle discount ceiling, FiveM scarcity claim,
and the Product/Offer JSON-LD gap are all unchanged since their last
check-ins on their respective tracks; not re-verified today since none is
on this off-rotation day's checklist.

---

## 2026-08-23 (Sunday) — Off-Rotation Check-In

**Note:** Tenth unassigned-weekday run (rotation covers Mon–Fri only, cron
fires daily). Re-pulled raw HTML via direct curl for the homepage,
`/games/fivem`, and `/games/minecraft` (including the embedded plan-pricing
JSON, not just visible text); re-fetched `youtube.com/@officiallumixsolutions`
directly; re-pulled the Discord invite API; re-checked all four "Coming
Soon" slugs and four bot-hosting candidate URLs for stub pages; and
re-checked for Product/Offer JSON-LD on the FiveM page. Nothing new
surfaced — every open item is exactly where Saturday's report left it, now
1 day older, with one item crossing a round milestone.

### Findings (max 3)

1. **ESCALATION — YouTube footer link hits 30 days (a full calendar month)
   unresolved today, the ninth consecutive ask with zero action.** Direct
   fetch of `youtube.com/@officiallumixsolutions` today returns the same
   HTTP 404 confirmed on every check since the account went dormant on
   07-24. This is the oldest unresolved item in the entire log and the
   only one that has now stood open for a full month against a fix that
   remains a single footer-link deletion with no dependencies.
   → *Action:* This has passed the point where "log and ask again" is a
   reasonable process — nine identical asks with zero movement means the
   asking mechanism isn't reaching whoever has footer/CMS access. Escalate
   out of band (not just another log line) to get a direct owner and ETA
   this week.

2. **Evergreen discount code gap is now 34 days unresolved**, five full
   weeks as of Monday's next pricing check if still open then. Raw HTML
   today confirms: no code, voucher, or sale banner on the homepage or
   `/games/fivem` (the only related copy on either page is the unrelated
   "Longer terms are a discount, not a lock-in" contract-terms line).
   → *Action:* Unchanged from every prior entry — this needs a yes/no from
   whoever owns pricing, not further research. Code name and placement have
   been proposed since 07-20.

3. **Homepage meta description is unchanged, now 31 days unresolved.** Raw
   `<meta name="description">` pull today is still byte-for-byte
   "Infrastructure built by engineers. Node.js servers, game services,
   voice infrastructure, and enterprise DDoS protection" — unchanged since
   07-23, with no FiveM/Minecraft/Terraria keyword anywhere in it.
   → *Action:* Unchanged from every prior SEO/copy entry — paste the
   already-drafted meta description onto the homepage. One tag, no design
   work.

### Do this today (<1 hour)
Remove the YouTube icon/link from the site footer (finding 1). Ninth
consecutive ask, now open a full month, and still the cheapest fix on the
board relative to how long it has sat unaddressed.

**Unchanged since Saturday (not re-listed as findings):** Wednesday's
(08-19) two-SKU annual-pricing bug is re-confirmed present at 4 days old
(sub-threshold): Advanced FiveM Server (pid 22) pricing JSON today shows
annually $311.99 ($26.00/mo) vs. semiannually $149.99 ($25.00/mo); Standard
Minecraft Plan (pid 26) shows annually $323.99 ($27.00/mo) vs. semiannually
$155.99 ($26.00/mo) — both annual rates still price worse than semiannual.
The Miami/location picker on both FiveM and Minecraft builders still shows
Miami, FL as a selectable, pre-checked region (the ticker-vs-picker
contradiction from 08-15 remains resolved, no regression). Discord invite
API: 137 members / 20 online, in line with the recent flat-to-noisy range.
The four "Coming Soon" slugs (`/games/ark-survival-ascended`, `/rust`,
`/arma-reforger`, `/squad`) are still all 404, now 22 days since first
flagged (08-01). Bot/Application hosting footprint is unchanged: the four
re-checked candidate URLs (`/games/bot-hosting`, `/discord-bot`,
`/python-bot`, `/nodejs-bot`) are all still 404 and absent from the
sitemap. The FiveM page still carries no Product or Offer JSON-LD — only
Organization and WebSite schema are present, same gap flagged on the SEO
track. Billing-cycle discount ceiling and FiveM scarcity claim are
unchanged since their last check-ins on their respective tracks; not
re-verified today since neither is on this off-rotation day's checklist.

---

## 2026-08-24 (Monday) — Competitor Pricing & Plans (Week 6)

**Note:** Re-fetched Lumix's `/games/fivem` and `/games/minecraft` via
direct curl (raw HTML plus the embedded `data-builder-config` pricing
JSON, not just rendered text) to re-verify 08-19's two-SKU annual-discount
bug at the byte level. RocketNode fetched live and directly; BisectHosting
partially (billing-cycle percentages visible, per-tier dollar pricing
gated behind a "Choose a Plan" selector this run). ZAP-Hosting, Shockbyte,
and Apex Hosting all blocked direct fetch again and were re-confirmed via
search instead, consistent with every prior week. No structural change on
the competitor side — same five providers, same tiers, same discount
mechanics as every check since 07-20. The one genuinely new finding this
run came from re-verifying our own site more carefully, not from a
competitor move.

### Findings (max 3)

1. **CHANGED — 08-19's "Annually priced worse than Semi-Annually" bug on
   the Minecraft Standard plan is not a buried JSON quirk, it's a badge
   every visitor sees by default.** Standard Minecraft Plan (pid 26) is
   the page's pre-selected "Most Popular" plan, and its billing-cycle
   selector renders a `Save X%` badge directly under each cycle: Monthly
   Save 0%, Quarterly Save 5%, **Semi-Annually Save 7%, Annually Save
   4%**, before biennial/triennial climb again. That means anyone who
   lands on `/games/minecraft` and does nothing else sees a lower savings
   percentage on the 12-month option than the 6-month one, with no click
   required. The underlying dollar figures are unchanged from 08-19
   ($155.99 semi-annual = $26.00/mo vs. $323.99 annual = $27.00/mo, pid
   26; Advanced FiveM Server pid 22 unchanged too: $149.99 semi-annual vs.
   $311.99 annual), so this isn't a new bug — it's proof the existing one
   is more exposed than logged five days ago.
   → *Action:* Same fix as 08-19 (correct the Annually price on pid 22 and
   pid 26 to land on the same curve as their neighbors, roughly $291 and
   $312), but raise the priority: this isn't a number a customer would
   have to dig for, it's the default view of the site's most-promoted
   plan.

2. **ESCALATION — evergreen discount code gap hits 35 days today, five
   full weeks unresolved with no owner decision ever recorded.** Direct
   fetch of the homepage and `/games/fivem` today: still no code, voucher,
   or sale banner. All five competitors checked this run still run live
   discount mechanisms: ZAP-Hosting's permanent 20%-off voucher
   (`Keishin-a-8710`) reconfirmed; RocketNode's "Summer Sale — Up to 25%
   Off" banner is still live; Shockbyte and Apex both still show active
   promo codes per search (Shockbyte's `SHOCK10`/`LAUNCH`, Apex's
   `APEX25`, both previously confirmed live via direct fetch and
   unchanged since). This is the eleventh-plus consecutive weekly check-in
   logging the identical gap with the identical requested action.
   → *Action:* Unchanged from every prior entry — needs a yes/no from
   whoever owns pricing, not another log line next Monday.

3. **ESCALATION — billing-cycle discount ceiling hits 21 days today**
   (three full weeks; first flagged 08-03, escalated 08-10 and 08-17).
   Re-fetched `/games/fivem` today: still 5% quarterly, 5% semi-annual, 5%
   annual, 10% biennial/triennial, byte-for-byte unchanged. RocketNode
   still offers 20% annual; BisectHosting's billing selector still shows a
   clean, monotonic 10%/15%/20% (quarterly/semi/annual). At the one-year
   commitment point, Lumix still offers 5% against a 20% category norm
   from two separate competitors.
   → *Action:* Same ask as the last two weeks: confirm whether a 20%
   annual discount is a real margin problem or just an unrevisited number.

### Do this today (<1 hour)
Flag finding 1 to whoever owns the WHMCS pricing config, specifically
noting it's not buried data — it's the default badge shown on
`/games/minecraft` to every visitor who changes nothing. It's a one-field
price correction (pid 26's Annually price), and unlike the discount-code
ask (finding 2), it's never been escalated as customer-visible before, so
it hasn't had a fair chance at getting picked up yet.

**Escalation status:** Evergreen discount code (pricing track) crosses 35
days (five full weeks) unresolved today, still the oldest continuously-open
item in the log measured from its 07-20 baseline. Billing-cycle discount
ceiling (pricing track) crosses 21 days (three weeks) today. The two-SKU
annual-pricing bug (pid 22, pid 26; first flagged 08-19) is 5 days old
today — still under this log's 7-day repeat threshold, but see finding 1
for why it's being surfaced again ahead of that mark. Off-track items not
re-checked this run: YouTube 404 (social track) was at 30 days as of
08-23; homepage meta description (SEO/copy track) was at 31 days as of
08-23; bot/application hosting SEO footprint was at ~21 days as of 08-20.

---

## 2026-08-25 (Tuesday) — Website Copy (Week 6)

**Note:** One week since the 08-18 entry. Re-pulled raw HTML via direct
curl (not a summarizing fetch tool) for the homepage, `/games/`, and
`/contact` to check the two 08-11-origin findings byte-for-byte, confirm
whether the Bot Hosting listing gap moved, and look for anything genuinely
new on the pages this track covers. Nothing new turned up — every open
item on this track is exactly where 08-18 left it, one week older, so
today's entry is escalations only, no new findings.

**Confirmed unchanged since 08-18 (verified via raw HTML):** The five
`/games/` product cards (FiveM, Minecraft, Palworld, BeamMP, Terraria) plus
the four Coming Soon teasers (ARK: SA, Rust, Arma Reforger, Squad) are
unchanged — no Bot Hosting card. The CTA-naming split noted 08-18 as
"half-resolved" (only "Contact Sales" remained) has flipped back: today's
fetch shows "Talk to an engineer" live again on `/games/` and "Contact
Sales" live on the homepage — both variants exist simultaneously again,
same underlying inconsistency as 07-28, not worth a separate finding slot
this week since it's a reversion of an already-logged issue, not a new one.

### Findings (max 3) — all escalated (7+ days unresolved)

1. **ESCALATION — the "corporate overhead" claim hits 14 days unresolved
   today, its second escalation.** Raw HTML confirms the homepage "What we
   do" paragraph is still byte-for-byte unchanged: "...reliability without
   the corporate overhead." No list, comparison, or stat anywhere on the
   homepage, `/games/`, or `/contact` defines what this means or what Lumix
   actually cuts that larger hosts don't.
   → *Action:* Unchanged from 08-11/08-18 — replace with a concrete,
   checkable fact (support response time, team size, a specific process
   skipped) instead of the undefined contrast phrase.

2. **ESCALATION — the ticker's "better than ever" claim hits 14 days
   unresolved today, its second escalation, still the same one-line
   zero-dependency edit flagged as "do this today" twice now (08-11,
   08-18).** Raw HTML confirms the exact line is still live: "Production
   and development are better than ever - faster builds, cleaner systems,
   and improved stability." No baseline, no number, still sitting in the
   same ticker rotation as operational claims that are backed by real
   numbers (capacity, stock).
   → *Action:* Unchanged from 08-11/08-18 — attach a real number/date or
   delete the line. Two consecutive "do this today" asks haven't moved it;
   worth a direct nudge rather than a third identical log line next week.

3. **ESCALATION — Bot/Application hosting listing gap hits 28 days
   unresolved (four full weeks), first flagged 07-28, now its fifth
   consecutive copy-track escalation (08-04, 08-06, 08-11, 08-18, and
   this one).** `/games/` re-confirmed today: same five priced product
   cards, no Bot Hosting card, no price, no CTA — the only sitewide
   mentions remain the ticker line ("Expanded bot hosting capacity...")
   and the "Node.js application hosting" phrase in the hero paragraph.
   → *Action:* Unchanged from 08-18 — this needs a recorded yes/no from
   whoever owns the `/games/` catalog on whether the card is blocked or
   simply unscheduled. A month of identical weekly log entries with no
   answer either way is itself the finding at this point.

### Do this today (<1 hour)
Cut or fix the ticker line "Production and development are better than
ever - faster builds, cleaner systems, and improved stability" (finding
2). Same zero-dependency, no-decision-needed edit flagged as today's item
on both 08-11 and 08-18 — the fastest way to clear one of today's three
findings outright, and the one with the least excuse for still being open.

**Escalation status:** Findings 1 and 2 above both cross 14 days (second
escalation) today, first flagged 08-11. Bot/Application hosting listing
gap (finding 3) crosses 28 days, fifth escalation, first flagged 07-28.
Also still open, not re-listed as findings since unchanged and off today's
specific checks: FiveM scarcity claim with no cap number (07-28, ~28 days)
and the CTA-naming inconsistency (07-28, ~28 days, now confirmed reverted
to its original two-variant state per the note above). Off-track items not
re-checked here: evergreen discount code (pricing track) was at 35 days as
of yesterday's Monday entry; homepage meta description and title (SEO
track) were at 31/23 days as of 08-23 — both re-confirmed unchanged as a
side effect of today's homepage fetch (title still "Game Server & VPS
Hosting | Lumix Solutions," meta still "Infrastructure built by
engineers...").

---

## 2026-08-26 (Wednesday) — Competitor UX Deep-Dive: RocketNode (Week 6)

**Note:** Shockbyte was attempted first — `shockbyte.com/hosting/minecraft`
returned HTTP 403 to fetch tools again today, a fifth consecutive blocked
attempt (07-22, 08-05, 08-12, 08-19, and now 08-26). Rotated to RocketNode
instead, the most stale UX-track subject after last week's Bisect revisit
(RocketNode last checked 07-29, 28 days ago, vs. Apex's 21 and ZAP's 14).
Re-fetched RocketNode's FiveM page live, plus raw fetches of Lumix's
`/games/fivem`, `/games/minecraft`, and the billing-portal cart landing
page. Most of RocketNode's own numbers are unchanged since 07-29 (still 6-7
regions, still 20% annual discount, still the 1-Day Free Trial CTA) — the
one genuinely new thing this run surfaced is a product-category change on
RocketNode's page that Lumix's FiveM page has no answer to at all.

### Findings (max 3)

1. **NEW — RocketNode is actively marketing "FiveM Enhanced" support with a
   "NEW!" banner; Lumix's FiveM page has zero mention of it.** FiveM
   Enhanced is Cfx.re's server target for GTA V Enhanced — a genuinely
   different server binary (`cfx-server`, not the Legacy `FXServer`), with
   its own sync model and requirements; it isn't just a marketing label; a
   host has to actually support the new binary. RocketNode presents it as a
   free switch inside the existing plan ("switch the gamemode in the
   startup tab of your Apollo panel"), and three other hosts found via
   search (ServerPrism, CloudNord, Evolution Host, Revive Hosting) all
   market Enhanced support as a named product/checkout option. A direct
   text search of `lumixsolutions.org/games/fivem` today found no mention
   of "Enhanced," "cfx-server," or "GTA V Enhanced" anywhere. For a
   FiveM-focused host, this is a live, currently-relevant technical
   question a prospect or existing customer could reasonably ask in
   Discord this week, and right now Lumix's site gives no answer either
   way.
   → *Action:* Ask infra/panel ownership one question today: does Lumix's
   current FXServer/artifact setup already support switching to the
   Enhanced (`cfx-server`) binary? If yes, add one line to `/games/fivem`
   saying so — a same-day copy fix, no new product needed. If no, that's
   worth flagging as a roadmap gap before more competitors normalize it as
   a standard feature.

2. **ESCALATION — Lumix's location picker is still stuck at 2 regions,
   unfixed since this was first flagged 07-22 (now 35 days, five weeks).**
   RocketNode's FiveM page still lists 6 named regions across three
   continents (Ashburn, Dallas, Salt Lake City, London, Singapore, Sydney);
   Lumix's `/games/fivem` and `/games/minecraft` both still offer exactly
   two (Miami, Ashburn), unchanged since 07-22, 07-29, and 08-19's repeated
   checks of the same gap. 08-19's scoped-down fix (add the existing
   location-card subtext directly into the picker's visible copy) was never
   shipped.
   → *Action:* This is the single oldest continuously-open UX-track finding
   in the log. Needs a decision, not another log line: either commit to
   adding regions (a real infra lift) or at minimum ship 08-19's one-line
   copy fix so the 2-location reality reads as intentional rather than
   unfinished.

3. **ESCALATION — RocketNode's prominent "1 Day Free Trial" CTA next to its
   deploy button is unchanged, and Lumix still has no trial or guarantee
   anywhere in its flow, 28 days since this was first flagged 07-29.**
   Checked homepage, `/games/fivem`, `/games/minecraft`, and the billing
   portal cart landing page today — no trial period, refund window, or
   money-back language on any of them.
   → *Action:* Unchanged from 07-29 — a short trial or a "not satisfied in
   24 hours, full refund" line next to the Deploy Server CTA is a policy
   decision plus one line of copy, not a new product.

### Do this today (<1 hour)
Ask whoever owns the game panel/infra one question: does the current
FXServer setup support switching to FiveM Enhanced's `cfx-server` binary?
It's the one item today that's a single question with no research or
design work on the requester's side, and it's the most time-sensitive of
the three — Enhanced support is actively being marketed as a differentiator
by name right now, not a long-standing gap like findings 2 and 3.

**Escalation status:** Finding 2 (location-picker region count) crosses 35
days today, first flagged 07-22 — now the oldest open item specific to the
UX track. Finding 3 (no free trial/guarantee) crosses 28 days, first
flagged 07-29. Shockbyte remains blocked to fetch tools for a fifth
straight attempt (07-22, 08-05, 08-12, 08-19, 08-26) — still worth a manual
check outside automated tooling next time it comes up. Off-track items not
re-checked today: evergreen discount code and billing-cycle discount
ceiling (pricing track) were at 35 and 21 days as of yesterday; homepage
meta description (SEO/copy track) was at 31 days as of 08-23; bot/
application hosting listing gap (copy track) was at 28 days as of
yesterday.

---

## 2026-08-27 (Thursday) — SEO & Keywords (Week 7)

**Note:** One week since 08-20. Re-pulled raw HTML via direct curl (not a
summarizing fetch tool) for the homepage and `/games/fivem/` — title, meta
description, H1, and JSON-LD `@type` blocks — plus `sitemap-0.xml` (still
18 URLs, byte-identical list to every check since 08-13) and eight
candidate URLs (four bot-hosting slugs, four "Coming Soon" slugs, all still
404). Ran a fresh `site:lumixsolutions.org` search and a "qbcore server
hosting" search to check for movement on competitor framework-targeted
content. Nothing genuinely new turned up this run — every open SEO-track
item is exactly where 08-20 left it, now one week older, with one item
crossing its first escalation threshold. (One data point from the
`site:lumixsolutions.org` search — an AI-generated summary claiming the
homepage advertises "99.9% node uptime," a "100% money-back guarantee," and
"<15 min average first ticket response time" — was checked directly against
the raw homepage HTML and found nowhere in the markup; treating that as a
search-summary hallucination, not a real site change, and not logging it as
a finding.)

### Findings (max 3)

1. **ESCALATION — the FiveM page's framework-keyword gap (08-20's new
   finding) hits 7 days unresolved today, first escalation.** Direct grep
   of `/games/fivem/` raw HTML today: "QBCore" 0, "ESX" 0, "vRP" 0,
   "roleplay" 0, "framework" 0 — identical to 08-20, "txAdmin" still the
   only related term and still appearing exactly once. This was last week's
   "do this today" item (zero dependencies, pure copy) and it didn't ship.
   → *Action:* Unchanged from 08-20 — add one section to `/games/fivem/`
   naming the frameworks Lumix supports (QBCore, ESX, vRP) and working
   "roleplay" into the body copy. Still the single highest-intent keyword
   gap on the page, still a same-day fix.

2. **ESCALATION — homepage title/meta description mismatch is now over a
   month old and the single most repeated ask in this log.** Raw HTML
   confirms today: title is still "Game Server & VPS Hosting | Lumix
   Solutions" (unchanged since 08-02, names no game or "FiveM/Minecraft/
   Terraria"), and the meta description is still byte-for-byte
   "Infrastructure built by engineers. Node.js servers, game services,
   voice infrastructure, and enterprise DDoS protection" — unchanged since
   07-23, now 35 days (five full weeks) with the exact same ready-to-paste
   replacement sitting in this log since day one. This is the seventh
   distinct log entry to flag the meta description specifically (07-23,
   07-26, 07-30, 08-06, 08-13, 08-20, and this one).
   → *Action:* Same two-line copy-paste as every prior entry — title →
   "Lumix Solutions | FiveM, Minecraft, Terraria & Bot Hosting"; meta →
   "FiveM, Minecraft, Terraria, and Discord bot hosting with DDoS
   protection and sub-10ms latency. Deploy in under 60 seconds." At 35 days
   with zero movement despite being logged as a one-line fix seven times,
   this needs a direct answer from whoever holds CMS access on whether
   there's a blocker (a CMS constraint, a branding decision) that hasn't
   surfaced yet — not an eighth identical log line next Thursday.

3. **ESCALATION — no `Product`/`Offer` JSON-LD on the FiveM page, now 28
   days unresolved (fourth escalation).** Confirmed again today: `/games/
   fivem/` ships only `Organization` and `WebSite` `@type` blocks, no
   `Product` or `Offer`, despite the page rendering a clear $8.99 starting
   price and full spec table. First flagged 07-30, escalated 08-06, 08-13,
   and 08-20; unchanged at each check.
   → *Action:* Unchanged from every prior entry — one shared template
   change across all five game pages (they share a layout), pulling the
   price already rendered on each page into an `Offer` block.

### Do this today (<1 hour)
Add the QBCore/ESX/vRP framework line to `/games/fivem/` (finding 1). It's
the only item today that isn't already a month-plus-old stuck item needing
an out-of-band owner decision — pure copy, zero dependencies, and it was
already asked for once with no result, so shipping it this week stops it
from becoming this track's next "seventh ask" item like finding 2.

**Escalation status:** Finding 2 (homepage title/meta) crosses 35 days
(five weeks) today on the meta description specifically, its fourth
distinct escalation mention; the title mismatch (since 08-02) is 25 days.
Finding 3 (Product/Offer JSON-LD) crosses 28 days today, fourth escalation.
Finding 1 (FiveM framework keywords) crosses its first 7-day threshold
today. Off-track items not re-checked this run: evergreen discount code and
billing-cycle discount ceiling (pricing track) were at 35 and 21 days as of
08-24; corporate-overhead and better-than-ever ticker claims plus the
bot/application hosting listing gap (copy track) were at 14/14/28 days as
of 08-25; location-picker region count and no-trial gap (UX track) were at
35/28 days as of yesterday; YouTube 404 and Discord growth (social track)
were last checked 08-21.

---

## 2026-08-28 (Friday) — Social & Community (Week 6)

**Note:** One week since 08-21. Re-fetched the homepage footer directly
(`curl`, not a summarizing fetch tool) to confirm all five social hrefs,
fetched `youtube.com/@officiallumixsolutions` directly, re-pulled the
Discord invite API (`uaNYBJQtvn`), and searched fresh for any new
BisectHosting/Shockbyte/RocketNode social content and for the outcome of
Apex's Minecraft Scholarship (flagged 07-31 as a seasonal content format
Lumix has no equivalent of). Nothing new turned up on the competitor side
this run; the two developments worth logging are both on Lumix's own side.

### Findings (max 2)

1. **ESCALATION — YouTube footer link hits 35 days (five full weeks)
   unresolved today, the tenth consecutive ask with zero action.** Direct
   fetch of `youtube.com/@officiallumixsolutions` today returns the same
   HTTP 404 confirmed on every check since 07-31 (07-31, 08-07, 08-14,
   08-15, 08-16, 08-21, 08-22, 08-23, and this one). The homepage footer's
   raw HTML still links to it, confirmed again via direct `curl` this run.
   This is now the single oldest, most-repeated, lowest-effort open item in
   the entire log — a one-line footer deletion that outlasted every other
   track's findings, including items that need a pricing or infra decision.
   → *Action:* This has already crossed the point (flagged 08-23) where
   another log line stops being useful. Whoever has footer/CMS access needs
   this as a direct, named to-do with an ETA — not an eleventh identical
   Friday entry.

2. **CHANGED — Discord membership resumed real growth this week after
   08-21's "flat" reading, but there's still no confirmation any planned
   community content has ever shipped.** Invite API today: 141 members / 22
   online, up from 08-21's 135/14 (+6 members, +4.4%, the strongest
   week-over-week gain since 08-14's since-stalled +3 spike). That's a
   genuine positive data point, not noise. But it arrives with no visible
   cause: the site's public footer, Discord invite description, and search
   results show no evidence of the "share your server clip" call (first
   recommended 07-24) or any other community post going out — the same gap
   08-21's finding 2 flagged, now five weeks old with the growth trend
   turning up despite it, not because of it.
   → *Action:* Get a direct yes/no on whether anyone posted the standing
   community-clips call this week. If this growth happened with zero
   deliberate content, that's a case for how much upside is being left on
   the table by not shipping the recommendation — worth surfacing as-is
   rather than re-proposing the same idea an eleventh time.

### Do this today (<1 hour)
Remove the YouTube icon/link from the site footer (finding 1). Tenth
consecutive ask, still zero dependencies, and now the single most overdue
item of any kind in this log at 35 days.

**Escalation status:** YouTube 404 (social track) crosses 35 days (five
full weeks) unresolved today, its sixth consecutive Friday-or-off-rotation
escalation since 07-31. Evergreen discount code (pricing track) was at 35
days as of Monday's 08-24 entry, not re-checked here. Homepage meta
description (SEO track) was at 35 days as of yesterday's 08-27 entry, not
re-checked here since it's off today's track.

---

## 2026-08-29 (Saturday) — Off-Rotation Check-In

**Note:** Re-pulled raw HTML via direct `curl` (not a summarizing fetch
tool) for the homepage, `/games/fivem`, `/games/minecraft`, and `/games/`
(including the embedded pricing JSON on the two game-builder pages, not
just rendered text); checked `youtube.com/@officiallumixsolutions`
directly; and re-pulled the Discord invite API. Nothing genuinely new
turned up — every open item is exactly where Friday's report left it, one
day older — except one item that quietly crossed this log's own 7-day
repeat threshold for the first time today.

### Findings (max 3)

1. **ESCALATION — the two-SKU annual-pricing bug (Advanced FiveM Server,
   Standard Minecraft Plan) crosses 7 days unresolved today, its first
   formal escalation.** First flagged 08-19, called out again 08-24 as
   "customer-visible by default" (both SKUs are the pre-selected "Most
   Popular" plan on their respective pages) but still logged as
   sub-threshold at the time (5 days). Today's raw pricing-JSON pull
   confirms both are still unchanged at the byte level: Advanced FiveM
   Server (pid 22) — semiannually $149.99 ($25.00/mo) vs. annually $311.99
   ($26.00/mo); Standard Minecraft Plan (pid 26) — semiannually $155.99
   ($26.00/mo) vs. annually $323.99 ($27.00/mo). Ten days since first
   flagged with zero movement, and it's now old enough that it stops being
   "a bug that hasn't been looked at yet" and starts being a recurring
   log item like the rest of this list.
   → *Action:* Same fix as 08-19/08-24 — correct the Annually price on pid
   22 and pid 26 so it lands on the same discount curve as their
   neighboring cycles (roughly $291 and $312 respectively). One-field
   pricing-config correction on both SKUs.

2. **ESCALATION — YouTube footer link hits 36 days unresolved today, the
   eleventh consecutive ask with zero action.** Direct fetch of
   `youtube.com/@officiallumixsolutions` today returns the same HTTP 404
   confirmed on every check since 07-31, and the homepage footer's raw
   HTML still links to it. This remains the single oldest, most-repeated,
   lowest-effort open item in the entire log.
   → *Action:* Unchanged from every prior ask — this needs a named owner
   and ETA, not a twelfth identical log line next week.

3. **Evergreen discount code gap is now 40 days unresolved.** Raw HTML of
   the homepage and `/games/fivem` today: still no code, voucher, or sale
   banner anywhere on either page — same as every check since the 07-20
   baseline. This is the single oldest continuously-open item in the log
   measured from its origin date, even though YouTube's finding above has
   more consecutive weekly mentions.
   → *Action:* Unchanged from every prior entry — needs a yes/no from
   whoever owns pricing, not further research.

### Do this today (<1 hour)
Remove the YouTube icon/link from the site footer (finding 2). Eleventh
consecutive ask, zero dependencies, and still the cheapest fix on the
board relative to how long it has sat unaddressed.

**Unchanged since Friday (not re-listed as findings):** Homepage `<title>`
("Game Server & VPS Hosting | Lumix Solutions") and meta description
("Infrastructure built by engineers...") are both re-confirmed unchanged
today (meta description now 37 days unresolved, not re-listed as a
standalone finding since it's off today's specific pricing/social checks
and was already the headline of Thursday's 08-27 SEO entry). The
"corporate overhead" and ticker "better than ever" claims (copy track,
14+ days) are both still live verbatim. `/games/fivem` still has zero
"QBCore"/"ESX"/"roleplay" mentions (SEO track, 2 days into its first
escalation window). `/games/` still shows no Bot Hosting product card; the
four "Coming Soon" slugs (`/games/ark-survival-ascended`, `/rust`,
`/arma-reforger`, `/squad`) are all still 404. `/games/fivem` still ships
only `Organization`/`WebSite` JSON-LD, no `Product`/`Offer` block. Discord
invite API: 140 members / 26 online, essentially flat against yesterday's
141/22 (-1 member, +4 online) — noise, not a trend change.

---

## 2026-08-30 (Sunday) — Off-Rotation Check-In

**Note:** Fifth unassigned-weekday run (rotation covers Mon–Fri only, cron
fires daily). Re-pulled raw HTML via direct `curl` (not a summarizing fetch
tool) for the homepage, `/games/`, `/games/fivem`, and `/games/minecraft`
(including the embedded pricing JSON on the two game-builder pages),
checked `youtube.com/@officiallumixsolutions` directly, and re-pulled the
Discord invite API. One small, genuinely new site change turned up (noted
below, not counted as a finding since it needs no action); every other open
item is exactly where yesterday's report left it, one day older.

**NEW, not a finding:** The four "Coming Soon" game cards on `/games/`
(ARK: Survival Ascended, Rust, Arma Reforger, Squad) now carry a "Get
notified" CTA that links straight to the Discord invite, instead of being
inert teaser tiles. The underlying `/games/<slug>` URLs (checked again
today: `ark-survival-ascended`, `rust`, `arma-reforger`, `squad`) still all
404, so this doesn't touch 08-01's SEO-stub recommendation, but it closes a
smaller gap that was never explicitly logged — a prospect clicking a
Coming Soon tile now lands somewhere useful instead of nowhere.

### Findings (max 3)

1. **ESCALATION — the two-SKU annual-pricing bug (Advanced FiveM Server,
   Standard Minecraft Plan) is now 11 days unresolved.** Today's raw
   pricing-JSON pull confirms both are still byte-identical to every prior
   check: Advanced FiveM Server (pid 22) — semiannually $149.99 ($25.00/mo)
   vs. annually $311.99 ($26.00/mo); Standard Minecraft Plan (pid 26) —
   semiannually $155.99 ($26.00/mo) vs. annually $323.99 ($27.00/mo). Both
   remain the pre-selected "Most Popular" plan on their respective pages,
   so this is still the default view, not a buried number.
   → *Action:* Unchanged from 08-19/08-24/08-29 — correct the Annually
   price on pid 22 and pid 26 to land on the same discount curve as their
   neighboring cycles (roughly $291 and $312 respectively). One-field
   pricing-config correction on both SKUs.

2. **YouTube footer link hits 37 days unresolved today, the twelfth
   consecutive ask with zero action.** Direct fetch of
   `youtube.com/@officiallumixsolutions` today returns the same HTTP 404
   confirmed on every check since 07-31, and the homepage footer's raw HTML
   still links to it.
   → *Action:* Unchanged from every prior ask — remove the footer link or
   fix the handle; this needs a named owner and ETA, not a thirteenth
   identical log line next week.

3. **Evergreen discount code gap is now 41 days unresolved.** Raw HTML of
   the homepage and `/games/fivem` today: still no code, voucher, or sale
   banner anywhere on either page — same as every check since the 07-20
   baseline.
   → *Action:* Unchanged from every prior entry — needs a yes/no from
   whoever owns pricing, not further research.

### Do this today (<1 hour)
Fix the two-SKU annual-pricing bug (finding 1). Unlike the YouTube link and
discount code — both of which need an owner decision before anything ships
— this is a pure data-entry correction on two pricing-config fields, it's
customer-visible on both pages' default "Most Popular" plan, and it's the
newest of the three findings, so it hasn't had the same number of ignored
asks yet.

**Unchanged since yesterday (not re-listed as findings):** Homepage
`<title>` ("Game Server & VPS Hosting | Lumix Solutions") and meta
description ("Infrastructure built by engineers...") both re-confirmed
unchanged today (meta description now 38 days unresolved). Billing-cycle
discount ceiling (pricing track, first flagged 08-03) is 27 days unresolved
— re-checked today via `/games/fivem`'s Save% badges (still 5%/5%/5%
quarterly/semi/annual, 10% biennial/triennial), byte-identical to every
prior check. `/games/fivem` still has zero "QBCore"/"ESX"/"vRP"/"roleplay"
mentions and ships only `Organization`/`WebSite` JSON-LD (no `Product`/
`Offer` block). `/games/` still shows no Bot Hosting product card. Location
picker on `/games/fivem` still lists exactly two regions (Miami, Ashburn).
No free trial or money-back guarantee appears anywhere in the flow. Discord
invite API: 141 members / 28 online, up slightly from yesterday's 140/26
(+1 member, +2 online) — noise, not a trend change.

---

## 2026-08-31 (Monday) — Competitor Pricing & Plans (Week 7)

**Note:** Re-fetched Lumix's `/games/fivem` and `/games/minecraft` via direct
`curl` (raw HTML plus the embedded `data-builder-config` pricing JSON) to
re-verify all three open pricing-track items at the byte level. Ran a fresh
competitor check across all five providers (BisectHosting, Shockbyte, Apex
Hosting, ZAP-Hosting, RocketNode) looking specifically for anything new
since 08-24 — a seasonal promo swap in particular, since US Labor Day
(Sept 7) is now one week out. Nothing new turned up: no competitor has
launched a Labor Day/back-to-school promo yet (RocketNode's "Summer Sale —
Up to 25% Off" banner and 1-Day Free Trial CTA are both still running
unchanged; Bisect's 10%/15%/20% ladder, Shockbyte's `SHOCK10`, Apex's
`APEX25`, and ZAP's permanent voucher mechanic are all unchanged per search).
One low-confidence data point — a general fetch of ZAP-Hosting's site
surfaced a FiveM entry price of $9.24/mo vs. the $8.57 baseline — is not
solid enough to log as a finding (could be a different plan/region being
surfaced, not a real repricing) but is worth a manual spot-check next time
ZAP comes up. All three findings below are escalations of already-open
items, all still exactly where 08-24 left them at the byte level.

### Findings (max 3)

1. **ESCALATION — the two-SKU annual-pricing bug (Advanced FiveM Server,
   Standard Minecraft Plan) is now 12 days unresolved.** Today's raw
   pricing-JSON pull confirms both are still byte-identical to every prior
   check since 08-19: Advanced FiveM Server (pid 22) — semiannually $149.99
   ($25.00/mo) vs. annually $311.99 ($26.00/mo); Standard Minecraft Plan
   (pid 26) — semiannually $155.99 ($26.00/mo) vs. annually $323.99
   ($27.00/mo). Both remain the pre-selected "Most Popular" plan on their
   respective pages (`data-pid="22"`/`data-pid="26"` confirmed inside the
   ribboned card again today), so this is still the default view every
   visitor sees, not a buried number.
   → *Action:* Unchanged from 08-19/08-24/08-29/08-30 — correct the Annually
   price on pid 22 and pid 26 to land on the same discount curve as their
   neighboring cycles (roughly $291 and $312 respectively). One-field
   pricing-config correction on both SKUs.

2. **ESCALATION — evergreen discount code gap hits 42 days today, six full
   weeks unresolved with no owner decision ever recorded.** Direct fetch of
   the homepage, `/games/fivem`, and `/games/minecraft` today: still no
   code, voucher, or sale banner anywhere (grepped for "promo," "coupon,"
   "discount code," "voucher," "% off" across all three pages — zero hits).
   All five competitors checked this run still run live discount mechanisms,
   unchanged from every prior week's snapshot.
   → *Action:* Unchanged from every prior entry — needs a yes/no from
   whoever owns pricing, not another log line next Monday.

3. **ESCALATION — billing-cycle discount ceiling hits 28 days today** (four
   full weeks; first flagged 08-03, escalated 08-10, 08-17, 08-24). Re-fetched
   `/games/fivem` today: Save-badge counts still 5%/5%/5% (quarterly/semi/
   annual, three "Save 5%" badges) and 10%/10% (biennial/triennial),
   byte-for-byte unchanged. RocketNode confirmed today at 5% quarterly / 12%
   semi-annual / 20% annual; BisectHosting confirmed today at a clean
   10%/15%/20% ladder. At the one-year commitment point, Lumix still offers
   5% against a 20% category norm from two separate competitors.
   → *Action:* Same ask as the last three weeks: confirm whether a 20%
   annual discount is a real margin problem or just an unrevisited number.

### Do this today (<1 hour)
Fix the two-SKU annual-pricing bug (finding 1). It's the newest of the three
open pricing items, it's a pure one-field data correction on each SKU (no
policy decision needed like findings 2 and 3), and it's customer-visible by
default on both pages' pre-selected "Most Popular" plan.

**Escalation status:** Evergreen discount code (finding 2) crosses 42 days
(six full weeks) today, still the oldest continuously-open item in the log
measured from its 07-20 baseline. Billing-cycle discount ceiling (finding 3)
crosses 28 days (four weeks) today. The two-SKU annual-pricing bug (finding
1) crosses 12 days today, its second consecutive weekly mention since
08-29's first escalation. Off-track items not re-checked this run: YouTube
404 (social track) was at 37 days as of 08-30; homepage title/meta
description (SEO track) was at 38 days as of 08-30; FiveM framework-keyword
gap (SEO track) was at 4 days into its first escalation window as of 08-27;
corporate-overhead and better-than-ever ticker claims plus bot/application
hosting listing gap (copy track) were at 14/14/28 days as of 08-25;
location-picker region count and no-trial gap (UX track) were at 35/28 days
as of 08-26.

---

## 2026-09-01 (Tuesday) — Website Copy (Week 7)

**Note:** One week since 08-25. Re-pulled raw HTML via direct `curl` (not a
summarizing fetch tool) for the homepage, `/games/`, `/spotlight/`,
`/partners/`, and `/contact/`. All three of 08-25's open items (corporate
overhead phrase, ticker "better than ever" line, Bot/Application hosting
listing gap) are confirmed byte-for-byte unchanged. The CTA-naming split
is also unchanged from 08-25's reverted state ("Contact Sales" on the
homepage, "Talk to an engineer" on `/games/`). One genuinely new item
turned up this run, on a page not scrutinized line-by-line before.

### Findings (max 3)

1. **NEW — `/games/` has a decorative "system status" readout that omits
   Terraria, a real, purchasable product listed right below it.** The
   `lumix catalog --available` terminal block lists exactly four rows —
   `fivem`, `minecraft`, `palworld`, `beammp`, each "ONLINE / ACCEPTING" —
   then the page's own live "5 live / 9 total" catalog directly underneath
   lists five purchasable games including Terraria at $5.00/mo with a
   working "Configure" CTA. This is the inverse of the scarcity-claim
   problem already on this log (07-28): instead of an unproven claim, it's
   a proof/trust element (a fake-terminal "status" readout meant to signal
   real infrastructure) that's simply wrong — a prospect who reads the
   status table before the catalog would conclude Terraria hosting doesn't
   exist or isn't accepting signups, one scroll before the page proves
   otherwise.
   → *Action:* Add a `terraria ONLINE ACCEPTING` row to the status block
   template on `/games/` so it matches the five live catalog entries.
   One line in a shared template, no design or pricing decision needed.

2. **ESCALATION — the ticker's "better than ever" claim hits 21 days
   unresolved today, its third escalation, and the third consecutive
   "do this today" ask (08-11, 08-18, 08-25) with zero movement.** Raw
   HTML confirms the exact line is still live on the homepage, `/games/`,
   `/spotlight/`, `/partners/`, and `/contact/`: "Production and
   development are better than ever - faster builds, cleaner systems, and
   improved stability." Still no baseline, number, or date attached.
   → *Action:* Unchanged from every prior entry — attach a real number/date
   or delete the line. Three identical "do this today" asks haven't moved
   it; worth a direct nudge to whoever owns the ticker content rather than
   a fourth ask next Tuesday.

3. **ESCALATION — Bot/Application hosting listing gap hits 35 days
   unresolved (five full weeks), first flagged 07-28, now its sixth
   consecutive copy-track escalation.** `/games/` re-confirmed today: still
   the same five priced product cards (plus four Coming Soon teasers), no
   Bot Hosting card, no price, no CTA. The only sitewide mentions remain
   the ticker line ("Expanded bot hosting capacity...") and "Node.js
   application hosting" in the homepage hero paragraph.
   → *Action:* Unchanged from every prior entry — this needs a recorded
   yes/no from whoever owns the `/games/` catalog on whether the card is
   blocked or simply unscheduled. Six identical weekly log entries with no
   answer either way is itself the finding at this point.

### Do this today (<1 hour)
Add the missing `terraria ONLINE ACCEPTING` row to the `/games/` status
readout (finding 1). It's the newest item on the board, hasn't had a
single ignored ask yet (unlike findings 2 and 3), and is a pure one-line
template fix with no pricing or scheduling decision behind it — the
highest-leverage fix available today.

**Escalation status:** Finding 2 (ticker "better than ever") crosses 21
days today, third escalation, first flagged 08-11. Finding 3 (Bot/
Application hosting listing gap) crosses 35 days today, sixth escalation,
first flagged 07-28. Also still open, not re-listed as findings since
unchanged and this week's slots went to a new item: the "corporate
overhead" phrase (08-11 origin, 21 days, same status as finding 2), the
FiveM scarcity claim with no cap number (07-28, ~35 days), and the
CTA-naming inconsistency (07-28, ~35 days, confirmed still in its
reverted two-variant state). Off-track items not re-checked this run
beyond what a homepage/`/games/` fetch surfaced incidentally: homepage
title ("Game Server & VPS Hosting | Lumix Solutions") and meta description
("Infrastructure built by engineers...") both directly re-confirmed
unchanged today via this run's own fetch — SEO track, ~39/40 days per
08-30's count. Evergreen discount code, two-SKU annual-pricing bug, and
billing-cycle discount ceiling (pricing track) were at 42/12/28 days as of
08-31. Location-picker region count and no-trial gap (UX track) were at
35/28 days as of 08-26. YouTube 404 and Discord growth (social track) were
last checked 08-30 (141/28 members/online).

---

## 2026-09-02 (Wednesday) — Competitor UX Deep-Dive: Apex Hosting (Week 2)

**Note:** Second Apex entry (first was 08-05, method-limited to search/review
sources since Apex's own pages 403 fetch tools — same block hit again today
across `apexminecrafthosting.com/`, `/order`, `/games/minecraft-server-hosting/`,
and `billing.apexminecrafthosting.com`, so today's Apex data is again
reconstructed from independent review sites, not a live render). Lumix's
`/games/fivem` and `/games/minecraft` were fetched live via direct `curl`
for the comparison side. **One genuine improvement turned up first:** Miami,
FL is no longer marked "Sold Out" on either Lumix builder — it's now a
selectable, pre-checked default location with the same descriptive-note
treatment as Ashburn ("Best for the Southeast US, Caribbean, and Latin
America"). This resolves the dead-looking-option half of 07-29's finding
(the specific "sold out card next to a live one" symptom); it does not
resolve the underlying 2-locations-vs-"12 PoPs" gap, which this run's
Apex comparison sharpens rather than closes (see finding 2).

### Findings (max 3)

1. **NEW — Apex puts modpack/version selection inside the purchase flow
   itself; Lumix's wizard has no equivalent step, pushing that choice to
   after checkout.** Per independent reviews of Apex's order flow: step 2
   ("configure your version — Java or Bedrock, vanilla or a specific
   modpack") is where a buyer picks from a "one-click installer for over
   200+ modpacks" (e.g. SkyFactory, All the Mods) before payment — the
   server that comes out the other end is already running the requested
   modpack. Lumix's `/games/minecraft` builder (re-confirmed today via raw
   HTML) is a 3-step wizard — Plan → Location → Billing cycle — with no
   version or modpack step anywhere; the page's own copy places that
   entirely post-purchase: "Modpack and plugin installs from the panel."
   A Lumix buyer finishes checkout with a blank server and still has to
   go configure it themselves; an Apex buyer's server is already the
   modpack they asked for.
   → *Action:* Add a lightweight 4th wizard step (or a sub-choice inside
   the existing Plan step) — "Java or Bedrock" plus a short list of
   common modpacks/loaders (Vanilla, Paper, Forge, Fabric) — that gets
   passed to provisioning, so at least the base server type is right at
   first boot instead of requiring a panel trip immediately after
   purchase.

2. **ESCALATION — the 2-location wizard vs. "12 PoPs" homepage claim hits
   42 days unresolved today, and this run completes a second full lap of
   the competitor rotation with the same gap confirmed against all four
   (Bisect 07-22/08-19, RocketNode 07-29/08-26, Apex 08-05/today, ZAP
   08-12) — six consecutive Wednesday UX reviews, zero movement.** Today's
   Apex figure is unchanged from 08-05's confirmed count: 18 real
   datacenters across 6 continents (US x6, Canada, Brazil, UK, France,
   Poland, Germany, Israel, Russia, China, Singapore, Australia, Turkey).
   Lumix's `/games/fivem` and `/games/minecraft` (re-fetched live today)
   both still list exactly two: Miami and Ashburn. The homepage/`/games`
   stats block still reads "12 PoPs Locations," unchanged.
   → *Action:* This has now outlasted a full rotation of this routine's own
   comparison set — worth treating as a standing decision request rather
   than a recurring finding: either commit an infra timeline for opening
   more of the claimed 12 PoPs, or change the homepage stat to something
   accurate today (e.g. "2 Locations — more rolling out") until it does.

3. **ESCALATION — the FiveM Enhanced (`cfx-server`) support question first
   asked 08-26 crosses 7 days unresolved today, its first escalation.**
   `/games/fivem` (re-checked today via direct text search of the raw
   HTML) still has zero mentions of "Enhanced," "cfx-server," or "GTA V
   Enhanced." This was last week's zero-dependency "do this today" item
   (a single yes/no question to infra/panel ownership, no research or
   design work needed) and it didn't get answered.
   → *Action:* Unchanged from 08-26 — get a yes/no from whoever owns the
   game panel on whether the current FXServer/artifact setup supports
   switching to the Enhanced binary, then add one line to `/games/fivem`
   either way (support confirmed, or "Enhanced support coming soon").

### Do this today (<1 hour)
Get the FiveM Enhanced yes/no answer (finding 3). It's the only one of the
three with zero research, design, or infra-timeline decision attached —
just a question that's been sitting unanswered for a full week.

**Escalation status:** Finding 2 (2-location wizard vs. "12 PoPs" claim)
crosses 42 days today, its most-repeated UX-track finding — sixth
consecutive weekly mention across all four rotation competitors. Finding 3
(FiveM Enhanced) crosses its first 7-day threshold today. Not re-listed as
a full finding but still open: no free trial or money-back guarantee
anywhere in Lumix's flow (07-29 origin, 35 days) — Apex's own risk-reversal
mechanism is a 7-day money-back guarantee rather than RocketNode's 1-day
trial, a second distinct pattern (trial vs. guarantee) neither of which
Lumix offers either version of; this is the same underlying gap already
covered in depth on 08-05 and 08-26, not re-analyzed today to avoid a
fourth near-identical writeup. Off-track items incidentally re-confirmed
today via this run's own fetch, not re-listed as findings since off-track:
homepage title/meta description (SEO/copy track) unchanged — still "Game
Server & VPS Hosting | Lumix Solutions" / "Infrastructure built by
engineers..."; two-SKU annual-pricing bug (pid 22, pid 26 — pricing track)
unchanged at the byte level; billing-cycle discount ladder (pricing track)
unchanged at 5%/5%/5%/10%/10%; no promo/coupon/discount code anywhere on
homepage, `/games/fivem`, or `/games/minecraft` (pricing track); `/games/`
status readout still omits Terraria despite it being a live catalog entry
(copy track, flagged yesterday 09-01, 1 day old — too new to escalate).
Social-track items (YouTube 404, Discord count) not re-checked this run;
last confirmed 08-30 (141/28 members/online).

---

## 2026-09-03 (Thursday) — SEO & Keywords (Week 8)

**Note:** One week since 08-27. Re-pulled raw HTML via direct curl for the
homepage and `/games/fivem/` (title, meta description, JSON-LD `@type`
blocks, keyword grep), plus `sitemap-0.xml`/`sitemap-index.xml`/`robots.txt`
(18 URLs, byte-identical list since 08-13; robots.txt allows full crawl;
`/games/fivem/` carries `<meta name="robots" content="index, follow">` and
a correct self-referencing canonical — ruling out a technical indexing
block). Ran fresh unbranded searches ("fivem server hosting," "cheap
minecraft server hosting," "discord bot hosting node.js python cheap") and
three `site:lumixsolutions.org` searches (bare, `+fivem`, `+minecraft`).
Nothing genuinely new this run — every open SEO-track item is exactly where
08-27 left it, one week older. One data point worth noting but not logging
as its own finding: the site-restricted searches for `+fivem` and
`+minecraft` return no `/games/fivem/` or `/games/minecraft/` result at all
(Wikipedia camera pages and the billing portal fill the results instead),
while a bare `site:lumixsolutions.org` search does surface `/games/`,
`/games/terraria/`, `/staff/`, and `/partners/`. With robots/canonical
confirmed clean, this reads as a symptom of the already-logged root causes
(generic title/meta, no page-level schema) rather than a new distinct
problem, so it's folded into findings 1-2 below instead of counted
separately. Also re-confirmed: the AI search-summary hallucination first
caught 08-27 (claiming "99.9% node uptime," "100% money-back guarantee,"
"<15 min average first ticket response") still doesn't match the raw
homepage HTML on any of the three phrases — same non-issue, not re-logged.

### Findings (max 3)

1. **ESCALATION — the FiveM page's framework-keyword gap crosses 14 days
   unresolved today, second escalation.** Direct grep of `/games/fivem/`
   raw HTML: "QBCore" 0, "ESX" 0, "vRP" 0, "roleplay" 0, "framework" 0,
   identical to both 08-20 and 08-27 — "txAdmin" still the only related
   term, still appearing exactly once. This is the second week running
   as the "do this today" item with no ship.
   → *Action:* Unchanged — add one section to `/games/fivem/` naming the
   supported frameworks (QBCore, ESX, vRP) and working "roleplay" into
   body copy. Still a same-day, zero-dependency fix; likely also the
   reason `/games/fivem/` doesn't surface for its own site-restricted
   search (see note above) alongside finding 2.

2. **ESCALATION — homepage title/meta description mismatch is now 42 days
   old on the meta description and 32 days on the title; this is the
   eighth distinct log entry to flag it (07-23, 07-26, 07-30, 08-06,
   08-13, 08-20, 08-27, and today).** Raw HTML confirms both are still
   byte-identical to every prior check: title "Game Server & VPS Hosting |
   Lumix Solutions" (no game name), meta "Infrastructure built by
   engineers. Node.js servers, game services, voice infrastructure, and
   enterprise DDoS protection" (no product terms, no CTA). Per 08-27's own
   note, this shouldn't be a ninth identical log line next Thursday.
   → *Action:* The copy-paste fix has been sitting ready for seven weeks
   (title → "Lumix Solutions | FiveM, Minecraft, Terraria & Bot Hosting";
   meta → "FiveM, Minecraft, Terraria, and Discord bot hosting with DDoS
   protection and sub-10ms latency. Deploy in under 60 seconds."). This
   log will stop re-proposing the copy and instead flag the process gap
   directly: get one explicit answer from whoever holds CMS access — yes,
   no, or blocked-by-X — logged here, so next week either closes this or
   records a real reason instead of a ninth "unchanged."

3. **ESCALATION — no `Product`/`Offer` JSON-LD on `/games/fivem/`, now 35
   days unresolved, fifth escalation.** Confirmed again today: the page
   ships only `Organization` and `WebSite` `@type` blocks despite
   rendering a clear $8.99 starting price and full spec table. First
   flagged 07-30, escalated 08-06, 08-13, 08-20, 08-27, unchanged at every
   check since.
   → *Action:* Unchanged — one shared template change across the five game
   pages (they share a layout), pulling each page's already-rendered price
   into an `Offer` block.

### Do this today (<1 hour)
Add the QBCore/ESX/vRP/roleplay line to `/games/fivem/` (finding 1). Same
zero-dependency copy fix asked for two weeks running — the only item today
that doesn't require an out-of-band owner decision first.

**Escalation status:** Finding 2 (homepage title/meta) crosses 42 days
(meta) / 32 days (title) today, its eighth distinct mention. Finding 3
(Product/Offer JSON-LD) crosses 35 days today, fifth escalation. Finding 1
(FiveM framework keywords) crosses 14 days today, second escalation.
Off-track items not re-checked this run: evergreen discount code and
billing-cycle ceiling (pricing track) were at 42/28 days as of 08-31;
corporate-overhead/ticker claims and bot-hosting listing gap (copy track)
were at 21/21/35 days as of 09-01; two-location vs. "12 PoPs" and FiveM
Enhanced support (UX track) were at 42/7 days as of 09-02; YouTube 404 and
Discord growth (social track) last confirmed 08-30.

---

## 2026-09-04 (Friday) — Social & Community (Week 7)

**Note:** One week since 08-28. Re-fetched the homepage directly (`curl`) to
confirm all five footer social hrefs unchanged, checked
`youtube.com/@officiallumixsolutions` and `tiktok.com/@lumix.solutions`
directly, and re-pulled the Discord invite API (`uaNYBJQtvn`). Also
searched fresh for any new BisectHosting/Shockbyte/RocketNode TikTok/
YouTube content and for any indexed Lumix social activity. Nothing
genuinely new turned up on either side this run — every open item is
exactly where 08-28 left it, one week older.

### Findings (max 2)

1. **ESCALATION — YouTube footer link hits 42 days (six full weeks)
   unresolved today, the twelfth consecutive ask with zero action.** Direct
   fetch of `youtube.com/@officiallumixsolutions` today returns the same
   HTTP 404 confirmed on every check since 07-31 (07-31, 08-07, 08-14,
   08-15, 08-16, 08-21, 08-22, 08-23, 08-28, 08-29, and this one). The
   homepage footer's raw HTML (re-pulled today) still links to it. TikTok's
   `@lumix.solutions` still loads (HTTP 200) but remains unindexed with no
   discoverable posts, same as every prior check — not re-analyzed as a
   separate item since its status hasn't changed since 07-24.
   → *Action:* Unchanged from every prior ask, now six weeks old: whoever
   has footer/CMS access should either delete the dead YouTube link or
   replace it with the correct handle today. This is the single most
   overdue item in the entire log across all five tracks, and the fix is a
   one-line footer edit with zero dependencies.

2. **Discord growth stalled again this week, and no evidence the
   community-content plan has ever shipped.** Invite API today: 141
   members / 21 online — flat against 08-28's 141/22 and within noise of
   08-29's 140/26. Last week's +6 member gain (08-21→08-28) did not
   continue; this week reads as a return to the earlier flat baseline, not
   a trend. The site footer, Discord invite description, and fresh
   searches this run again show no evidence the "share your server clip"
   call (first recommended 07-24, now 42 days open) or any other
   community-sourced content has ever gone out.
   → *Action:* Same ask as every prior Friday — get a direct yes/no on
   whether the community-clips call has been posted. Six weeks of flat-to-
   noisy membership with zero confirmed content output is itself now the
   finding: there's no data yet on whether the idea works, because it's
   never been tried.

### Do this today (<1 hour)
Delete the dead YouTube icon/link from the site footer (finding 1). Twelfth
consecutive ask, zero dependencies, now 42 days overdue — the cheapest,
most repeated, and most ignored fix on the entire board.

**Escalation status:** YouTube 404 (social track) crosses 42 days (six full
weeks) unresolved today, its seventh consecutive Friday-or-off-rotation
escalation since 07-31. No other tracks re-checked this run beyond the
homepage footer fetch used for finding 1.

---
