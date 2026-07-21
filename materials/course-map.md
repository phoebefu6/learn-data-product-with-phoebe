# learn-data-product-with-phoebe - course map + running case canon

**Format:** capability catalog / showcase. Not a build-it-yourself practitioner course.
**Audience (dual):** prospective clients + KOL followers AND execs / decision-makers.
**Voice:** each data product = what it is (plain) -> mini SVG -> Kasa example -> business value / ROI -> when to reach for it -> maturity-tier chip. Light on code, heavy on "what it delivers and when".
**Spine:** ONE running case (Kasa) matures up the ladder, tier by tier.
**Sessions:** 6. Palette climbs the ladder: graphite/indigo intro -> slate infra -> teal analytics -> indigo DS -> violet gen-AI -> indigo summit.
**Attribution:** "by Phoebe Fu". Hyphens only, never em/en dash.

---

## Running case canon: Kasa

**Kasa** - a fictional omnichannel retailer + embedded fintech in Southeast Asia. Use these facts consistently across all 6 sessions (do not invent conflicting numbers).

- HQ Singapore. ~4M customers, 180 physical stores across SG / MY / ID / PH, an e-commerce app, and **Kasa Pay** - an embedded loyalty wallet with a small buy-now-pay-later (BNPL) line.
- Revenue ~US$1.2B. Blended online+offline.
- **The arc:** Kasa starts in data chaos - spreadsheets emailed around, every team with its own "revenue" number, no single source of truth. Across the course it climbs the ladder: lay infrastructure, earn trustworthy analytics, add data science, then govern and automate with gen AI. By the capstone the products stack into ONE governed platform (ties to Phoebe's FDE one-data-platform vision).
- **Why Kasa carries every product:** retail (BI, forecasting, segmentation, thematic analysis), 180 stores (biz performance monitoring, exec scorecard), Kasa Pay wallet + BNPL (payment fraud, transaction ML), an app (self-serve BI, support bot / agentic AI), and a regulated fintech arm (governance, data quality, PDPA).
- Named characters to reuse: **Mei** (CDAO, the buyer/sponsor), **Raj** (data engineering lead), **Sofia** (head of BI / analytics), **Deng** (data scientist), **the CFO** (scorecard consumer), **the Kasa Pay risk team** (fraud consumer).

**Recurring flagship examples (thread these through):**
- **BI / scorecard:** "one trusted revenue number" for the CFO across 180 stores + app.
- **Fraud detection:** Kasa Pay wallet account-takeover + BNPL default + promo-abuse.
- **Forecasting:** demand forecast per store-SKU for inventory buys.
- **Segmentation:** loyalty base -> actionable CRM segments.
- **Agentic AI / bot:** "Where is my order / refund me" support agent.

---

## The maturity ladder (the spine)

Four tiers, rising. Each product sits on a rung. The core teaching line: **you cannot skip rungs - a dashboard on ungoverned, unvalidated data is a confident lie; an AI agent on a broken warehouse hallucinates with authority.** (Echoes Monica Rogati's AI Hierarchy of Needs: infrastructure before AI.)

```
Gen AI          govern + amplify        (violet)
Data Science    predict + segment       (indigo)
Data Analytics  measure + explain       (teal)
Infrastructure  store + serve           (slate)
```

Tier colour ramps (SVG hexes + per-page :root override of --indigo*):
- **Infra / slate:** deep #334155 · primary #475569 · mid #64748B · soft #94A3B8 · tint #F1F5F9
- **Analytics / teal:** deep #0F766E · primary #0D9488 · mid #14B8A6 · soft #5EEAD4 · tint #F0FDFA
- **DS / indigo (site base):** deep #3730A3 · primary #4F46E5 · mid #6366F1 · soft #A5B4FC · tint #EEF2FF
- **Gen AI / violet:** deep #5B21B6 · primary #7C3AED · mid #8B5CF6 · soft #C4B5FD · tint #F5F3FF
- Universal warm/star accent (all pages): lime #84CC16 on ink #1A2E05 (this is the template `--amber`, keep it).
- ink #1E1B3A · muted #6B6785 · faint #C7C4DE · hairline #E7E5F2.

---

## Session -> product mapping (29 products)

Every product card carries a **maturity chip** (its tier) and a **"reach for it when"** line. Diagrams: 1-2 SVGs per session (a tier overview + one flagship product anatomy).

### Session 1 - The Data Product Maturity Ladder (intro, indigo base) 🟢
Not a product session - the frame. Covers: what "a data product" even means (something built, owned, and maintained that delivers repeatable value from data - not a one-off chart); the 4-tier ladder; why you climb, not skip; Kasa introduced in full chaos; how to read the rest of the course. One SVG: the ladder. One SVG: "same question, four maturities" (how "how are we doing?" is answered at each tier). Sets the card format learners will see 29 times.

### Session 2 - Infrastructure (slate) 🟢 · 7 products
The plumbing. "Boring on purpose - everything above stands on it."
1. **Cloud Infra** - managed compute/storage/network you rent instead of run. Kasa: lift the on-prem store DBs to cloud so data isn't trapped per-store. Value: elastic cost, no capex, faster to build. Reach when: scaling past one server / spiky load.
2. **App Performance Monitoring (APM)** - watch latency/errors/traces of running apps + pipelines. Kasa: catch the nightly ETL that silently half-loaded. Value: find breakage before the business does. Reach when: pipelines/app feed decisions.
3. **Data Schema Design** - the deliberate shape of tables/keys/types before data lands. Kasa: model orders / customers / payments once, cleanly. Value: joins that work, no rework. Reach when: standing up any new store.
4. **Data Dictionary** - the plain-language catalog of every field + meaning + owner. Kasa: one definition of "active customer". Value: kills the "whose number is right" fight. Reach when: >1 team reads the same data.
5. **Data Dump** - a raw, as-is export of source data. Kasa: nightly raw drop from the POS system. Value: cheap capture, nothing lost. Reach when: you must land data before you understand it.
6. **Data Lake** - cheap store for raw + semi-structured data of any shape. Kasa: app logs + clickstream + POS + wallet events in one lake. Value: keep everything, decide schema later (schema-on-read). Reach when: variety/volume outgrows a warehouse alone.
7. **Data Warehouse** - modeled, query-fast store of clean, conformed data for analytics. Kasa: the conformed sales/customer marts BI runs on. Value: one trusted, fast source for reporting. Reach when: you need reliable, repeatable analytics (schema-on-write).
Flagship SVG: lake vs warehouse (raw-in / modeled-out), plus the pipeline dump -> lake -> warehouse.

### Session 3 - Data Analytics (teal) 🟡 · 11 products
Turning stored data into trustworthy answers. Biggest session - group it: (a) trust the number, (b) show the number, (c) run on the number.
1. **Data Validation** - automated checks that data is complete/valid/fresh before use. Kasa: reject a store's load if row-count drops 30%. Value: no garbage reaches a dashboard. Reach when: before ANY reporting - the gate.
2. **Smart Reporting** - reports that are automated, refreshed, and self-explaining (not hand-built decks). Kasa: the weekly store-performance report generates itself. Value: hours back, no copy-paste errors. Reach when: you rebuild the same report by hand.
3. **Dashboarding** - live visual views of metrics for monitoring/exploration. Kasa: the daily sales + traffic dashboard per region. Value: everyone sees the same live picture. Reach when: a metric needs watching, not a one-off.
4. **Executive Scorecard** - the few board-level numbers vs target, on one page. Kasa: CFO's revenue / margin / NPS / cash scorecard. Value: leadership aligned on what matters. Reach when: execs ask "how are WE doing" weekly.
5. **Self-Serve BI Enablement** - tools + training + governed datasets so business users answer their own questions. Kasa: store managers slice their own numbers, no ticket. Value: analysts freed from ad-hoc queue. Reach when: the analytics team is a bottleneck.
6. **Metric Development** - defining a metric rigorously (formula, grain, filters, edge cases). Kasa: nail "conversion rate" once - which sessions, which orders. Value: everyone computes it the same way. Reach when: a term means 3 things to 3 teams.
7. **KPI System Design** - a coherent tree of KPIs linked to goals + owners (not a random pile). Kasa: north-star -> input KPIs, each owned. Value: metrics that drive action, not vanity. Reach when: you have 200 metrics and no hierarchy.
8. **Ad-hoc Thematic Analysis** - a deep one-off study answering a specific business question. Kasa: "why did MY margin drop in Q2?" Value: a decision, fast, when no dashboard covers it. Reach when: a novel, high-stakes question appears.
9. **Biz Performance Monitoring** - ongoing tracking of business health with alerting on drift. Kasa: alert when a region's basket size falls 2 weeks running. Value: catch problems while they're small. Reach when: you need to be told, not to go look.
10. **Regular Insights Sharing** - a cadenced ritual turning data into narrative for the org. Kasa: Sofia's monthly "3 things the data says" note. Value: data culture, not just data. Reach when: dashboards exist but nobody acts.
11. **Data Dictionary Scorecard** - a health score on the dictionary itself: % fields defined/owned/fresh. Kasa: track "78% of gold tables documented". Value: makes governance measurable + funded. Reach when: the dictionary exists but rots.
Flagship SVG: the "trust pyramid" (validation -> metric def -> KPI tree -> scorecard) + a scorecard mock.

### Session 4 - Data Science (indigo) 🟠 · 5 products (+ fraud showcase)
Using data to predict and personalize. Where "descriptive" becomes "predictive/prescriptive".
1. **Data Literacy Training** - lifting the org's ability to read/question/use data. Kasa: managers learn to read a confidence interval, not just a mean. Value: better decisions everywhere; prerequisite for self-serve + AI. Reach when: tools outrun people's ability to use them. (Note: literacy is really cross-cutting - flag that Phoebe placed it in DS because it's the human on-ramp to the predictive tier.)
2. **Customer Segmentation** - grouping customers by behavior/value for targeted action. Kasa: RFM + k-means on the loyalty base -> 6 actionable CRM segments. Value: right offer, right customer, higher ROI. Reach when: you treat all customers the same.
3. **Sales Forecasting** - predicting future demand/revenue from history + drivers. Kasa: per store-SKU weekly forecast for inventory buys. Value: less stockout + less dead stock. Reach when: you buy/plan against an unknown future.
4. **Machine Learning** - models that learn patterns to score/classify/rank at scale. Kasa flagship: **fraud detection** on Kasa Pay - a classifier scoring each wallet/BNPL transaction for account-takeover, default, promo-abuse. Value: block fraud without blocking good customers. Reach when: the rule-list can't keep up with adversaries. (Also: churn, propensity, recommendations.)
5. **Data Product** - the meta-lesson: a model becomes a *product* only when it's deployed, owned, monitored, and re-trained - not a notebook. Kasa: the fraud score served live behind Kasa Pay checkout with monitoring + retraining. Value: durable value vs a one-off model. Reach when: a model needs to run in production, reliably, for years.
Flagship SVG: fraud-detection flow (transaction -> features -> model -> score -> allow/hold/deny + feedback loop) + segmentation scatter.

### Session 5 - Gen AI (violet) 🔴 · 6 products (+ support bot showcase)
Governing and amplifying with the newest layer. Teach the nuance: **governance + quality are foundational, but they get real teeth (and urgency) in the gen-AI era** - because LLMs/agents act on data at scale and amplify any rot.
1. **Data Governance** - the policies/roles/controls for how data is owned, accessed, protected, used. Kasa: PDPA-compliant access + lineage on wallet data. Value: trust, compliance, safe AI. Reach when: data is regulated / shared / feeding AI. (Foundational, teeth in gen-AI era.)
2. **Data Quality Scorecard** - a live health score of data across completeness/accuracy/timeliness. Kasa: quality score gating what the AI agent may use. Value: quality becomes visible + fundable. Reach when: quality problems keep surfacing downstream.
3. **AI Literacy Training** - lifting the org's ability to use + question AI safely. Kasa: staff learn prompt basics + when NOT to trust the model. Value: adoption without incidents. Reach when: everyone suddenly has AI tools.
4. **AI Use Case Discovery Workshop** - a structured session to find + prioritize AI opportunities by value/feasibility. Kasa: score 20 ideas, pick the support bot + fraud copilot. Value: focus + buy-in before spend. Reach when: "we should use AI" with no plan.
5. **Workflow Automation** - AI/rules automating a repeatable multi-step process. Kasa: auto-triage + draft replies for support tickets. Value: hours saved, faster response. Reach when: a process is repetitive + rule-ish.
6. **Agentic AI** - AI that plans + acts across tools/steps toward a goal, with guardrails. Kasa flagship: the **support agent** that checks order status, issues a refund within policy, escalates edge cases. Value: 24/7 resolution, human-in-loop for risk. Reach when: automation needs judgment + tool use, not a fixed script.
Flagship SVG: agentic loop (goal -> plan -> tool calls -> guardrail check -> act -> observe) + governance-guardrail layer under it.

### Session 6 - Composing the Platform (indigo summit / capstone) 🟠
Not new products - how the 29 stack into ONE governed platform. Covers: the reference architecture (infra -> analytics -> DS -> gen-AI, with governance as a spine through all tiers); sequencing (what to build first for a company like Kasa, and why skipping rungs backfires); the ROI framing (cost vs value per tier, where the money actually is); and how Kasa went from chaos to platform. Ties to Phoebe's FDE one-data-platform vision. One SVG: the full stacked platform with governance spine. One SVG: the sequencing roadmap (crawl/walk/run). Ends with "which rung is YOUR org on" self-assessment.

---

## Coverage honesty (the "not covered by design" list)

- This is a **capability catalog**, not a hands-on build course. Each product is taught at the "what / example / value / when" level so a leader can commission it and a follower can understand it - **not** at the "here is the code to build it" level. Point deeper courses for the how (see cross-links below).
- Deep how-to lives in Phoebe's other courses: infrastructure/DataOps, SQL, Python data analysis, statistics, experimentation, RAG, LangChain, evals, the governance bucket (PDPA/GDPR/AI-Act), data-literacy, AI-literacy. Cross-link, don't duplicate.
- Vendor-specific tooling (Snowflake/Databricks/BigQuery/specific BI tools) named as examples only; the course is tool-agnostic by design.
- Content verified against Phoebe's consulting spectrum + standard industry definitions, July 2026.

## Cross-links (sibling courses on the hub to reference in "covered / go deeper" rows)
learn-dataops · learn-sql · learn-python-data-analysis · learn-statistics · learn-experimentation · learn-data-literacy · learn-ai-literacy · learn-rag · learn-langchain · learn-evals · learn-data-governance · learn-pdpa-dnc · learn-strategic-thinking.
