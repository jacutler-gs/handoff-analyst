# Handoff Analyst

> A Pulse 2026 SC demo showing how a CSM could interact with Gainsight and its connected products through a **headless, AI-orchestrated experience** — surfacing everything they need to take over a new account in under 30 seconds.

![Status](https://img.shields.io/badge/status-demo-purple) ![Built for](https://img.shields.io/badge/built%20for-Pulse%202026-blue) ![Hosting](https://img.shields.io/badge/hosting-GitHub%20Pages-black)

---

## The Concept

User personas are about to start interacting with Gainsight and its connected products through Claude or other "headless" model interfaces — not just the Gainsight UI. The **Handoff Analyst** is one persona-shaped agent view, built for the moment a **CSM takes over a brand-new account from presales/onboarding**.

Instead of spending 2–3 days digging through C360, Timeline, Cockpit, Staircase, PX, Community, and Skilljar to piece together what happened during the sale, the agent does it for them and presents one synthesized view:

- What was promised or discussed during presales — **with dates and citations**
- What the previous CSM was actively quarterbacking, and which work is a direct baton-pass
- Who the stakeholders are and how they feel
- What's been adopted (and what hasn't) across the connected products
- Where the systems disagree, and which signal to actually trust
- What the CSM should do this week

The dashboard is built for **Abbett**, a representative Enterprise account in the CSMCP-Demo tenant ($275K ARR, ~34 days from renewal, in active expansion).

---

## Design Principle: Synthesis, Not Display

The dashboard intentionally avoids regurgitating data the CSM can already find in C360. A health score chart, a list of CTAs, a renewal date — those exist a million places. The agent's job is **synthesis and judgment**, so every panel earns its place by doing one of:

1. **Aggregating across multiple systems** that the CSM would otherwise have to open separately
2. **Reading and rewriting** what's there into a narrative form the source UI doesn't provide
3. **Reconciling conflicts** between systems and making a judgment call
4. **Recommending an action**, not just describing a state
5. **Citing where it came from** so the CSM trusts the synthesis and can drill in if needed

If a panel can be replaced by "go look at C360," it shouldn't be on this dashboard.

---

## What's on the Dashboard

### Sticky Navigation Rail
Just under the header, a sticky nav bar with jump-to links: Brief · Sally's Work · Signal Reconciliation · Commitments · Stakeholders · Signals · Risks · Plans · Ask Analyst. Stays pinned as you scroll so the CSM can jump between panels without scrolling back to the top.

### 1. Header
Account identity at a glance — industry, segment, region, status, lifecycle stage — with a prominent countdown to renewal date so the time pressure is visible immediately.

### 2. AI Handoff Brief (hero)
A 30-second read covering:
- The good news (Green health, signed 2-year term, expansion intent)
- The "but" (17 open risk CTAs, AI Insights Red and declining, 20% usage drop)
- **Three explicit Week 1 priorities** with handoff provenance under each one — annotated *"Continuing Sally's work"* with status notes, so the CSM knows exactly what's a baton-pass versus a fresh recommendation
- A counter at the top of the priorities: *"3 of 3 continuing Sally's work"*

This is the "wow" moment — a CSM who reads only this panel walks away with the full picture, knows what's already in motion, and has a clear next step.

### 3. Top Stats Strip
Six headline numbers: Current ARR, Renewable ARR, Open Upsell, Health Score, Staircase Sentiment, Customer Lifetime.

### 4. What Sally Was Quarterbacking
**The previous CSM's active work, surfaced for the incoming CSM.** Pulled from her authored Timeline notes, Cockpit CTAs she owned, and Success Plan objectives where she was the owner. Six items, each with:

- **Status**: In-flight, Blocked, Scheduled, or Deferred
- **Last touch date** so the CSM sees freshness
- **Source citation** — which Timeline note, CTA, email thread, or Success Plan objective it came from
- **Who Sally was coordinating with** — Solutions Architecture, Product, Support, Marketing, etc.
- **A note** explaining where the work stands

Header summary shows a count of in-flight vs. blocked items, so the inheriting CSM can immediately gauge what's stuck.

> 💡 **This panel is conditional.** A `HAS_PRIOR_CSM` flag at the top of the data block controls whether it renders. For a brand-new sale where there is no prior CSM, the panel hides entirely, the nav link disappears, and the Brief priorities lose their "Continuing Sally's work" annotations. Set `HAS_PRIOR_CSM = false` to demo that state.

### 5. Cross-System Signal Reconciliation
**The flagship agent panel.** Six different systems are measuring this account's health and saying very different things:

- Gainsight rollup: **74 Green**
- Scorecard AI Insights group: **45 Red, declining**
- Staircase AI: **100, strongly positive**
- PX: **−20% usage drop**
- Support: **10+ open tickets**
- Cockpit: **17 open risk CTAs**

The agent explains *why* the systems disagree (Staircase reflects executive conversations; PX/Cockpit reflect end-user reality; the Gainsight rollup averages both and is misleading), and gives a decision-by-decision guide on which signal to trust:

- **Renewal commercial story** → Staircase + rollup
- **Internal risk forecasting** → AI Insights + PX
- **Expansion conversation** → Don't pitch Analytics until DAU recovers
- **Exec reporting** → Cite both, don't hide the split

This is the panel that exists nowhere in the Gainsight UI today.

### 6. Commitments & Promises from Presales
Synthesized from Staircase conversations + Gainsight timeline. The panel opens with a **date anchor strip** showing the four dates every commitment needs context against:

- **Customer Since** (Go-live)
- **Current Term Started** (Original contract)
- **Renewal Signed** (2-year DocuSign)
- **New Term Through** (Next renewal)

Then a filterable grid of commitments in three categories:

- **Value delivered** — ROI metrics quoted in presales (34% ROI, 91% deliverability, 55% manual work reduction, etc.). These need to stay quoted in every QBR going forward.
- **Commitments** — Things sales/SC promised but haven't been fully delivered yet (Advanced Analytics 3-4 week implementation, 15–20% capacity uplift, multi-BU rollout).
- **Concerns** — Risks flagged by the customer during the sale (implementation complexity, governance/compliance for scaled rollout).

**Every commitment card carries**:
- A **monospaced date pill** showing when it was made or committed
- The **source category** (e.g., "Q3 BR", "Renewal email")
- An **italic citation line** showing exactly where in Timeline or Staircase it came from
- A red **⚠ Overdue** badge when the commitment is past its expected delivery

This is the panel that answers the CSM's core question: *"What did sales tell them we would do, and when?"*

### 7. Stakeholder Map
Eight key contacts with engagement signal (Champion / Engaged / Watchful), depth, last touch date, and a one-line note on each:

- **Sarah Johnson** — Executive Sponsor, said "confidence has been restored"
- **Michael Chen** — Commercial owner, approved 2-year term
- **David Patel** — Technical champion, owned the automation pilot
- **Marie Forshaw** — Watchful exec, flagged need for broader alignment
- Plus four more

### 8. Adoption & Engagement Signals
Cross-product signals from the connected products — each row tagged with its source connector:
- **PX**: Logged in, 137 of 210 users active
- **Community**: Topics & Replies, Identified Advocates
- **Skilljar**: Learning Path completion, failed Academy course
- **Scorecard**: NPS, CSAT, Adoption Depth and Breadth

### 9. Risk Radar
Seven high-priority risks distilled from the 17 open risk CTAs on the account. Each carries owner and source connector inline.

### 10. Active Success Plans
Five success plans currently active on the account, with a recommendation to do a hygiene review in week 1 (some are stale).

### 11. Ask the Handoff Analyst
Eight pre-canned questions a CSM would actually ask, with answers grounded in the real data:
- *"What was committed during presales?"*
- *"Who are the executive stakeholders and what's my entry strategy?"*
- *"What are the top risks I'm inheriting?"*
- *"What's the renewal motion and where am I in it?"*
- *"Has the customer engaged with Community, Skilljar, or PX?"*
- *"Which success plans are active and who owns them?"*
- *"Give me a 30-second elevator brief."*
- *"Is there a case study or reference opportunity?"*

Click any question to expand the answer.

---

## Source Badges

Every panel carries a color-coded badge showing which connector(s) the data came from. This makes the **"orchestration across connected products"** story visible at a glance without anyone having to say it out loud.

| Badge | Color | What it represents |
|---|---|---|
| `Gainsight` | Purple | Company, CTAs, success plans (Gainsight CSMCP) |
| `Staircase` | Cyan | Conversations, sentiment, presales narrative |
| `PX` | Pink | Product usage, logins, DAU/WAU signals |
| `Community` | Orange | Topics, replies, advocate identification |
| `Skilljar` | Yellow | Learning paths, certifications |
| `Scorecard` | Green | Health measures and groups (Gainsight scorecard) |
| `Cockpit` / `Timeline` | Purple | Gainsight-family sub-domains |

---

## Data Sources (and What's Real)

All data is **snapshotted at build time** from real demo systems:

- **Gainsight CSMCP-Demo** — Company profile, scorecard, CTAs, success plans, timeline activities. Account is the parent "Abbett" record.
- **Staircase AI** — Account 15191592, queried with the demo tenant credentials. Presales narrative, stakeholder signals, sentiment.

Every name (Sally McField, Sarah Johnson, Michael Chen, David Patel, etc.), every dollar amount, every score, every date is grounded in those systems. The CSM (Sally McField) and SC (Matt Shea) are the actual people recorded on the account. Quarterback Map items and commitment citations are synthesized from her authored Timeline notes, Cockpit CTAs, Success Plan objectives, and Staircase email threads.

> ⚠️ **Important**: This is **not** internal Gainsight production data. It is the public CSMCP-Demo tenant + the Staircase demo account. Safe to share externally and host publicly.

---

## Why Snapshotted (Not Live)?

GitHub Pages serves **static files only** — no backend. To make live MCP calls from the page, we'd need a server to hold credentials and orchestrate the connectors.

For a Pulse demo, snapshotted is actually better:
- ✅ Works anywhere with no auth
- ✅ Loads instantly (no waiting for API calls during a live demo)
- ✅ The data is stable — won't change between rehearsal and the actual session
- ✅ Easy to share via a public URL
- ❌ Data won't refresh — but for the handoff story, the point is the **snapshot**, not the live state

When/if this evolves into a live agent, the architecture would swap snapshotted JSON for actual MCP tool calls behind a thin server.

---

## How to Deploy on GitHub Pages

This is a single-file HTML artifact. No build step, no `npm install`, no framework.

### One-time setup

1. Create a new public GitHub repo (e.g. `handoff-analyst-demo`)
2. Add two files to the root:
   - `index.html` — the dashboard (copy from the artifact)
   - `README.md` — this file
3. In repo settings → **Pages**, choose:
   - **Source**: Deploy from a branch
   - **Branch**: `main` / `/ (root)`
4. Save. GitHub will give you a URL like `https://<your-user>.github.io/handoff-analyst-demo/`

That's it. First publish takes 1–2 minutes. Subsequent pushes deploy in seconds.

### Updating

Push any change to `main` and GitHub Pages redeploys automatically. To update the underlying data, edit the constants at the top of the `<script>` block in `index.html`:

- `ACCOUNT` — top-level account metadata
- `HAS_PRIOR_CSM` / `PRIOR_CSM_NAME` — toggle the Quarterback Map panel for net-new accounts
- `QUARTERBACK_ITEMS` — what the previous CSM was actively driving on handoff day
- `BRIEF_PROVENANCE` — provenance flags for each Week 1 Priority in the Brief
- `SIGNALS_TABLE` — the six conflicting signal rows in the Reconciliation panel
- `STAIRCASE` — Staircase sentiment number
- `COMMITMENTS` — presales commitments and value, each with `date`, `citation`, and optional `overdue` flag
- `CUSTOMER_DATES` — anchor dates shown at the top of the Commitments panel
- `STAKEHOLDERS` — contact map
- `RISKS` — risk radar items
- `ENGAGEMENT_SIGNALS` — adoption/engagement rows
- `SUCCESS_PLANS` — active plans
- `ANALYST_QA` — Q&A drawer

---

## Demoing Two Scenarios

The `HAS_PRIOR_CSM` flag lets the dashboard tell two different stories:

### Scenario A: Inherited account (default)
`HAS_PRIOR_CSM = true`. The Quarterback Map panel renders, the nav shows "Sally's Work", and the Brief priorities carry "Continuing Sally's work" annotations. This is the demo flow.

### Scenario B: Net-new sale handoff
`HAS_PRIOR_CSM = false`. The Quarterback Map disappears, the nav link disappears, and the Brief reads as fresh recommendations from the agent rather than baton-passes from a predecessor. Good for showing the dashboard's flexibility across different handoff types.

Toggling between the two states is a one-line config change. Worth having both ready for Pulse Q&A if anyone asks how this would work for a fresh account.

---

## How to Demo

A clean 3.5-minute flow for SC team rehearsal:

**0:00 — Frame the problem (15s)**
> "A CSM gets handed a new account. Today they spend 2–3 days digging through C360, Timeline, Cockpit, Staircase, PX, Community, and Skilljar to figure out what sales committed and where the landmines are. This is what that looks like if a Claude-style agent does the synthesis instead."

**0:15 — Hero brief (30s)**
> "30-second brief. $275K ARR, renewal in 34 days, signed 2-year term. But health is Green at 74 *while* the account is carrying 17 open risk CTAs — the relationship is recovering, operational health is lagging. Three explicit Week 1 priorities — and notice each one is annotated with where it came from. All three are continuing work Sally was already driving. The agent isn't making this up; it's reading her Cockpit, her Timeline, her email threads."

**0:45 — Quarterback Map (45s)**
> "And here's where that handoff information comes from. Six items Sally had in flight on handoff day. Each one shows the status — in-flight, blocked, scheduled — when she last touched it, where the agent pulled it from (Cockpit CTA, Timeline note, Success Plan objective), and who she had pulled in to help. The blocked item with Michael Chen on capacity projections? That's what's holding up the renewal modeling. The CSM doesn't have to guess what Sally was working on — it's all here, cited."

**1:30 — Signal Reconciliation (60s) — the wow moment**
> "Here's the panel you can't get anywhere else. Six different systems measuring this account's health and they disagree. Gainsight 74 Green. Scorecard AI Insights 45 Red. Staircase 100. PX usage dropped 20%. The agent doesn't just show this — it explains *why* they disagree (executive conversations vs. end-user reality) and tells the CSM which signal to trust for which decision. Don't pitch Advanced Analytics until DAU recovers. Report Green to execs but cite the risk CTA load. This is the synthesis no Gainsight UI gives them today."

**2:30 — Commitments panel (40s)**
> "This one saves days of work. Every number sales quoted in the deal — 34% ROI, 91% deliverability, 55% less manual work — auto-pulled from Staircase conversations with dates and citations. Filter by Commitments and you see what hasn't been delivered yet: Advanced Analytics plan, 15–20% capacity uplift. Look at the overdue flags — these are what gets forgotten in handoff today. Every card cites where it came from so the CSM trusts the synthesis."

**3:10 — Ask the Analyst (20s)**
> "And it's interactive. Eight pre-canned questions a CSM would actually ask. The agent doesn't just surface data; it tells the CSM what to do."

**3:30 — Land (10s)**
> "This is one persona view. Same pattern works for Renewal Analyst, Risk Analyst, EBR Analyst, Onboarding Analyst. Headless Gainsight isn't a chatbot — it's purpose-built agents for the moments customer success teams actually need them."

---

## Architecture Notes

The dashboard is intentionally **single-file** with no framework dependency beyond CDN-loaded React + Recharts. This keeps the deployment story dead simple:

- React 18 (CDN) — UI rendering
- Recharts 2.10 (CDN, optional) — included as a dependency but no longer essential after the Health Trajectory panel was replaced with Signal Reconciliation
- Babel Standalone (CDN) — in-browser JSX compilation so we don't need a build step
- Inline `<script type="text/babel">` for the dashboard logic
- All data as JS constants at the top of the script block
- A try/catch around the root render so any failure shows on-screen rather than producing a black page

No localStorage, no backend, no auth, no API keys, no build process.

---

## File Structure

```
handoff-analyst-demo/
├── index.html        # The full dashboard (single file)
└── README.md         # This file
```

---

## Future Ideas (Not in V1)

- **Live MCP calls** via a thin proxy (Cloudflare Worker / Vercel function) so the dashboard refreshes in real time
- **Live Q&A** wired to Anthropic API so the analyst answers ad-hoc questions from the CSM, not just pre-canned ones
- **Active section highlighting** in the sticky nav (intersection observer-style) as you scroll
- **Auto-detect** of `HAS_PRIOR_CSM` based on whether any prior CSM had Timeline activity, instead of a manual flag
- **Other persona views** — Renewal Analyst, Onboarding Analyst, EBR Analyst, Risk Analyst, each with its own Signal Reconciliation tailored to its decisions
- **Embed mode** so the same agent could be surfaced inside Gainsight C360 as a panel

---

## Credits

Built by the Gainsight SC team for Pulse 2026.

- **Account data**: Gainsight CSMCP-Demo + Staircase AI demo tenant
- **CSM (in demo data)**: Sally McField
- **Solutions Consultant (in demo data)**: Matt Shea
