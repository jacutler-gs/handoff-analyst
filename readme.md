# Handoff Analyst

> A Pulse 2026 SC demo showing how a CSM could interact with Gainsight and its satellite products through a **headless, AI-orchestrated experience** — surfacing everything they need to take over a new account in under 30 seconds.

![Status](https://img.shields.io/badge/status-demo-purple) ![Built for](https://img.shields.io/badge/built%20for-Pulse%202026-blue) ![Hosting](https://img.shields.io/badge/hosting-GitHub%20Pages-black)

---

## The Concept

User personas are about to start interacting with Gainsight and its satellite products through Claude or other "headless" model interfaces — not just the Gainsight UI. The **Handoff Analyst** is one persona-shaped agent view, built for the moment a **CSM takes over a brand-new account from presales/onboarding**.

Instead of spending 2–3 days digging through C360, Timeline, Cockpit, Staircase, PX, Community, and Skilljar to piece together what happened during the sale, the agent does it for them and presents one synthesized view:

- What was promised or discussed during presales
- Who the stakeholders are and how they feel
- What's been adopted (and what hasn't) across the satellite tools
- Where the risks and expansion levers are
- **Where the systems disagree, and what to actually trust**
- What the CSM should do this week

The dashboard is built for **Abbett**, a representative Enterprise account in the CSMCP-Demo tenant ($275K ARR, ~34 days from renewal, in active expansion).

---

## Design Principle: Synthesis, Not Display

The dashboard intentionally avoids regurgitating data the CSM can already find in C360. A health score chart, a list of CTAs, a renewal date — those exist a million places. The agent's job is **synthesis and judgment**, so every panel earns its place by doing one of:

1. **Aggregating across multiple systems** that the CSM would otherwise have to open separately
2. **Reading and rewriting** what's there into a narrative form the source UI doesn't provide
3. **Reconciling conflicts** between systems and making a judgment call
4. **Recommending an action**, not just describing a state

If a panel can be replaced by "go look at C360," it shouldn't be on this dashboard.

---

## What's on the Dashboard

### Sticky Navigation Rail
Just under the header, a sticky nav bar with jump-to links: Brief · Signal Reconciliation · Commitments · Stakeholders · Signals · Risks · Plans · Ask Analyst. Stays pinned as you scroll so the CSM can jump between panels without scrolling back to the top.

### 1. Header
Account identity at a glance — industry, segment, region, status, lifecycle stage — with a prominent countdown to renewal date so the time pressure is visible immediately.

### 2. AI Handoff Brief (hero)
A 30-second read covering:
- The good news (Green health, signed 2-year term, expansion intent)
- The "but" (17 open risk CTAs, AI Insights Red and declining, 20% usage drop)
- **Three explicit Week 1 priorities** the CSM should action

This is the "wow" moment — a CSM who reads only this panel walks away with the full picture and a clear next step.

### 3. Top Stats Strip
Six headline numbers: Current ARR, Renewable ARR, Open Upsell, Health Score, Staircase Sentiment, Customer Lifetime.

### 4. Cross-System Signal Reconciliation
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

### 5. Commitments & Promises from Presales
Synthesized from Staircase conversations + Gainsight timeline. Three filter categories:

- **Value delivered** — ROI metrics quoted in presales (34% ROI, 91% deliverability, 55% manual work reduction, etc.). These need to stay quoted in every QBR going forward.
- **Commitments** — Things sales/SC promised but haven't been fully delivered yet (Advanced Analytics 3-4 week implementation, 15–20% capacity uplift, multi-BU rollout).
- **Concerns** — Risks flagged by the customer during the sale (implementation complexity, governance/compliance for scaled rollout).

This is the panel that answers the CSM's core question: *"What did sales tell them we would do?"*

### 6. Stakeholder Map
Eight key contacts with engagement signal (Champion / Engaged / Watchful), depth, last touch date, and a one-line note on each:

- **Sarah Johnson** — Executive Sponsor, said "confidence has been restored"
- **Michael Chen** — Commercial owner, approved 2-year term
- **David Patel** — Technical champion, owned the automation pilot
- **Marie Forshaw** — Watchful exec, flagged need for broader alignment
- Plus four more

### 7. Adoption & Engagement Signals
Cross-product signals from the satellite tools — each row tagged with its source connector:
- **PX**: Logged in, 137 of 210 users active
- **Community**: Topics & Replies, Identified Advocates
- **Skilljar**: Learning Path completion, failed Academy course
- **Scorecard**: NPS, CSAT, Adoption Depth and Breadth

### 8. Risk Radar
Seven high-priority risks distilled from the 17 open risk CTAs on the account. Each carries owner and source connector inline.

### 9. Active Success Plans
Five success plans currently active on the account, with a recommendation to do a hygiene review in week 1 (some are stale).

### 10. Ask the Handoff Analyst
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

Every panel carries a color-coded badge showing which connector(s) the data came from. This makes the **"orchestration across multiple products"** story visible at a glance without anyone having to say it out loud.

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

Every name (Sally McField, Sarah Johnson, Michael Chen, David Patel, etc.), every dollar amount, every score, every date is real data from those systems. The CSM (Sally McField) and SC (Matt Shea) are the actual people recorded on the account.

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
- `SIGNALS_TABLE` — the six conflicting signal rows in the Reconciliation panel
- `STAIRCASE` — Staircase sentiment number
- `COMMITMENTS` — presales commitments and value
- `STAKEHOLDERS` — contact map
- `RISKS` — risk radar items
- `ENGAGEMENT_SIGNALS` — adoption/engagement rows
- `SUCCESS_PLANS` — active plans
- `ANALYST_QA` — Q&A drawer

---

## How to Demo

A clean 3-minute flow for SC team rehearsal:

**0:00 — Frame the problem (15s)**
> "A CSM gets handed a new account. Today they spend 2–3 days digging through C360, Timeline, Cockpit, Staircase, PX, Community, and Skilljar to figure out what sales committed and where the landmines are. This is what that looks like if a Claude-style agent does the synthesis instead."

**0:15 — Hero brief (30s)**
> "30-second brief. $275K ARR, renewal in 34 days, signed 2-year term. But health is Green at 74 *while* the account is carrying 17 open risk CTAs — the relationship is recovering, operational health is lagging. Three explicit Week 1 priorities."

**0:45 — Signal Reconciliation (60s) — the wow moment**
> "Here's the panel you can't get anywhere else. Six different systems are measuring this account's health and they disagree. Gainsight says 74 Green. Scorecard AI Insights says 45 Red. Staircase says 100, strongly positive. PX says usage dropped 20%. The agent doesn't just show this — it explains *why* they disagree (executive conversations vs. end-user reality), and then tells the CSM which signal to trust for which decision. Don't pitch Advanced Analytics until DAU recovers, because PX numbers will get questioned. Report Green to execs but cite the risk CTA load. This is the synthesis no Gainsight UI gives them today."

**1:45 — Commitments panel (30s)**
> "This one saves the CSM days of work. Every number sales quoted in the deal — 34% ROI, 91% deliverability, 55% less manual work — auto-pulled from Staircase conversations. Filter by Commitments and you see what hasn't been delivered yet: Advanced Analytics plan, 15–20% capacity uplift. These are what gets forgotten in handoff today."

**2:15 — Source badges (15s)**
> "And look at the badges on every panel. PX, Community, Skilljar, Staircase, Scorecard — the agent reads from every product in the portfolio and synthesizes. The CSM never logs into seven tools."

**2:30 — Ask the Analyst (30s)**
> "And it's interactive. Eight pre-canned questions a CSM would actually ask. *'Who are the stakeholders?'* — Sarah Johnson, Michael Chen, David Patel, here's the entry strategy on each. The agent doesn't just surface data; it tells the CSM what to do."

**3:00 — Land (10s)**
> "This is one persona view. Same pattern works for Renewal Analyst, Risk Analyst, EBR Analyst, Onboarding Analyst. Headless Gainsight isn't a chatbot — it's purpose-built agents for the moments customer success teams actually need them."

---

## Architecture Notes

The dashboard is intentionally **single-file** with no framework dependency beyond CDN-loaded React + Recharts. This keeps the deployment story dead simple:

- React 18 (CDN) — UI rendering
- Recharts 2.10 (CDN, optional) — included as a dependency but no longer essential after the Health Trajectory panel was replaced
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
- **Other persona views** — Renewal Analyst, Onboarding Analyst, EBR Analyst, Risk Analyst, each with its own Signal Reconciliation tailored to its decisions
- **Embed mode** so the same agent could be surfaced inside Gainsight C360 as a panel

---

## Credits

Built by the Gainsight SC team for Pulse 2026.

- **Account data**: Gainsight CSMCP-Demo + Staircase AI demo tenant
- **CSM (in demo data)**: Sally McField
- **Solutions Consultant (in demo data)**: Matt Shea
