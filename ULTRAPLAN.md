# Veritail — ULTRAPLAN
**Technology-Leadership & Value-for-Money Master Plan**
*Companion to PRD v2.0 · Version UP-1.0 — June 2026 · Owner: TMLC Solutions*

> **What this is.** A companion to (not a replacement for) PRD v2.0. The PRD answers *what we build and in what order*. This document answers the two questions the PRD raises but does not fully resolve: **(1) How does Veritail become the technology *leader* of retail commercial operations — not merely competitive, but the un-catchable standard?** and **(2) How does Veritail become the unambiguous *best value for money* for mid-market retail customers?**
>
> **The central claim of this plan: those are the same question.** In mid-2026 the cost of intelligence is collapsing and the architectural "middle" of every agentic-data platform has commoditized. In that world, both leadership and value-for-money come from one place — **proprietary, compounding assets that convert cheap commodity intelligence into finance-grade recovered money.** One flywheel produces both. This document specifies that flywheel, the seven frontier technical bets that power it, the engineered economics that make it cheap, and the sequenced plan to build it — all inside the v2.0 trust gates. **Nothing here justifies skipping a Phase-1 exit criterion. The apex is reached through the wedge, never around it. When timeline and trust gate conflict, the timeline yields.**

---

## 0. The thesis in one page

Three forces converged by mid-2026:

1. **LLMflation.** LLM inference cost has fallen >90% since 2023 — roughly 10x/year historically, now moderating to ~3–5x/year through 2027. Economy-tier models that match 2023 frontier quality now price near **$0.10–0.40 per million tokens**. *Compute is no longer the cost driver, and the model is no longer the moat.*
2. **The middle commoditized.** Lakehouse → ontology/semantic layer → governance → MCP → agents is now the table-stakes pattern. MCP is the default agent-to-data bridge (10,000+ enterprise servers by April 2026). Crisp ships an AI Master Data product and a Retail Knowledge Graph; Palantir Foundry ships the Ontology + AIP + writeback. *Everyone gets the same middle.*
3. **The ends opened up.** Computer-use agents crossed the line of *economic viability* for the no-API long tail (portals, inboxes, files) — but **not** the line of *finance-grade reliability* (leading agents score ~58% on WebArena, ~87–89% on WebVoyager; new benchmarks measure "operational reliability beyond task accuracy" precisely because raw accuracy is not enough). *The data nobody reaches is now reachable — but only by whoever engineers reliability on top of unreliable commodity computer-use.*

**Implication.** Whoever wins does **not** win on the commoditizing middle or on raw model capability — those trend to free. They win by owning the two ends and the memory, and by turning the collapsing cost of compute into customer value and gross margin *at the same time*.

Therefore:

- **Technology leadership = owning the assets cheap commodity intelligence cannot replicate:** a learned no-API **ingestion library**, a finance-grade **resolution-and-recovery loop**, and a multi-year **outcome memory**. These are *data-and-process* moats, not *model* moats — which is exactly why they are durable in the LLMflation era. Everyone gets the same models; only Veritail has the data, the loop, and the history.
- **Value-for-money = the same collapse, captured deliberately.** On a fixed customer workload, cost-per-investigation falls ~3–5x/year. Veritail (a) banks that as gross margin and price headroom, and (b) makes each investigation *worth more* via the proprietary assets — so the value/price ratio compounds.

> **The line that organizes everything below:** *Veritail's competitors are racing on the part of the stack whose price is going to zero. Veritail races on the part whose value compounds.* Every dollar recovered makes the next dollar **cheaper to recover** (memory cuts tokens) and **more valuable to the customer** (better agents, deeper ledger). That single loop is both the leadership engine and the value engine.

---

## 1. What "technology leadership" means in *this* domain (defined precisely)

Leadership is **not** "best AI" — models commoditize, and a January-2026 frontier model is an April-2026 economy model. In retail commercial operations for distributor-heavy markets, leadership is being first **and** structurally hardest-to-copy across **four frontiers**:

| # | Frontier | The leadership bar (what "leading" means, measurably) | Who else is at the frontier | Why they cannot follow Veritail here |
|---|---|---|---|---|
| **F-I** | **Ingestion** — reach data no one else reaches | Finance-grade ingestion of no-API portals/inboxes/files at a *measured, falling* cost-per-successful-sync, with self-healing | Crisp (but only **integrated US retailer POS feeds**, not the no-API EM long tail) | Every portal taught is unscalable grunt work; in EM few even try; the cross-tenant portal registry compounds |
| **F-T** | **Trust** — numbers finance will defend in an audit | 100% brief numeric factuality; complete, tamper-evident, bitemporal lineage; zero wrong numbers in front of finance, for years | Palantir Foundry (but **enterprise-priced, implementation-heavy**) | The moat is the *track record*, not the tech — a multi-year zero-incident streak cannot be bought |
| **F-O** | **Outcome** — close the loop and remember what worked | A growing, context-fingerprinted record of measured intervention→outcome pairs that makes agents better every quarter | No one in EM retail commercial ops | A new entrant — even with better models — has **no history**; this is the one asset compute cannot generate |
| **F-E** | **Economics** — deliver all of the above at mid-market unit cost | Cost-per-resolved-dollar and onboarding-cost-per-tenant *falling* quarter over quarter; healthy gross margin per pack | No one serves this segment at this price | Foundry/Crisp economics are built for enterprise/US; verticalization + LLMflation capture is a different cost structure |

**Veritail's leadership claim, stated exactly:** *the only platform that is at the frontier on all four — ingestion, trust, outcome, and economics — simultaneously, for the mid-market, distributor-heavy segment.* Crisp leads F-I and the middle for US data; Foundry leads F-T for enterprise; **nobody else is even attempting F-I + F-T + F-O + F-E together for this segment.** That intersection is the open, defensible apex.

---

## 2. The seven frontier technical bets (the un-catchable lead)

Each bet sharpens and makes more ambitious the `[A]` apex features already in the PRD, and adds what the PRD leaves implicit: *why this is leadership, why it cannot be copied, the metric that proves it, and the ambitious frontier form.* Priority/phase tags are consistent with PRD §14.

### Bet 1 — The Self-Healing No-API Ingestion Mesh `(F-I · wedge · Phase 1→3)`
*Sharpens F-1.6, F-1.8, F-1.9, F-1.11.*

- **What it is.** Not "a portal scraper." A reliability-engineered ingestion system layered *on top of* commodity computer-use: learned navigation artifacts (DOM **+** visual fingerprints), **tri-modal redundancy** (portal → inbox → file with automatic failover below a reliability floor), **drift sentinels** (continuous UI-change detection that pre-empts breakage instead of reacting to it), and **confidence-gated writes** (sub-threshold records route to human review — never silently into the ledger).
- **Why it is leadership, not parity.** Best-in-class computer-use agents are ~58% reliable on WebArena and ~87–89% on WebVoyager — *nowhere near finance-grade.* The differentiator is therefore **not** the computer-use model (rent it; it's commoditizing) but the **reliability engineering that converts unreliable commodity automation into auditable, finance-grade ingestion.** That layer plus the accumulated portal library is the wedge.
- **Why it cannot be copied.** Each portal taught is unscalable grunt work a competitor must repeat; in GCC/India/SEA/Africa few even attempt it; and the **cross-tenant `PortalDefinition` registry `[A]`** turns the library into a compounding code asset shared (with per-tenant credentials) across customers.
- **Frontier form (the ambitious bet).** **"Teach-zero" onboarding:** a new portal of a *known template* onboards with **zero** human teaching by instantiating a parameterized `PortalDefinition`. Marginal ingestion cost for the Nth customer on a known portal → near-zero.
- **Leadership metric.** Per-portal reliability %; **cost-per-successful-sync (must fall)**; portals in registry; teach-zero onboarding rate.

### Bet 2 — The Bitemporal Verified Ledger + Tamper-Evident Audit Chain `(F-T · Phase 1→3)`
*Sharpens F-4.7, F-7.9, F-1.2.*

- **What it is.** The system-of-record spine: every fact versioned across **valid-time × system-time** (any number reconstructable as-of any past moment), provenance + confidence on every record, and a **hash-chained, cryptographically verifiable, append-only audit** of every state transition.
- **Why it is leadership.** This is Foundry-grade lineage at mid-market price. The moment finance **defends a Veritail number in an audit**, Veritail stops being a tool and becomes infrastructure; switching cost approaches infinity.
- **Why it cannot be copied.** Bitemporal stores and hash chains are not exotic — *the moat is the multi-year, zero-wrong-number track record they enable.* That is the slowest moat and the cleanest separator of apex from also-ran.
- **Leadership metric.** Brief numeric factuality = 100%; audit completeness = 100%; **zero-wrong-number streak (days)**; finance sign-off rate.

### Bet 3 — The Action-Centric Ontology with Governed Writeback + Scenario Staging `(F-T · system-of-record gravity · Phase 1→2)`
*Sharpens F-2.5, F-7.8, F-1.10.*

- **What it is.** Entities carry typed `Action` definitions (resolve / dispute / post / notify), each bound to a required role, risk tier, reversibility flag, and writeback target. Consequential actions stage against a **branch of the ledger** (what-if), merging only on approval.
- **Why it is leadership.** This is the move that turns a data model into a *system of record where work happens*. It also rides the **SAP April-2026 API policy tailwind**: the prescribed pattern — *extract once into a governed downstream source of truth, let agents act from there* — **is** this architecture, now blessed by the largest ERP vendor.
- **Why it cannot be copied.** Combined with the resolution loop and the **write-back security profile** (least-privilege per surface, irreversible writes forced to top tier, idempotency-keyed, pen-tested), it is the only *safe* place to let agents act on money in these markets. Safety-at-the-writeback is a trust asset, not a feature.
- **Leadership metric.** System-of-record gravity = **% of tenant money decisions transacted through Veritail**; share of actions executed (not just drafted).

### Bet 4 — The Outcome Ledger as Agent Long-Term Memory `(F-O · THE capability gap · Phase 2→4)`
*Sharpens F-8.2, F-8.5, F-3.6, F-6.7.*

- **What it is.** Every executed action registers a measurement plan; observed effect (seasonality-adjusted) is recorded as a **context-fingerprinted** `Outcome` and **retrieved into future agent reasoning.** Causal honesty is enforced: associations, recorded confounders, quasi-experimental framing — *"associated with," never "caused."*
- **Why it is leadership.** As models commoditize, **proprietary outcome data is the only durable intelligence moat.** A multi-year record of measured intervention→outcome pairs is the one asset a new entrant cannot acquire — they have no history. This is the real, un-closable capability gap.
- **Why it cannot be copied (and compounds twice).** Memory makes agents **better** (higher acceptance, sharper recommendations) *and* **cheaper** (the agent stops re-deriving what it already learned → fewer tokens per investigation). The same asset lifts the numerator and cuts the denominator of value-for-money.
- **Frontier form.** Every Veritail agent measurably improves every quarter from accumulated outcomes — a compounding capability curve competitors start at zero on.
- **Leadership metric.** Cumulative outcome-pair depth; investigation-acceptance % (↑ over time); recommendation precision; **tokens-per-investigation (↓ as memory deepens).**

### Bet 5 — The Eval-Gated Agent Reliability Platform `(F-T + F-E · the LLMflation harness · Phase 0→2)`
*Sharpens F-10.2, F-10.3, F-10.4, F-5.5.*

- **What it is.** Golden-set CI gates (extraction ≥98%, mapping precision ≥95%, brief numeric factuality = 100%), production sampling + drift detection, **continuous per-investigation scoring** of deployed agents, and **deterministic replay** (re-run a historical investigation against pinned inputs; confirm identical findings).
- **Why it is leadership *and* the key to value-for-money.** Most agent products ship without a release gate. Veritail's eval harness is a **competitive weapon**: it lets Veritail adopt the newest, cheapest model the *day it ships*, safely, because the gate catches any regression. **This is how Veritail rides LLMflation** — model-tier routing + eval gate = *always run the cheapest model that still passes the SLO.* Leadership in trust and leadership in cost come from the same harness.
- **Why it cannot be copied quickly.** The golden sets are built from real, resolved retail-commercial cases — another proprietary, accumulating asset.
- **Leadership metric.** Eval SLOs green; **model-swap latency (days from a new model's release to safely in production — drive toward < 7)**; production-audit pass rate; cost-per-investigation.

### Bet 6 — The Two-Way MCP Retail Semantic Layer `(F-T + ecosystem · standard status · Phase 3)`
*Sharpens F-11.8.*

- **What it is.** Every Builder block is callable as an MCP tool/API by external agents (n8n, Copilot, Claude), **and** external MCP tools are callable by Veritail agents. Veritail becomes the **governed retail-commercial semantic layer** exposed over MCP — *the verified number, as a service.*
- **Why it is leadership.** MCP is the default bridge (10,000+ enterprise servers). The winner is whoever becomes the *governed retail-commercial* MCP layer others build on. When an external agent calls Veritail to get "the verified number," Veritail is infrastructure, not an app. Research note: MCP interop is messier than the marketing (naming/auth differ per server) — so the edge is shipping the **cleanest, best-governed retail MCP server**, turning a loose standard into a held position.
- **Guardrail.** Exposure is **additive and metered** — the *governed read* and the semantic layer are shared; the **resolution-and-recovery loop stays proprietary.** We let others read the verified number; we keep the engine that produces and recovers it.
- **Leadership metric.** External MCP calls into Veritail; partner-built workflows live; third-party tools integrated.

### Bet 7 — The Unit-Economics Control Plane `(F-E · value-for-money as engineering · Phase 0→2)`
*Sharpens the PRD's cost-accounting stack and NFRs.*

- **What it is.** Value-for-money treated as an engineered system, not a hope: per-run token/tool capture from day one, **automatic model-tier routing** (economy models for extraction/classification/mapping; frontier models reserved for hard investigations — made safe by Bet 5), aggressive caching/batching, per-tenant budget caps and kill switches, and **cost-to-serve as a first-class live surface** (cost-per-investigation, cost-per-successful-sync, gross-margin-per-pack, onboarding-cost-per-tenant).
- **Why it is leadership.** This is what lets Veritail price at "fraction-of-an-analyst" with healthy, *expanding* margin. You cannot manage a value-for-money you do not measure; competitors who don't instrument cost-to-serve will misprice or bleed margin as workloads scale.
- **Frontier form.** Drive **cost-per-resolved-dollar down every quarter** and publish the falling curve as a customer-facing trust artifact (see §3.4).
- **Leadership metric.** Cost-per-investigation (↓); cost-per-successful-sync (↓); gross margin per pack; onboarding-cost-per-tenant (↓); **human-minutes-per-$-recovered (↓, sublinear to volume).**

### Capstone — The Regional Two-Sided Data Exchange `(F-I + F-O · the endgame · Phase 4)`
*Sharpens F-3.5 and §8.3.* The same distributors serve many brands; once both sides of a region are onboarded, **onboarding brand N approaches free**, and no competitor can replicate the position without having onboarded both sides. This is Crisp's network play, **in the geography Crisp cannot serve.** It is built only after the wedge is won, on the distributor-net-positive incentive design (§8.3 of the PRD) — free reconciliation back to the distributor, faster evidence-backed dispute resolution, less friction than emailing spreadsheets.

---

## 3. The value-for-money engine

Value-for-money = **value delivered ÷ price.** Veritail must win the numerator *and* the denominator — and mid-2026 economics let it win both at once.

### 3.1 The economic tailwind (why now is uniquely favorable)
On a *fixed* customer workload, LLMflation drops cost-per-investigation ~3–5x/year. That lets Veritail do something most software cannot do simultaneously: **cut price, expand margin, and reinvest in moats** — because its dominant variable cost is the one that is collapsing. The discipline is to *deliberately capture* the collapse (Bet 7) rather than let it leak.

### 3.2 The customer ROI model — *illustrative, validated in Phase 1*
Anchored to the PRD's own stated problem magnitudes, for a representative ICP brand (**~$100M revenue, 12 trading partners, 8-person commercial team**). **These are illustrative ranges to be validated against the anchor's real data; the Phase-1 gate requires ≥$X *resolved-as-genuine / recovered*, never "surfaced."**

| Value source | PRD basis | Illustrative annual value |
|---|---|---|
| Deduction leak recovered (disputed-and-won + prevented) | Deductions = 1–3% of revenue → $1.0–3.0M leaking; recover 15–35% | **$150K–$1.05M** |
| Trade-spend efficiency captured | Trade spend = 15–20% of revenue → $15–20M; capture 1–3% | **$150K–$600K** |
| Analyst time returned | 2–3 analyst-weeks/month ≈ 0.6–0.75 FTE freed | **$15K–$40K** |
| Faster decisions (week-2 vs quarterly) | Reduced OOS/overstock | *Qualitative, excluded from total* |
| **Total illustrative annual value** | | **~$315K–$1.69M** |

| Veritail annual cost (illustrative) | Model | Range |
|---|---|---|
| Platform fee (tiered by SKU) + 2 packs (fraction-of-analyst) + 12 connections | PRD §13 | **~$40K–$90K** |

> **Illustrative value-for-money ratio: every $1 paid to Veritail returns ~$4–$20 in recovered/resolved money** — dominated by money the customer's analysts currently *write off.* The headline is deliberately conservative because it counts only **resolved-as-genuine + recovered**, the PRD's hard currency, not "surfaced."

### 3.3 Time-to-value as a value-for-money lever
- **Value before subscription.** The **30-day Discrepancy Audit** pilot (land motion) quantifies the leak *with recovered-value proof* in 30 days — value-for-money is demonstrated before a subscription is signed.
- **Value-for-money that *improves* over the lifetime.** Because the assets compound, every subsequent pack and partner onboards **cheaper and faster** (Bet 1 teach-zero, Bet 4 memory, the mapping graph's "confirm once = applied forever"). **Onboarding-cost-per-tenant must fall** (PRD guardrail) — making this the rare product whose value/price ratio *rises* with tenure.

### 3.4 Pricing architecture, re-cut for value-for-money
Refines PRD §13 through the value lens:

1. **Price on value, not cost-plus.** The value metric is the **per-trading-partner connection** (it grows with the moat) plus the **per-pack** fee (anchored to a *fraction* of analyst headcount).
2. **Outcome kicker (% of recovered).** The purest value-for-money signal — the customer pays more *only when they get more.* Reserved for the Deductions pack; structured for target-jurisdiction legality (PRD open question 5).
3. **The self-proving value-for-money guarantee (novel — recommend adopting).** The same Verified Ledger that does the work **publishes the customer's recovered-vs-paid ratio in every monthly Brief**, audited and lineage-complete. Value-for-money stops being a sales claim and becomes a **product-proven, finance-signed fact.** The renewal slide writes itself, from the system of record. *No competitor that lacks the audit-grade ledger can make this guarantee.*
4. **The LLMflation dividend (recommend a hybrid posture).** As cost-per-investigation falls, **share part of the savings** with the customer (lower price-per-investigation, or more volume for the same price over the contract) and **bank part** as margin/moat reinvestment. A falling price is a retention weapon competitors on cost-plus pricing cannot match.

### 3.5 The cost stack, engineered (the denominator)
- **Dominant COGS:** investigations (frontier-model tokens) + portal syncs (computer-use compute). **Both are falling.**
- **Model-tier routing (Bet 7 + Bet 5):** economy models (~$0.10–0.40/M tokens) handle extraction, classification, and mapping; frontier models are reserved for genuinely hard investigations — and the eval gate makes every downgrade *safe*.
- **Memory cuts COGS (Bet 4):** as the Outcome Ledger and mapping graph deepen, agents re-derive less and retrieve more — tokens-per-investigation fall *faster* than raw model price.
- **Approval load held sublinear (F-7.7):** human-minutes-per-$-recovered must trend down, or the headcount-saving claim — the core of the value story — fails.

> **The value-for-money flywheel, in one sentence:** *the Outcome Ledger makes each investigation cheaper to run and more valuable to the customer at the same time* — denominator down, numerator up, from one compounding asset.

### 3.6 Value-for-money vs each competitor

| Competitor | Why Veritail is better value-for-money |
|---|---|
| **Crisp** | Enterprise/US-priced; harmonizes & recommends but **does not recover money**. Veritail *recovers* money in EM at mid-market price → higher value, lower price. |
| **Palantir Foundry** | Enterprise-priced, implementation-heavy (months, six-/seven-figure). Veritail is verticalized with a **30-day pilot** → an order-of-magnitude better value/price for mid-market. |
| **Deductions specialists** (HighRadius, Glimpse) | US-AR focused; don't serve EM retailers. Veritail's Deductions pack is **"free because the reconciled ledger already exists."** |
| **DMS/SFA** (BeatRoute, FieldAssist, Bizom) | They capture orders / run schemes; Veritail sits **on top as the verification layer** — net-new value, complementary not competing. |
| **Status quo** (Excel + analysts) | Veritail recovers the money analysts **write off**, at lower total cost than the analyst-weeks burned arguing about data. |

---

## 4. The unified flywheel (leadership × value-for-money, compounding)

```
        ┌──────────────────────────────────────────────────────────────┐
        │  LLMflation tailwind: compute per investigation ↓ 3–5x / year │
        └──────────────────────────────────────────────────────────────┘
                                   │ (cheaper to run the whole loop)
                                   ▼
  (1) No-API ingestion mesh  ──►  reaches data nobody else reaches
                                   │
                                   ▼
  (2) Finance-grade loop     ──►  resolves discrepancies, RECOVERS money
                                   │
              ┌────────────────────┼─────────────────────┐
              ▼                                            ▼
  (3) Recovered money         (4) Every resolution + outcome enriches
      PROVES ROI (value)          memory + mapping graph + portal registry
      and FUNDS expansion         (moats COMPOUND = leadership)
              │                                            │
              ▼                                            ▼
  (6) Better value-for-money  ◄── (5) Compounding assets LOWER COGS
      = faster adoption,           (memory ↓ tokens) and RAISE value
      more partners                (better agents) at the same time
              │                                            ▲
              └──────────────►  more partners = more data ─┘
                               + regional network density (endgame)
```

> **Synthesis:** *Veritail turns the collapsing cost of intelligence and the rising value of proprietary retail-commercial data into one compounding loop, where every dollar recovered makes the next dollar cheaper to recover and more valuable to the customer.* Leadership (moats compounding) and value-for-money (cost down, value up) are two readings of the same loop.

---

## 5. Execution overlay on the v2.0 roadmap

This **overlays** the PRD's phases — it does **not** reorder them. The wedge-first, two-packs-before-extraction, apex-features-sequenced-late discipline is preserved. Each phase names its **Leadership investment**, its **Value-for-money investment**, and the **gate that must hold.**

| Phase | Leadership investment (the bets) | Value-for-money investment | Gate (must hold — from PRD) |
|---|---|---|---|
| **0 · Foundations** (wk 0–8) | Eval harness skeleton (Bet 5 seed); bitemporal + action-ontology **schema designed-in** (Bets 2,3 — retrofitting later is expensive) | **Cost accounting from day one** (Bet 7 seed): per-run token/tool capture | Durable run survives a deploy; evals run in CI; tenant-schema migration verified on a prod copy |
| **1 · Reconciliation** (wk 8–30) | Ingestion mesh v1 (Bet 1: teach-mode + self-heal + tri-modal failover + drift sentinels + reliability instrumentation); bitemporal ledger + action-ontology **start** (Bets 2,3); **eval gate live** (Bet 5) | Cost-per-investigation + cost-per-sync **live**; 30-day Audit pilot motion; **value-for-money Brief prototype** (recovered-vs-paid) | Anchor closes a month-end on Veritail only; **≥$X resolved-as-genuine / recovered**; extraction/mapping SLOs met; **zero unaudited writes**; write-back security exercised once; **written wedge go/no-go** on portal reliability %/cost-per-sync |
| **2 · Deductions + extraction** (wk 30–44) | Outcome Ledger as memory **seeded** (Bet 4); continuous observability (Bet 5); scenario staging (Bet 3); tamper-evident audit **start** (Bet 2) | **Onboarding-cost-per-tenant measured & falling**; outcome-kicker pricing piloted; LLMflation dividend modeled | Deductions pack in **≤30% of Pack-1 effort**; first $ recovered; first renewal-quality outcome data (with causal caveat); onboarding cost trending down |
| **3 · Builder + ecosystem** (wk 44–64) | Two-way MCP semantic layer (Bet 6); cross-tenant portal registry → **teach-zero** (Bet 1 apex form); tamper-evident audit **GA** (Bet 2) | Partner-built packs (others build value *on* the platform = leverage); template gallery (cheaper expansion) | A non-engineer ships a working custom workflow; pack #3 live |
| **4 · Network** (mo ~15+) | Regional two-sided data exchange (capstone); consented cross-tenant mapping priors; outcome-driven recommendations | Marginal onboarding cost → **near-zero for brand N** on an onboarded partner | First distributor reused for a second brand; portal **net-positive for the distributor** independent of the brand's audit use |

**The three priority apex features, sequenced (PRD open question 11) — recommendation:** build **action-centric ontology + bitemporal ledger first** (Phase 1 — they are the trust spine and are expensive to retrofit); **seed outcome-memory in Phase 2** (it needs history to accrue — start the clock early, sell it only once it exists); **tamper-evident audit in Phase 2→3** (it converts the tool into infrastructure once a finance audit is in sight). Earn each against paying-customer pull.

---

## 6. The scoreboards — how we know we are leading and worth it

### 6.1 Technology-leadership scoreboard (per frontier)

| Frontier | Leading indicators |
|---|---|
| **Ingestion (F-I)** | Portals in cross-tenant registry; per-portal reliability %; **cost-per-successful-sync (↓)**; teach-zero onboarding rate |
| **Trust (F-T)** | Brief numeric factuality = 100%; audit completeness = 100%; **zero-wrong-number streak (days)**; finance sign-off rate; system-of-record gravity (% of money decisions through Veritail) |
| **Outcome (F-O)** | Cumulative outcome-pair depth; **investigation-acceptance % (↑ over time)**; recommendation precision; tokens-per-investigation (↓) |
| **Reliability / eval** | Eval SLOs green; **model-swap latency (days, ↓)**; production-audit pass rate |
| **Ecosystem** | External MCP calls into Veritail; partner-built workflows live |

### 6.2 Value-for-money scoreboard

| Metric | Target direction |
|---|---|
| **Recovered-vs-paid ratio per tenant** (the north-star value number, **audited via the ledger**) | ↑ — published monthly in the Brief |
| Cost-per-investigation; cost-per-successful-sync | ↓ every quarter |
| Gross margin per pack | ↑ / held at floor |
| Onboarding-cost-per-tenant | **↓ (the product-vs-consultancy fork)** |
| Human-minutes-per-$-recovered | ↓, **sublinear to volume** |
| Subscription payback period (from recovered money) | **< 1–2 months** |
| Net revenue retention | ↑ |

**Trust guardrails (non-negotiable, from the PRD):** brief numeric factuality = 100%; eval SLOs green; zero unapproved external actions; audit completeness = 100%. *A single wrong number in front of a CFO is existential — every leadership and value metric above is forfeit if a guardrail breaks.*

---

## 7. Risks specific to this ultraplan

| Risk | Severity | Mitigation |
|---|---|---|
| **Tech-leadership chase outruns wedge proof** | High | Apex bets sequenced as later-stage (§5); **Phase-1 exit criteria sacrosanct**; per-pack ROI gating; "apex through the wedge, never around it" |
| **LLMflation stalls / reverses** | Med-High | Even at today's prices Veritail is cheaper than analysts; model-tier routing + caching + memory cut tokens independent of price; never price below a cost-plus floor |
| **Over-claiming value-for-money (ROI)** | Med-High | Count only **resolved-as-genuine + recovered**, never "surfaced"; recovered-vs-paid ratio is **ledger-audited**; causal honesty ("associated with," never "caused") |
| **Computer-use never reaches finance-grade on some portals** | High | Inbox/file **first-class** fallback; per-portal reliability floor + **written go/no-go**; a portal below floor auto-routes to "request by email" |
| **Memory moat slow to compound** | Med | It is a Phase-2+ payoff by design — **start the clock early, sell it only once real**; don't price it before it exists |
| **"Infrastructure others build on" cannibalizes packs** | Med | MCP exposure is additive, governed, and metered; the **resolution-and-recovery loop stays proprietary** — share the read, keep the engine |
| **Crisp moves into resolution/recovery** | High | Compete only at the two ends; Crisp's US-data + recommendation core is built for neither no-API EM ingestion nor an approval-gated recovery loop; outcome ledger + regional network compound faster than it can re-platform |
| **Anchor overfit / off-ICP** | Med | Second design partner by Phase 2; onboarding-cost-per-tenant must fall; anchor confirmed ICP-fit before Phase-1 build |

---

## 8. Decisions to make now (action-oriented; extends PRD §19)

Each carries a **recommendation**, not just a question.

1. **Adopt the "own the ends, rent the middle" engineering allocation explicitly.** *Recommend:* ring-fence a fixed majority of engineering capacity for Bets 1–4 (the two ends + memory + trust spine); cap investment in the commodity middle to integration-and-glue only.
2. **Sequence the three priority apex features (PRD Q11).** *Recommend:* action-ontology + bitemporal ledger in **Phase 1**; outcome-memory seeded in **Phase 2**; tamper-evident audit **Phase 2→3** — as in §5.
3. **Set the wedge go/no-go floors (PRD Q9).** *Recommend:* a starting bar of **≥95% per-portal reliability** and a **declining cost-per-successful-sync trend** over Phase 1; below floor → inbox/file fallback. Confirm exact numbers with the anchor.
4. **Commit to the self-proving value-for-money Brief (§3.4.3).** *Recommend:* **yes** — ship the ledger-audited recovered-vs-paid ratio as a first-class monthly artifact from Phase 1. It is the single strongest value-for-money and retention asset, and only Veritail's audit-grade ledger can produce it.
5. **Set the LLMflation-dividend posture (§3.4.4).** *Recommend:* **hybrid** — share part of the falling cost with customers (retention) and bank part (margin/moat reinvestment).
6. **Set the gross-margin floor per pack and the cost-per-investigation budget (PRD Q8).** *Recommend:* fix both before Phase-2 pricing; make them release-gated like the accuracy SLOs.
7. **Resolve the anchor's ICP-fit (PRD Q1 — build-blocker).** *Recommend:* confirm the anchor resembles the $20M–$500M mid-market ICP **before** Phase-1 build commits; if enterprise-scale, add a second ICP-true design partner in parallel.

---

## 9. The one paragraph to remember

The cost of intelligence is collapsing and the architectural middle is now everyone's. In that world, racing on models or on the lakehouse-to-MCP stack is racing toward zero. **Veritail's leadership and its value-for-money come from the same three assets compute cannot replicate — the no-API ingestion library, the finance-grade resolution-and-recovery loop, and the multi-year outcome memory — wired into one flywheel where every recovered dollar makes the next one cheaper to recover and more valuable to the customer.** Build those, capture the LLMflation dividend deliberately, prove the value-for-money out of the audit-grade ledger itself, and hold the trust gates above all. That is how Veritail becomes the un-catchable standard *and* the best value for money in retail commercial operations — reached through the wedge, never around it.

---

## Appendix A — Evidence base (mid-2026)

*Competitive and market grounding for the claims above. External sources; read with the PRD's own analysis.*

- **LLMflation / inference-cost collapse:** a16z, *Welcome to LLMflation* (https://a16z.com/llmflation-llm-inference-cost/); Epoch AI, *LLM inference price trends* (https://epoch.ai/data-insights/llm-inference-price-trends). ~90%+ decline since 2023; ~3–5x/yr through 2027; economy models ~$0.10–0.40 / M tokens (mid-2026).
- **Crisp (primary threat) — capabilities & limits:** *Crisp Launches AI Agents* (https://www.businesswire.com/news/home/20260211212237/en/Crisp-Launches-AI-Agents-to-Drive-Shareholder-Value-for-CPG-Brands-and-Retailers); *Crisp Announces AI Master Data* (https://www.businesswire.com/news/home/20260203584899/en/); *AI-Powered Master Data Management* (https://www.gocrisp.com/masterdata). Confirms US-retailer data harmonization + recommendation focus, and that AI Master Data ≈ the SKU Mapping Graph concept.
- **Palantir Foundry / AIP (apex reference / architecture validator):** *Foundry platform summary* (https://www.palantir.com/docs/foundry/getting-started/foundry-platform-summary-llm); *AIP overview* (https://www.palantir.com/docs/foundry/aip/overview). Ontology + AIP agents that "propose and execute decisions and write results back into operational systems"; enterprise-priced, implementation-heavy.
- **Computer-use / browser-agent reliability (the wedge):** WebArena Verified (https://github.com/ServiceNow/webarena-verified); *UI-CUBE: operational reliability beyond task accuracy* (https://arxiv.org/pdf/2511.17131); Browser Use benchmark (https://browser-use.com/posts/ai-browser-agent-benchmark). Leading agents ~58% WebArena / ~87–89% WebVoyager — economically viable, not finance-grade alone.
- **MCP / semantic-layer as table stakes:** *MCP for enterprise AI integration* (https://www.strategy.com/software/blog/model-context-protocol-mcp-for-enterprise-ai-integration); *Semantic Layer for Enterprise AI in 2026* (https://www.strategy.com/software/blog/semantic-layer-for-enterprise-ai-in-2026-what-production-use-requires). MCP on 10,000+ enterprise servers by April 2026; semantic layer exposed over MCP is the governance pattern.

*End of ULTRAPLAN UP-1.0. This plan is subordinate to the PRD v2.0 trust gates. The apex is reached through the wedge, never around it. When timeline and trust gate conflict, the timeline yields.*
