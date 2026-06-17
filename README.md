# Veritail — Product Requirements Document

**The Retail Commercial-Operations Platform → the Retail Agent OS**
*Version 2.0 — June 2026. Owner: TMLC Solutions.*

> **What v2.0 is.** A full recreation that keeps the v1.2 spine and trust discipline, then folds in three things developed since: (1) a sharpened competitive position — reconciliation-first wedge, Crisp as the primary named threat, the emerging-market DMS/SFA lane, Palantir Foundry as the apex "build-it-yourself" tier, and the SAP API-policy tailwind; (2) an explicit **apex (category-leadership) thesis** — how Veritail ascends from a vertical product to the un-replicable standard for retail commercial operations; and (3) the **apex-grade technical architecture** that ascent requires, sequenced across the roadmap. Apex-grade features (later-stage, frontier investments rather than foundational) are tagged **[A]**. Priority tags `P0/P1/P2` are unchanged in meaning.
>
> **Unchanged and hardened:** the three trust gates — ledger-templated numbers, two-packs-before-extraction, no silent writes. When timeline and gate conflict, the timeline yields.

---

## 0. Changelog from v1.2 → v2.0

| # | Change | Where |
|---|---|---|
| 1 | Positioning reframed: **reconciliation-first**, "recover money from data nobody else can reach, with finance signing off" | §1, §2.3 |
| 2 | Competitive map rebuilt around real 2026 players, by lane; **Crisp named the primary threat** | §2.3 |
| 3 | Emerging-market **DMS/SFA lane added** (BeatRoute, FieldAssist, Bizom) — the in-region incumbents v1.2 missed | §2.3 |
| 4 | **Palantir Foundry positioned as the apex / enterprise build-it-yourself tier** (architecture validator, not wedge competitor) | §2.3, §2.6 |
| 5 | **SKU Mapping Graph downgraded** from novel moat to regionally-specialized asset (Crisp ships AI Master Data) | §2.4, §6.3 |
| 6 | **SAP API-policy tailwind** added (validates the extract-to-governed-ledger architecture) | §2.2, §2.4 |
| 7 | Defensibility narrowed to the three genuinely un-copyable things: no-API ingestion, finance-grade resolution loop, compounding moats | §2.4 |
| 8 | New section: **the apex thesis** — five ascent levers (system-of-record gravity, moat compounding, trust, two-sided network, OS expansion) | §15 |
| 9 | **Apex-grade technical architecture** added and tagged `[A]` across the fabric/runtime/network layers | §6–§9 |
| 10 | Roadmap annotated with **apex investments per phase** (foundational vs later frontier) | §14 |
| 11 | Carries forward all 15 v1.2 changes (timeline rebuild, recovered-not-surfaced exit, approval-load metric, COGS, write-back security, causal-honesty on outcomes, etc.) | throughout |

---

## 1. Product Vision

**One-liner:** A digital commercial team for retail — AI agents that connect to your ERP and every trading partner (even the ones with no API), maintain one verified version of your numbers, investigate every gap, draft every fix, and measure whether it worked. Humans approve; agents do the work.

**Positioning (sell this, not "AI"):** *We recover and resolve the money leaking through your commercial operations — by reconciling the messy distributor and retailer data nobody else can reach, finding the genuine gaps, drafting evidence-backed actions, and giving finance an audit-ready ledger of what was recovered.*

**The platform thesis:** Every retail/FMCG commercial workflow — reconciliation, deductions, trade spend, demand planning, pricing, field execution — is the same loop on the same entities:

> **Sense** (messy multi-source data) → **Investigate** (why is this number off?) → **Decide** (human approval) → **Act** (write back to ERP / email / portal) → **Measure** (did it work?)

Veritail builds that loop **once** as shared infrastructure (the Retail Fabric + Agent Runtime) and ships workflows as configurable agent "employees" (Workflow Packs), with a domain-specific Workflow Builder that lets partners compose new workflows from retail-native blocks.

**What it is not:** a BI tool, a dashboard product, a generic automation platform, or a chatbot over data. The dashboard is the appendix; the work product is the product.

---

## 2. Problem, Market & Competition

### 2.1 The problem

Mid-market FMCG brands and distributors run commercial operations on:
- **Conflicting numbers.** Sell-in (ERP) and sell-out (portals, emailed Excel, PDFs) never agree. Teams burn 2–3 analyst-weeks/month collecting and arguing about data.
- **Unmanaged money leaks.** Retailer deductions (1–3% of revenue) and unmeasured trade spend (15–20%) are written off.
- **Reactive operations.** Problems surface at the quarterly post-mortem, not in week 2 when they were fixable.
- **No closed loop.** Actions are taken; nobody measures whether they worked.

### 2.2 Why now

- **Computer-use and document agents** make the no-API long tail (portals, emailed spreadsheets, PDFs) economically solvable for the first time. This is the wedge — but it remains a *bet to validate with hard reliability/cost numbers in Phase 1*, not an assumed moat.
- **Conversational BI is commoditized** (Power BI Copilot, Tableau Pulse, ThoughtSpot). Differentiation moved from "answers questions" to "does the job."
- **The agentic-data-platform pattern is now mainstream direction** — semantic/knowledge layer + MCP + agents — so Veritail's architecture rides real 2026 infrastructure (MCP became the default agent-to-data bridge by mid-2026).
- **Tailwind — ERPs are locking agents out.** SAP's April 2026 API policy prohibits third-party AI agents from operating directly on SAP APIs; the prescribed fix is to *extract once into a governed downstream source of truth and let agents consume from there*. That is precisely Veritail's Verified Ledger architecture — now validated by the industry's largest ERP vendor's own policy.
- **Target markets (Gulf, India, Africa, SEA)** are distributor-heavy with thin Nielsen/Circana coverage — incumbents are structurally weakest where the pain is sharpest.

### 2.3 Competition (by lane)

Veritail competes in several distinct lanes; its real risk profile differs by lane.

| Lane | Strongest players (2026) | Threat | How Veritail must position |
|---|---|---|---|
| **Retail data platforms** | **Crisp** (primary threat), Stackline | **High** | "We don't just harmonize data and recommend — we *resolve* discrepancies and recover money, in the no-API geography Crisp doesn't serve." |
| **Deductions / recovery specialists** | Glimpse, HighRadius, CommerceIQ, ValenceIntel, Transformance | **Med-High** | "Deductions is one downstream pack, free because we already hold the reconciled ledger — never our identity, never benchmarked against US-retailer AR specialists." |
| **Emerging-market DMS/SFA** | BeatRoute, FieldAssist, Bizom | **Med-High** (in-region) | "We sit *on top of* your DMS as the verification layer — we don't capture orders or run schemes." |
| **Enterprise RGM/TPM** | Salesforce CG Cloud, SAP RGM, o9, Visualfabriq, RELEX | **High** (enterprise) | "Faster, lighter, mid-market, distributor-heavy, messy-data first." |
| **Apex / build-it-yourself** | **Palantir Foundry / AIP** | **Low (wedge), High (top-of-market)** | "The architecture validator, not a wedge competitor — Foundry is enterprise-priced and implementation-heavy; we're the verticalized, mid-market-accessible instance." |
| **BI copilots** | Power BI, Tableau Pulse, ThoughtSpot | **Medium** | "They answer questions; we do the work." |
| **Generic agent builders** | n8n, Zapier Agents, Copilot Studio | **Medium** | "They give you nodes; we give you retail-commercial employees." |
| **Status quo** | Excel + analysts + email | **Very High** | "30-day discrepancy audit with recovered-value proof." |

**Crisp — the primary threat, read precisely.** Crisp is a well-funded ($135M+ raised, ~320 staff, ~$25M revenue, 6,000+ customers including 80+ of the top-100 CPG brands), launched AI Agents in GA (Feb 2026) that go beyond reporting to recommend order/display/promo actions, and shipped AI Master Data — a human-in-the-loop product-mapping solution that is functionally Veritail's SKU Mapping Graph. Two facts follow: (1) the mapping graph is **not a novel moat** — Crisp already ships it; (2) Crisp's leadership is in **US retailer POS/inventory data harmonization plus recommendations**, *not* the no-API distributor long tail or an approval-gated resolution-and-recovery loop. Veritail's defensible space is exactly the two ends Crisp is not built for (see §2.5).

### 2.4 Defensibility — narrowed and honest

The moat is never the AI, and (as of v2.0) it is **not** the mapping graph or the semantic layer either — both are now industry-standard (Crisp, Foundry). What actually compounds and cannot be easily copied:

1. **No-API ingestion of the long tail** — every distributor/retailer portal taught to an agent (the connector/portal library) is unscalable grunt work competitors must repeat; in the target geographies, few even try.
2. **Finance-grade resolution-and-recovery loop** — approval-gated, audited, recovery-measured. Crisp recommends; the recovery specialists work US AR; nobody runs this loop in the distributor-heavy markets.
3. **Outcome Ledger** — measured intervention→outcome *associations* (causal caveats per §7.4); a track record new entrants start at zero on. This is the real capability gap.
4. **Regional two-sided network (endgame)** — the same distributors serve many brands; onboarding compounds within a region. This is the closest thing to an un-breachable position available.
5. **System-of-record gravity** — once finance defends Veritail's numbers in an audit, it is infrastructure, not a tool.

*Downgraded:* the SKU Mapping Graph is retained as a first-class capability but is a **regionally-specialized** asset, not a novel moat — within-tenant from day one, cross-tenant only at Phase 4, and already matched in concept by Crisp.

### 2.5 Where Veritail wins vs Crisp (layer by layer)

The two stacks are near-identical in the middle and diverge only at the ends:
- **Ingestion (diverges):** Crisp ingests 40+ integrated US retailer POS feeds; Veritail ingests no-API portals, inboxes, files.
- **Foundation / store (overlaps):** both cleanse and model a data foundation; Veritail's is finance-grade (immutable, provenance + confidence).
- **Semantic / knowledge layer (overlaps):** Crisp's Retail Knowledge Graph + AI Master Data ≈ Veritail's ontology + mapping graph + ledger. Not a differentiator.
- **Governance (diverges):** Crisp has data governance; Veritail has finance-grade approval + tamper-evident audit.
- **Agent interface (overlaps):** both expose agentic access (Crisp via Gemini, Veritail via MCP).
- **Agent purpose (diverges):** Crisp *recommends and optimizes* (assortment, displays, promos); Veritail *resolves and recovers* (disputes, recovery, approval-gated). **This is the decisive divergence.**

**Rule:** compete at the two ends (data Crisp can't reach; the resolution-and-recovery loop Crisp doesn't run). Never on the middle.

### 2.6 The apex reference point — Palantir Foundry

Foundry/AIP is the most mature instance of the agentic-data-platform pattern: an action-centric **Ontology** that models entities *and the decisions/actions on them*, stages actions as governed scenarios, and writes them back with full lineage and audit — deployed in the highest-stakes settings. It is not a wedge competitor (enterprise-priced, implementation-heavy, industry-agnostic), but it is the **architecture Veritail's design most resembles** and the proof that the apex is built on exactly Veritail's bones: ontology + actions + audit + writeback. Veritail's ambition (§15) is to be the *verticalized, mid-market-accessible* apex for retail commercial operations — "the Mythos of retail" reached through the wedge, not around it.

---

## 3. Target Users & Personas

**ICP (initial):** Mid-market FMCG brands ($20M–$500M) and large distributors in distributor-heavy markets (GCC first, then India/SEA/Africa). 50–5,000 SKUs, 3–50 trading partners, commercial team of 5–50.

**ICP discipline:** the anchor design partner must resemble this ICP. If the anchor is enterprise-scale, the build risks overfitting off-ICP — resolve before Phase 1 build commits (§18).

| Persona | Role in product | Primary surface |
|---|---|---|
| **Commercial Director / Head of Sales** (economic buyer) | Reads the brief, approves big-ticket actions, owns the number | Monday Brief |
| **Commercial / Sales Analyst** (daily user) | Reviews investigations, resolves mapping & reconciliation queues | Approval Queue, Ledger |
| **Finance Controller** (veto holder) | Trusts/audits the verified numbers, signs off on deductions | Verified Ledger, audit trail |
| **Key Account Manager** | Receives drafted partner escalations, approves sends | Approval Queue (mobile) |
| **IT / Data lead** (gatekeeper) | Manages connections, credentials, security review | Admin console |
| **Partner consultant (TMLC + others)** | Onboards clients, builds custom Workflow Packs | Workflow Builder |
| **Distributor user** (Phase 4) | Reports data, responds to discrepancy queries | Partner Portal |

---

## 4. Product Principles

1. **Work product over dashboards.** Every feature ends in completed or drafted work, not a chart.
2. **Show the work.** Every agent conclusion ships with its evidence: queries run, sources checked, what was ruled out, confidence.
3. **Humans approve consequences.** Any externally visible or financially material action passes an approval gate. No silent writes, ever.
4. **One number, audit-trailed.** Every figure traces to sources and resolution decisions. One hallucinated number in front of a CFO kills the product.
5. **Build the pack by hand, extract the platform.** Primitives are discovered from shipped workflows, not designed speculatively.
6. **Boring infrastructure, modern agents.** Durable execution, idempotent writes, typed schemas underneath; agentic flexibility on top.
7. **Protect the trust gates above all.** When timeline and gate conflict, the timeline yields. A shipped date is recoverable; a CFO who caught a wrong number is not.
8. **Differentiate at the ends, ride the standard in the middle.** Invest engineering in the two things only Veritail does (no-API ingestion; the resolution-and-recovery loop). Rent/adopt the commodity middle (lakehouse, semantic-layer plumbing, MCP, computer-use infra).

---

## 5. System Architecture

```
┌────────────────────────────────────────────────────────────────────┐
│ LAYER 3 — WORKFLOW PACKS & BUILDER                                  │
│  Reconciliation Analyst · Deductions Auditor · Trade Spend Auditor  │
│  Demand Planner · Pricing Analyst · Field Exec · Launch · E-comm    │
│  Workflow Builder (retail-native blocks) · Pack SDK                 │
├────────────────────────────────────────────────────────────────────┤
│ LAYER 2 — AGENT RUNTIME                                             │
│  Durable agent runs · Investigation engine · Approval Queue ·       │
│  Audit Trail · Outcome Ledger (agent memory) · Brief Generator ·    │
│  Eval Harness · Agent observability · Notification fabric           │
├────────────────────────────────────────────────────────────────────┤
│ LAYER 1 — RETAIL FABRIC                                             │
│  Connector Fabric (MCP: API/portal/inbox/file/write-back) ·         │
│  Action-centric Retail Ontology · SKU Mapping Graph ·               │
│  Verified Ledger (reconciled, bitemporal, source-traceable)         │
├────────────────────────────────────────────────────────────────────┤
│ FOUNDATIONS — Multi-tenancy · RBAC · Secrets vault · Observability  │
│  · Event bus · Job scheduler · Cost accounting                      │
└────────────────────────────────────────────────────────────────────┘
```

This is, deliberately, the industry-standard agentic-data-platform pattern (lakehouse → semantic/ontology layer → governance → MCP → agents). Four of those layers are now table stakes; Veritail's divergence lives only in the bottom layer (ingesting data nobody else reaches) and the top (the resolution-and-recovery agent loop). The apex investments (§6–§9, tagged `[A]`) deepen exactly those two ends plus the trust spine.

### 5.1 Tech stack

| Component | Choice | Rationale |
|---|---|---|
| Backend | Node.js + TypeScript + Express/Fastify | Continuity with team & codebase |
| Database | PostgreSQL + Prisma | Sound schema spine; extend it |
| Durable execution | Temporal (or equivalent) | Multi-day agent runs; checkpoints, retries, resumability are non-negotiable |
| Agent framework | Claude Agent SDK (primary), provider-abstracted | Tool-use over DB/connectors |
| Connectors | MCP servers, one per source type | Two-way interop is the standard |
| Portal automation | Computer-use agent in sandboxed browser workers | The no-API long tail is the wedge — **rent the commodity computer-use layer, build the learned-navigation library** |
| Document parsing | LLM extraction + schema validation + confidence | Distributor files are wildly inconsistent |
| Frontend | React + TS + Vite, React Router, token persistence | Reuse shell; fix auth/routing debt |
| Builder canvas | React Flow over block registry (Phase 3) | Avoid generic-engine lock-in |
| Evals | Golden-set suite in CI; accuracy SLO | Release gate, not afterthought |
| Cost accounting | Per-run token/tool capture; model-tier routing | "Fraction-of-analyst" pricing requires measured COGS from day one |

### 5.2 Carryover from RetailPulse

- **Keep & extend:** Prisma schema spine → Ledger; multi-tenant model; status logic; React shell; SSE streaming.
- **Rebuild:** connectors (simulated → agentic MCP servers); chat (prompt-stuffing → grounded tool-use agent); reconciliation (auto-average → investigate + approve).
- **Add:** ontology + actions; mapping graph; approval queue; audit trail; outcome ledger; agent run store; brief generator; eval harness; builder registry.
- **Delete:** seeded `aiInsights`; simulated-connector data; landing-page claims not yet true (SOC 2, SSO, SLA).

---

## 6. Layer 1 — Retail Fabric

### 6.1 Connector Fabric (the wedge — must be best-in-world)

Four connector classes, each an MCP server exposing typed tools (`fetch_data`, `test_connection`, `write_back`).

| Class | Mechanism | Priority |
|---|---|---|
| **API** | SAP OData, Oracle Retail, e-commerce APIs | P0 (one real ERP path) |
| **Portal** | Computer-use agent in sandboxed browser; learned navigation cached; self-heals | P0 (the wedge) |
| **Inbox** | Per-tenant ingest address; LLM extraction → schema validation → quarantine | P0 |
| **File** | Upload, ontology-aware extraction | P0 (exists) |

- **F-1.1 (P0)** Per-tenant connector registry: type, vault-stored credentials, schedule, health, fetch window.
- **F-1.2 (P0)** Every fetched record → immutable `SourceRecord` with full provenance + extraction confidence.
- **F-1.3 (P0)** Confidence scoring; sub-threshold records route to human review, never silently into the ledger.
- **F-1.4 (P0)** Durable sync jobs: per-record error capture, retry policy, human-readable sync log.
- **F-1.5 (P1)** Write-back tools (email, ERP posting, portal submission) — all require an approved `Action`; idempotency keys mandatory.
- **F-1.6 (P1)** Portal "teach mode": human navigates once, agent records, replays, self-heals; re-teach fallback.
- **F-1.8 (P0)** **Portal reliability instrumentation** — per sync: success/fail, self-heal events, re-teach events, latency, fully-loaded cost. Surfaced as per-portal reliability % and cost-per-successful-sync; a Phase-1 go/no-go input.
- **F-1.9 (P0)** **Inbox/file as first-class** — production-quality on their own; a portal below its reliability floor auto-routes to "request by email."
- **F-1.10 (P0)** **Write-back security profile** — separate least-privilege write credentials per surface; irreversible writes forced to top approval tier; all write-backs idempotency-keyed, rate-limited, audit-logged with approver + evidence version; read-only default elsewhere; pen test before production posting.
- **F-1.11 (P2) [A] Cross-tenant portal-definition registry** — versioned, parameterized navigation artifacts (DOM/visual fingerprints) shared across tenants with per-tenant credentials, with automatic UI-drift detection and re-teach triggering. *This is the connector library as a compounding, code-level asset — the apex form of moat #1.*

**Acceptance (V1):** one ERP, two portals, one inbox; 95%+ records ingest untouched; every ledger number traces to source in two clicks; each live portal reports measured reliability % and cost-per-sync with a written wedge go/no-go.

### 6.2 Retail Ontology (action-centric)

Canonical, tenant-scoped entities: `SKU · TradingPartner · Location · Target · Promo · Order/Shipment · SalesFact · Claim/Deduction · PriceRecord · InventorySnapshot`.

- **F-2.1 (P0)** All entities tenant-scoped with compound keys (fixes global-SKU-ID collision).
- **F-2.2 (P0)** Period model: monthly P0; weekly P1; fiscal-calendar P2.
- **F-2.3 (P0)** V1 ships SKU, TradingPartner, Target, SalesFact, Order; rest added by the pack that needs them — but namespace/FK conventions designed now.
- **F-2.4 (P1)** Entity versioning: targets and prices time-ranged, never overwritten.
- **F-2.5 (P1) [A] Action-centric ontology** — entities carry typed `Action` definitions (resolve, dispute, post, notify) bound to them, each with required role/risk tier, reversibility flag, and writeback target. *This is the Foundry-grade move that turns the ontology from a data model into a system of record; it is the technical foundation of system-of-record gravity (§15).*

### 6.3 SKU Mapping Graph (regionally-specialized asset — not a novel moat)

- **F-3.1 (P0)** Mapping store: `(tenant, partner, raw_code, raw_description) → canonical SKU`, with status, confidence, who/when.
- **F-3.2 (P0)** Agent-proposed mappings on every new raw code (embedding + fuzzy + pack-size logic), one-click human confirm. Confirmed once = applied forever.
- **F-3.3 (P0)** Unmapped records quarantine; nothing enters the ledger unmapped.
- **F-3.4 (P1)** Mapping analytics: coverage %, confirmation rate, drift alerts.
- **F-3.5 (P2) [A]** Consented cross-tenant anonymized priors — the regional network effect, in code. *Phase 4. The within-tenant flywheel is real from day one; cross-tenant does not exist until this ships, and Crisp's AI Master Data already matches the concept — so message this as regional specialization, not novelty.*
- **F-3.6 (P1) [A]** Active-learning loop: every confirmation/rejection retrains the proposal model; precision is the release-gated metric, not throughput.

**Acceptance:** new 200-code file → ≥80% auto-proposed correctly; analyst confirms in <15 min (raise the time budget before the auto-apply rate if confident-wrong errors aren't easy to catch); second file from same partner needs zero touches.

### 6.4 Verified Ledger (system of record)

- **F-4.1 (P0)** `LedgerFact` = (tenant, entity, SKU, partner/channel, period, metric, value, status, source set, resolution ref).
- **F-4.2 (P0)** Conflict detection: ≥2 sources, variance > threshold (default 5%) → `disputed` + Investigation. No silent averaging.
- **F-4.3 (P0)** Resolution writes back with method + approver identity.
- **F-4.4 (P0)** Immutability: corrections are new versions; "as-reported" vs "as-resolved" views.
- **F-4.5 (P1)** Source authority weights as the investigation's prior, not an auto-decision.
- **F-4.6 (P1)** Ledger export: CSV/Excel + API, finance-grade.
- **F-4.7 (P1) [A] Bitemporal ledger** — every fact versioned across valid-time *and* system-time, so any number is reconstructable as-of any past moment. *Audit-defensible, finance-grade, and the technical basis for trusting the ledger in disputes.*

---

## 7. Layer 2 — Agent Runtime

### 7.1 Durable Agent Runs

- **F-5.1 (P0)** Every agent task is a durable run: checkpointed, resumable after crash/deploy, full step trace (tool calls, I/O, tokens, cost).
- **F-5.2 (P0)** Runs pause on external events (approval, partner reply, scheduled wake) for days without losing state.
- **F-5.3 (P0)** Per-tenant concurrency limits, cost budgets, kill switch.
- **F-5.4 (P1)** Run replay/debug view.
- **F-5.5 (P1) [A]** Deterministic re-execution / replay for audit and regression — re-run a historical investigation against pinned inputs and confirm identical findings.

### 7.2 Investigation Engine

- **F-6.1 (P0)** Triggers: ledger conflict (auto), target miss (auto), user request (manual), pack-defined.
- **F-6.2 (P0)** Output schema: question, finding, confidence (with basis), evidence list, hypotheses ruled out, recommended action(s).
- **F-6.3 (P0)** Toolset: typed read-tools over ledger/ontology, source-record drill-down, seasonality baseline; pack-extendable.
- **F-6.4 (P0)** "Show the work" UI: every investigation renders its evidence trail.
- **F-6.5 (P0)** `unresolved_pending_external` terminal state — when data alone can't determine truth, the agent does not guess; it drafts a partner query (via Approval Queue) and pauses on reply. Report time-to-surface (fast) and time-to-resolve (partner-reply-bound) separately.
- **F-6.6 (P1)** Investigations can request external info via drafted partner comms.
- **F-6.7 (P1)** Quality feedback (correct/incorrect/partial) → feeds eval set and Outcome Ledger.

### 7.3 Action & Approval System

- **F-7.1 (P0)** `Action` object: type, payload, evidence link, risk tier, state machine (`drafted → pending_approval → approved → executing → executed | failed → verified`).
- **F-7.2 (P0)** Approval Queue UI: grouped by workflow + risk tier; evidence inline; approve / edit-then-approve / reject-with-reason; bulk approve for low-risk.
- **F-7.3 (P0)** Policy engine: auto-execute (none by default) / single approval / role-specific (finance for disputes above $X); per-tenant configurable; irreversible writes forced to top tier.
- **F-7.4 (P0)** Audit trail: every transition recorded (who/what/when/evidence version) — append-only, exportable.
- **F-7.5 (P1)** Mobile approval surface.
- **F-7.6 (P1)** Escalation & expiry: unapproved actions nag, escalate, expire safely.
- **F-7.7 (P0)** **Approval-load accounting** — human-minutes per approval; approvals-per-analyst-per-day and human-minutes-per-$-recovered exposed. Must trend sublinear to volume or the headcount-saving claim fails.
- **F-7.8 (P1) [A] Scenario staging / branching** — proposed resolutions and actions staged against a branch of the ledger; what-if runs; merge only on approval. *Lets agents propose consequential actions safely; the Foundry-grade scenario primitive.*
- **F-7.9 (P2) [A] Tamper-evident audit** — hash-chained / cryptographically verifiable append-only log, so auditors can trust the record absolutely. *Apex-grade trust; converts tool into infrastructure.*

### 7.4 Outcome Ledger (moat #3 + agent memory)

- **F-8.1 (P1)** On execution, register a measurement plan: metric, baseline window, measurement window (default 4 weeks), expected direction.
- **F-8.2 (P1)** Scheduled measurement computes observed effect vs baseline (seasonality-adjusted) → `Outcome` (action, context fingerprint, effect size, confidence). **Causal honesty: no control group ⇒ record an *association*, note confounders, prefer quasi-experimental framing; all copy says "associated with," never "caused."**
- **F-8.3 (P2)** Recommendation engine: "in similar contexts, this action class was associated with +X% (n=Y)."
- **F-8.4 (P2)** Tenant-facing track record (with causal caveat) — the renewal slide.
- **F-8.5 (P2) [A] Outcome Ledger as agent long-term memory** — context-fingerprinted outcomes retrieved into future agent reasoning. *This is the capability gap a new entrant cannot match (no history); the technical core of the un-replicable moat.*

### 7.5 Brief Generator

- **F-9.1 (P0)** Scheduled per-tenant brief (weekly default; daily P1): what changed (seasonality-aware), why (linked investigations), what I did, what needs you, what I'm watching. Every claim links to evidence.
- **F-9.2 (P0)** Delivery: in-app + email; default landing surface after login.
- **F-9.3 (P1)** Role-scoped briefs.
- **F-9.4 (P2)** Conversational follow-up grounded in the ledger.

### 7.6 Eval Harness + Agent Observability (release gate)

- **F-10.1 (P0)** Golden datasets: extraction accuracy, mapping precision/recall, investigation-finding correctness, brief numeric factuality.
- **F-10.2 (P0)** CI gate: no prompt/model change ships below SLO (extraction ≥98% field accuracy; mapping precision ≥95%; brief numeric factuality = 100%, ledger-templated).
- **F-10.3 (P1)** Production sampling: % of live investigations human-audited weekly; drift dashboard.
- **F-10.4 (P1) [A] Continuous agent observability** — per-investigation scoring, drift detection, and live performance evaluation of deployed agents. *What makes agents trustworthy at scale, i.e. mission-critical.*

---

## 8. Layer 3 — Workflow Packs

A Pack = a named agent "employee": triggers + investigation templates + action types + brief sections + KPIs + required entities + required connector classes. Configuration + prompts + tools on the runtime, not forked code.

### 8.1 Pack 1 — Reconciliation Analyst (V1, hand-built, Phase 1) — **the wedge**

*"We find the money leaking between your sell-in and your sell-out."*
- **Sense:** ERP sell-in + ≥2 sell-out sources.
- **Investigate:** every disputed `LedgerFact` → investigation (invoice drill-down, timing-difference detection, mapping-error detection, missing-credit-note detection).
- **Act:** ledger resolution proposals; drafted partner discrepancy emails; monthly report.
- **Brief:** discrepancy total (money), resolved vs open, aging.
- **KPIs:** $ identified, **$ resolved-as-genuine (net of timing/mapping artifacts)**, median time-to-resolution, % auto-resolved-with-approval. Report "identified" and "resolved-as-genuine" as distinct numbers; the second proves the product.

### 8.2 Pack 2 — Deductions & Claims Auditor (V2, Phase 2) — **platform test, not identity**

*"Stop writing off 1–3% of revenue."*
- **Sense:** retailer deduction feeds/portals, remittance advices (inbox), claim docs. Adds `Claim`.
- **Investigate:** validity per deduction against the ledger; evidence assembly.
- **Act:** drafted dispute packets, drafted approvals of valid deductions (finance tier), recovery tracking.
- **KPIs:** $ audited, $ disputed, $ recovered, win rate.
- **Positioning guardrail:** built *because* the reconciled ledger already exists; for GCC/India retailers the US AR specialists don't serve. **Never benchmark head-to-head against Glimpse/HighRadius on US retailers.**
- **Platform test:** must be buildable in ≤30% of Pack-1 effort. If not, the abstraction is wrong — fix before Phase 3.

### 8.3 Pack roadmap (Phase 3+, sequenced by data flywheel)

| Pack | Needs | Adds |
|---|---|---|
| Trade Spend Auditor | Verified sell-out, partner comms | `Promo`, uplift measurement |
| Demand & Replenishment Planner | Clean historical ledger | Forecasting, `InventorySnapshot`, OTIF |
| Pricing / RGM Analyst | Ledger + promo + partner data | `PriceRecord`, price-gap monitors |
| Field Execution Manager | SKU/location ontology | Shelf-photo ingestion, audit tasks |
| Launch Tracker | Distribution + velocity | Launch plan entity |
| E-commerce Manager | Connector fabric | Marketplace connectors, buy-box monitors |

**Distributor incentive design (precondition for the Phase 4 Partner Portal).** A distributor will not feed clean data into a tool built to dispute its deductions. The portal must lead with distributor-side value independent of the brand's audit use: (a) free reconciliation back to the distributor; (b) faster, evidence-backed dispute resolution that shortens *their* cash cycle; (c) lower friction than emailing spreadsheets. Net-positive for the distributor on its own, or it won't get adoption.

---

## 9. Workflow Builder (Phase 3 — extracted, not designed up front)

### 9.1 Block taxonomy (from Packs 1–2)

| Class | Blocks |
|---|---|
| Sources | ERP / Portal / Inbox / File Source |
| Fabric | SKU Mapper, Ledger Writer, Conflict Detector, Period Aggregator |
| Agents | Investigation, Document Extractor, Drafter, Classifier |
| Control | Approval Gate, Threshold Trigger, Schedule Trigger, Wait-for-Event, Branch |
| Outputs | Brief Section, Notification, Write-back, Export, Outcome Measurement |

### 9.2 Requirements

- **F-11.1 (P1)** Versioned block registry, typed I/O contracts (JSON Schema); workflows pin block versions.
- **F-11.2 (P1)** Canvas (React Flow): drag/connect/configure; contract validation.
- **F-11.3 (P1)** Simulation mode: run against historical ledger, actions sandboxed — mandatory before activation.
- **F-11.4 (P1)** Lifecycle: draft → simulated → active → paused → archived; version history.
- **F-11.5 (P1)** Non-removable guardrails: any external-effect block routes through the Approval Gate; policy engine binds at runtime regardless of wiring.
- **F-11.6 (P2)** Pack SDK: typed TS pack authoring, publishing + review.
- **F-11.7 (P2)** Template gallery: installable per tenant with config wizard.
- **F-11.8 (P2) [A] Two-way MCP interop** — every block callable as an MCP tool/API by external agents (n8n/Copilot/Claude), *and* external MCP tools callable by Veritail agents. *Makes Veritail the retail semantic layer others build on — ecosystem/standard status.*

### 9.3 Non-goal

No general-purpose automation, no generic HTTP/arbitrary-code node (until the reviewed Pack SDK). Every block is retail-semantic. Need Zapier? Use Zapier — against our APIs.

---

## 10. Product Surfaces (Frontend)

| Surface | Priority |
|---|---|
| **Monday Brief** (default post-login work report) | P0 |
| **Approval Queue** (decision surface) | P0 |
| **Verified Ledger** (numbers + lineage; drill to source; export) | P0 |
| **Investigations** (list + full evidence trail) | P0 |
| **Mapping Review** | P0 |
| **Connections (Admin)** (connector setup, vault, sync health, teach-mode) | P0 |
| **Analytics** (target-vs-actual, reading the verified ledger; demoted to appendix) | P1 |
| **Outcomes** (action track record) | P2 |
| **Builder** (canvas, simulation, lifecycle) | P1 (Phase 3) |
| **Partner Portal** (distributor-side) | P2 (Phase 4) |

Phase-1 frontend debt: real routing, token persistence + refresh, role-based UI.

---

## 11. Non-Functional Requirements

| Area | Requirement |
|---|---|
| **Multi-tenancy** | Hard isolation at every layer; tenant-scoped keys; per-tenant encryption context |
| **Security** | Secrets vault; SSO (OIDC/SAML) by Phase 2 before claiming it; least-privilege creds; sandboxed browser workers with egress allowlists |
| **Write-back security** | Separate least-privilege write creds per surface; irreversible writes → top tier; idempotency-keyed, rate-limited, audit-logged; pen test before production ERP posting |
| **Compliance** | Append-only (and `[A]` tamper-evident) audit; data-residency option (GCC); SOC 2 started Phase 2, claimed only when achieved |
| **Accuracy SLOs** | Eval harness (§7.6); brief numbers ledger-templated, never generated |
| **Reliability** | Durable runs survive deploys; idempotent syncs/write-backs; RPO ≤ 24h, RTO ≤ 4h initially |
| **Cost / unit economics** | Per-tenant budget caps, per-run token accounting, model-tier routing; cost-per-investigation and cost-per-successful-portal-sync tracked; gross-margin modeled per pack |
| **Observability** | Run traces, connector health + per-portal reliability %/cost-per-sync, queue depths, approval human-minutes, eval drift, `[A]` agent performance — one ops dashboard |
| **Performance** | Brief < 5 min; portal sync < 30 min/source; approval interactions < 200ms |

---

## 12. Data Model (delta from current Prisma schema)

**Modified:** `SKU` → tenant-scoped compound identity; `DataSourceConnector` → vault credential ref, class (`api|portal|inbox|file`), teach-mode + reliability/cost telemetry; `RawSourceRecord` → immutable `SourceRecord` (provenance + confidence); `ReconciliationRecord` → `LedgerFact` + `Investigation`; `HistoricalDataPoint` → `LedgerFact`.

**New:** `TradingPartner`, `Location`, `Target` (time-ranged), `SkuMapping`, `LedgerFact` (+ versions, **`[A]` bitemporal**), `Investigation` (+ evidence items, `unresolved_pending_external`), `AgentRun` (+ steps, token/cost), `Action` (+ transitions append-only, approval human-minutes, **`[A]` ontology-bound typed action defs**, **`[A]` scenario branch ref**), `Outcome` (+ confounder notes, **`[A]` context fingerprint for memory retrieval**), `Brief` (+ items), `Policy`, `Block`, `WorkflowDefinition` (+ versions), `EvalCase`, `EvalRun`, **`[A]` `PortalDefinition`** (cross-tenant registry), **`[A]` `AuditChain`** (hash-chained).

**Dropped:** `AIInsights`; simulated-connector artifacts.

---

## 13. Pricing & Packaging

| Element | Model |
|---|---|
| Platform fee | Per tenant/month, tiered by SKU count |
| Digital employees | Per active Pack/month — priced vs fraction-of-analyst-headcount |
| Connections | Per trading-partner connection/month (the value metric; grows with the moat) |
| Pilot (land) | Fixed-fee 30-day "Discrepancy Audit": ERP + top-3 distributors, quantify the leak; white-glove by TMLC; converts to subscription |
| Outcome kicker (optional) | % of recovered deductions/discrepancies (Deductions pack) |
| Partner program (Phase 3) | Consultancies build packs; revenue share on template gallery |

**Unit-economics guardrails:** model fully-loaded AI COGS (cost-per-investigation × volume + cost-per-sync × volume) against price per pack — frontier investigations and computer-use sync are the swing costs. Track **onboarding-cost-per-tenant** (TMLC hours) tenant-over-tenant; it must fall, or Veritail is a consultancy with software.

---

## 14. Rollout Plan & Milestones

**Precondition — team:** the durations assume a named team (backend, agent/ML, frontend, plus TMLC onboarding), with **portal automation under dedicated ownership**. Record actual team before committing dates; if smaller, lengthen phases. Let dates slip before trust gates (§4.7).

Each phase notes its **apex investments** — the `[A]` features that build toward category leadership (§15) rather than foundational delivery.

### Phase 0 — Foundations (weeks 0–8)
Temporal + agent-run store; vault; **tenant-scoped schema migration (own work item, with rollback plan)**; eval-harness skeleton; frontend auth/routing.
*Apex investment:* none — pure foundation.
*Exit:* a durable run survives a deploy; evals run in CI; migration verified on a copy of production.

### Phase 1 — Reconciliation Analyst, hand-built (weeks 8–30)
Connector fabric (1 ERP, 2 portal, 1 inbox); mapping graph + review; Verified Ledger + conflict detection; Investigation engine v1 (incl. `unresolved_pending_external`); Approval Queue + audit trail; weekly Brief. **Anchor client (live data), confirmed ICP-fit.**
*Parallel track P1-A — Portal automation burn-down:* teach-mode + self-heal on 2 GCC portals; reliability %/cost-per-sync (F-1.8); inbox auto-fallback (F-1.9).
*Apex investment (start):* `[A]` action-centric ontology (F-2.5) and `[A]` bitemporal ledger (F-4.7) — designed in now because retrofitting them later is expensive; they are the foundation of system-of-record gravity.
*Exit:* anchor analyst closes a month-end on Veritail only; **≥$X *resolved-as-genuine / recovered*** (target with partner; "surfaced" alone does not satisfy the gate); extraction/mapping SLOs met (precision-gated); zero unaudited writes; write-back security exercised once; **written wedge go/no-go** on portal reliability %/cost-per-sync.

### Phase 2 — Deductions Auditor + platform extraction (weeks 30–44)
`Claim` + deduction connectors; pack abstraction extracted from the two hand-built packs; SSO; SOC 2 start; write-path pen test; 3–5 paying tenants.
*Apex investment:* `[A]` Outcome Ledger as agent memory (F-8.5) seeded; `[A]` continuous agent observability (F-10.4); `[A]` scenario staging (F-7.8).
*Exit:* Deductions pack in ≤30% of Pack-1 effort; first $ recovered; first renewal-quality outcome data (with causal caveat); **onboarding-cost-per-tenant measured and trending down.**

### Phase 3 — Workflow Builder + partner program (weeks 44–64)
Block registry; canvas + simulation + lifecycle; TMLC builds one custom workflow with zero core-team code; Trade Spend pack (first built *on* the primitives); template gallery seed.
*Apex investment:* `[A]` two-way MCP interop (F-11.8); `[A]` cross-tenant portal-definition registry (F-1.11); `[A]` tamper-evident audit (F-7.9).
*Exit:* a non-engineer ships a working custom workflow; pack #3 live.

### Phase 4 — Network (months ~15+)
Distributor Partner Portal (free reporting, built on the §8.3 incentive design); `[A]` consented cross-tenant mapping priors (F-3.5); Demand Planner + Pricing packs; outcome-driven recommendations (F-8.3).
*Apex investment:* the two-sided regional network itself — the closest thing to an un-breachable position.
*Exit:* first distributor onboarded once, reused for a second brand; distributors report because the portal is net-positive for them independent of the brand's audit use.

---

## 15. Path to Category Leadership — the Apex ("Mythos") Thesis

Veritail's ambition is to become the **un-replicable standard** for retail commercial operations in distributor-heavy markets — the verticalized, mid-market-accessible apex (the "Mythos of retail"), reached *through* the wedge, not around it. Apex here means category-defining and un-copyable, **not** most-expensive-and-exclusive (that is Foundry's model and the wrong target). Five ascent levers, each tied to the technical features above:

1. **From "surfaces money" to "is the system of record."** Operational gravity is the highest lever. The action-centric ontology with governed writeback (F-2.5), the bitemporal (F-4.7) and tamper-evident (F-7.9) ledger, and end-to-end lineage make finance *defend Veritail's numbers in an audit* — at which point Veritail is infrastructure, not a tool.
2. **Compound the moats until catch-up is impossible.** The cross-tenant portal registry (F-1.11), the active-learning mapping graph (F-3.6), and above all the **Outcome Ledger as agent memory** (F-8.5) — a multi-year record of measured intervention→outcome pairs is the capability gap a new entrant cannot close, because they have no history.
3. **Win trust so completely it converts tool to infrastructure.** The trust gates plus tamper-evident audit and continuous agent observability (F-10.4). A multi-year zero-incident record on money decisions is the slowest moat and the cleanest separator of apex from also-ran.
4. **Close the two-sided regional network — the endgame.** The distributor data exchange (Phase 4) makes Veritail the connective tissue of a region's retail data; once both sides are onboarded, onboarding brand N approaches free and nobody can replicate it without having onboarded both sides. This is Crisp's network play, in the geography Crisp can't serve.
5. **Expand wedge → operating system, along the flywheel, only after the wedge is won.** Reconciliation → Deductions → Trade Spend → Demand/Pricing → Field/E-comm, each reusing accumulated ledger/mapping/outcome assets. Apex is when a commercial team runs its entire operation through Veritail — but the two-packs-before-extraction and per-pack-ROI discipline is what prevents boil-the-ocean death.

**If only three apex features can reach true frontier quality:** the action-centric ontology with writeback (system-of-record gravity), the Outcome Ledger as agent memory (the capability gap no one can copy), and tamper-evident lineage-complete audit (the trust that makes finance treat Veritail as infrastructure). Those three separate an apex platform from a very good vertical tool.

---

## 16. Success Metrics

| Layer | North-star & guardrails |
|---|---|
| **Company north star** | $ verified financial impact **resolved-as-genuine + recovered** per tenant per quarter ("surfaced" is a leading indicator only) |
| Fabric | Partner connections live; % records ingested untouched; mapping coverage %; per-portal reliability %; cost-per-successful-sync |
| Runtime | Investigations accepted-as-correct %; approval queue latency; brief readership; **approvals-per-analyst-per-day & human-minutes-per-$ (sublinear to volume)** |
| Packs | Pack KPIs (8.1–8.2); pack #N build cost vs pack #1 |
| Builder | Workflows shipped by non-engineers; partner-built workflows live |
| Economics | Cost-per-investigation; gross margin per pack; **onboarding-cost-per-tenant (must fall)** |
| **Apex (category leadership)** | **System-of-record gravity** (% of tenant money decisions transacted through Veritail; finance sign-off rate); **outcome-ledger depth** (measured outcome pairs accumulated); **regional network density** (brands per onboarded partner); **renewal/NRR** |
| Trust (guardrails) | Brief numeric factuality = 100%; eval SLOs green; zero unapproved external actions; audit completeness = 100% |

---

## 17. Risks & Mitigations

| Risk | Severity | Mitigation |
|---|---|---|
| One wrong number in front of finance | Existential | Ledger-templated numbers; eval gates; show-the-work; human approval on all resolutions; `[A]` tamper-evident audit |
| Portal automation brittleness | High | Teach-mode + self-heal + re-teach; inbox fallback; instrumented reliability/cost with a Phase-1 go/no-go |
| Value flows through inbox/file, not portals | High | Inbox/file first-class; story + pricing hold on that path; measured in Phase 1 |
| **Crisp moves into resolution/recovery** | High | Compete only at the two ends (no-API ingestion; approval-gated recovery loop) — Crisp's US-data + recommendation core is not built for either; outcome ledger + regional network compound faster than it can re-platform |
| AI COGS blows up margin | High | Cost-per-investigation/sync tracked; model-tier routing; caching; per-tenant budgets; gross margin modeled per pack |
| Approval load eats the headcount value prop | Med-High | Approval-load accounting (F-7.7); one-click-confirm-at-scale; human-minutes-per-$ guardrail |
| Outcome attribution overclaims causation | Med-High | "Associated with," never "caused"; confounders recorded; quasi-experimental framing |
| Platform abstraction built too early | High | Extract after two hand-built packs; Phase-2 exit is the test |
| Boil-the-ocean drift (incl. premature apex chase) | High | Roadmap gated on per-pack ROI; apex features sequenced as later-stage; phase exits contractual |
| Anchor-client overfit / off-ICP | Medium | Second design partner by Phase 2; onboarding-cost-per-tenant must fall; anchor confirmed ICP-fit |
| Distributors won't feed the Phase-4 portal | Med-High | Distributor-net-positive design as precondition (§8.3) |
| **Foundry-style build-it-yourself at top of market** | Low-Med | Foundry is enterprise-priced and implementation-heavy; Veritail wins the mid-market it can't economically serve |
| Credential/security incident on client ERP | High | Vault; least-privilege; separate scoped write creds + write-path pen test (F-1.10); sandboxed workers |
| Data-sharing sensitivities (cross-tenant priors) | Medium | Opt-in, anonymized, legal review; off by default |

---

## 18. Non-Goals (V1–V2)

- Generic automation platform (no arbitrary HTTP/code nodes).
- Retailer-side merchandising suite — different buyer; revisit Phase 4+.
- Real-time/streaming POS analytics — batch matches the workflows.
- Own forecasting science beyond baseline + seasonality until the Demand pack.
- Consumer panel / syndicated data competition — we verify *your* data.
- Competing with Crisp on US-retailer data harmonization, or with deductions specialists on US AR.
- Being the enterprise apex (Foundry's model) — we are the mid-market-accessible apex.
- Marketing the AI. We market the work product and the track record.

---

## 19. Open Questions

1. **(Build-blocker)** Anchor partner: which client, and does it resemble the $20M–$500M mid-market ICP? Resolve before Phase 1 build.
2. Naming — **resolved: Veritail.** Pending: trademark search (Nice 9 & 42, UAE/KSA/India/US) and .com/.ai acquisition.
3. Durable-engine: Temporal self-hosted vs cloud vs lighter — 1-week spike.
4. First portal targets: 2–3 GCC distributor portals (by anchor's partner list).
5. Outcome-kicker pricing: legal/accounting structure for %-of-recovery in target jurisdictions.
6. TMLC services revenue: how much to bundle into the pilot vs keep separate — tie to onboarding-cost-per-tenant trend (the product-vs-consultancy fork).
7. Team size & composition for the Phase 0–1 timeline; who owns portal automation full-time.
8. Target gross-margin floor per pack and the cost-per-investigation/sync budgets that imply it.
9. Portal-reliability and cost-per-sync floors defining the Phase-1 wedge go/no-go.
10. Distributor-incentive model for the Phase-4 portal — net-positive independent of the brand's audit use.
11. **(Apex)** Sequencing of the three priority apex features (action-centric ontology, outcome-memory, tamper-evident audit) against paying-customer pull — which earns its build first.

---

*End of PRD v2.0. The build plan starts at Phase 0. Nothing in Phases 2–4 — including the apex investments — justifies skipping the Phase 1 exit criteria. The apex is reached through the wedge, never around it. When timeline and trust gate conflict, the timeline yields.*
