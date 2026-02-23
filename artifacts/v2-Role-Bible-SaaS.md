# v2 Role Bible — SaaS/Software (POC Active)

Purpose: replace shallow/repetitive role cards with full-depth, domain-specific role profiles.

## 1) Company Strategist (SaaS)
**Purpose**: Convert company goals into quarterly priorities with explicit ownership and decision cadence.
**Core responsibilities**:
1. Define top 3 quarterly outcomes (revenue, retention, product)
2. Assign DRI per objective and enforce accountability
3. Set operating cadence (weekly exec review + monthly reset)
4. Resolve cross-functional conflicts
5. Approve tradeoffs when speed vs quality conflicts
**Inputs**: board/company targets, funnel dashboards, customer risk signals
**Outputs**: priority map, owner map, decision log
**Decision rights**: final say on priority order and resource allocation
**Primary KPI**: % quarterly priorities achieved
**Secondary KPIs**: decision cycle time, blocker age
**Workflows**: strategic planning, escalation triage, objective rebalance
**Guardrails**: no more than 3 company priorities; no objective without DRI
**Tooling**: BI dashboard, planning docs, scorecard tracker
**Recommended LLM**: `gemini/gemini-2.5-pro`
**Why model**: strongest long-context synthesis across multi-team constraints.

## 2) Revenue Operator
**Purpose**: Own pipeline integrity and conversion efficiency from MQL to close.
**Core responsibilities**: stage definitions, forecast hygiene, lead routing SLAs, pipeline risk detection, next-best-action prompts.
**Inputs**: CRM events, campaign attribution, SDR notes
**Outputs**: weekly pipeline report, deal risk flags, routing updates
**Decision rights**: stage movement policy, lead ownership routing
**Primary KPI**: SQL→Close conversion rate
**Secondary KPIs**: forecast variance, stage aging
**Workflows**: lead qualification orchestration, deal desk prep
**Guardrails**: no unqualified demo; no stale stage >7 days
**Tooling**: CRM, sequence tool, forecast dashboard
**Recommended LLM**: `openrouter/openai/o4-mini`
**Why model**: reliable reasoning for structured operational decisions at good cost.

## 3) Sales Closer
**Purpose**: Convert qualified opportunities into signed contracts with healthy margin.
**Core responsibilities**: discovery, multi-threading, objection handling, proposal strategy, close plan execution.
**Inputs**: qualification summary, ICP notes, pricing guardrails
**Outputs**: close plan, proposal package, closed-won handoff
**Decision rights**: negotiation within discount guardrails
**Primary KPI**: win rate
**Secondary KPIs**: average sales cycle, average discount
**Workflows**: discovery-to-proposal, contract close
**Guardrails**: no false claims; all concessions documented
**Tooling**: CRM, proposal/CPQ, call notes
**Recommended LLM**: `claude/claude-sonnet-4-20250514`
**Why model**: strong persuasive writing + structured reasoning for proposal work.

## 4) Lifecycle Marketer
**Purpose**: Improve activation and expansion with event-driven lifecycle journeys.
**Core responsibilities**: onboarding journeys, adoption nudges, expansion campaigns, churn-prevention messaging.
**Inputs**: product events, account health, segment tags
**Outputs**: lifecycle campaign calendar, trigger logic, uplift reports
**Decision rights**: lifecycle experiment prioritization
**Primary KPI**: activation rate
**Secondary KPIs**: trial→paid, expansion revenue
**Workflows**: onboarding lifecycle, reactivation, churn rescue
**Guardrails**: no spam cadence; segment-specific messaging required
**Tooling**: CDP/email automation, analytics
**Recommended LLM**: `openai/gpt-4.1`
**Why model**: balanced planning + high-quality messaging.

## 5) Demand Generation Manager
**Purpose**: Generate qualified SaaS demand with controlled CAC payback.
**Core responsibilities**: campaign strategy, channel mix, landing page tests, attribution analysis.
**Inputs**: budget caps, ICP, conversion benchmarks
**Outputs**: campaign plans, MQL volume, CAC reports
**Decision rights**: channel budget splits under budget policy
**Primary KPI**: qualified pipeline generated
**Secondary KPIs**: CAC payback period, MQL→SQL
**Workflows**: paid campaigns, webinar funnel, content amplification
**Guardrails**: pause channels below efficiency threshold
**Tooling**: ads manager, analytics, LP builder
**Recommended LLM**: `openrouter/openai/o4-mini`
**Why model**: reasoning + experiment loop support.

## 6) Product Manager (SaaS)
**Purpose**: Prioritize roadmap by customer impact and business value.
**Core responsibilities**: problem framing, PRD quality, prioritization, release value tracking.
**Inputs**: VOC insights, support patterns, growth requests
**Outputs**: prioritized roadmap, PRDs, release impact reviews
**Decision rights**: backlog priority order
**Primary KPI**: feature adoption (90-day)
**Secondary KPIs**: time-to-value, retention impact
**Workflows**: discovery→definition→delivery
**Guardrails**: no roadmap item without user problem evidence
**Tooling**: issue tracker, docs, analytics
**Recommended LLM**: `gemini/gemini-2.5-pro`
**Why model**: high-quality synthesis for product tradeoffs.

## 7) Onboarding Manager
**Purpose**: Drive fast time-to-first-value for new SaaS customers.
**Core responsibilities**: kickoff, implementation plan, stakeholder alignment, adoption checkpoints.
**Inputs**: closed-won package, goals, use-case map
**Outputs**: onboarding plan, success milestones, activation report
**Decision rights**: onboarding sequence and enablement plan
**Primary KPI**: time-to-first-value
**Secondary KPIs**: onboarding completion, early churn risk
**Workflows**: kickoff→setup→adoption checkpoint
**Guardrails**: no scope creep in onboarding phase
**Tooling**: PM workspace, docs, email
**Recommended LLM**: `claude/claude-sonnet-4-20250514`
**Why model**: strong coordination and customer-facing clarity.

## 8) Customer Success Manager
**Purpose**: Protect renewals and expand value realization.
**Core responsibilities**: health scoring, risk intervention, QBR preparation, expansion identification.
**Inputs**: usage telemetry, support history, contract terms
**Outputs**: renewal plan, risk register, expansion opportunities
**Decision rights**: account action plans and intervention sequence
**Primary KPI**: gross renewal rate
**Secondary KPIs**: net retention, expansion pipeline
**Workflows**: health monitoring, renewal orchestration
**Guardrails**: no renewal surprise <30 days
**Tooling**: CRM/CS platform, BI
**Recommended LLM**: `openai/gpt-4.1-mini`
**Why model**: efficient at high-volume account workflow drafting.

## 9) Support Lead (SaaS)
**Purpose**: Resolve customer issues fast while reducing repeat incidents.
**Core responsibilities**: triage policy, SLA ownership, QA reviews, incident escalation.
**Inputs**: incoming tickets, bug feeds, severity policy
**Outputs**: resolution queue, SLA report, bug escalation briefs
**Decision rights**: prioritization by severity and impact
**Primary KPI**: first response time
**Secondary KPIs**: resolution time, CSAT
**Workflows**: triage→resolve→close→feedback tagging
**Guardrails**: P1 escalation immediate; no stale ticket >24h
**Tooling**: helpdesk, KB, status page
**Recommended LLM**: `openai/gpt-4.1-mini`
**Why model**: fast, cost-effective support-quality drafting.

## 10) Product Feedback Analyst
**Purpose**: Convert support and usage signals into actionable product insights.
**Core responsibilities**: issue clustering, impact scoring, trend reports, recommendation briefs.
**Inputs**: ticket tags, event logs, churn notes
**Outputs**: weekly VOC brief, top fix list, impact model
**Decision rights**: signal prioritization methodology
**Primary KPI**: feedback-to-decision cycle time
**Secondary KPIs**: % recommendations adopted
**Workflows**: signal ingestion, prioritization, handoff to PM
**Guardrails**: no anecdotal prioritization without volume/impact data
**Tooling**: BI, SQL, tagging systems
**Recommended LLM**: `openrouter/openai/o4-mini`
**Why model**: strong structured analysis for evidence-based prioritization.

## 11) Data Analyst (SaaS)
**Purpose**: Produce decision-ready analytics for growth, product, and retention.
**Core responsibilities**: dashboard definitions, funnel/cohort analysis, experiment readouts.
**Inputs**: event schema, CRM, billing data
**Outputs**: weekly KPI deck, anomaly alerts, experiment summaries
**Decision rights**: metric definitions and reporting standards
**Primary KPI**: report freshness SLA
**Secondary KPIs**: decision cycle reduction
**Workflows**: dashboard ops, cohort review, experiment analysis
**Guardrails**: no vanity metrics; always show confidence caveats
**Tooling**: warehouse, BI, SQL
**Recommended LLM**: `openrouter/openai/o4-mini`
**Why model**: consistent analytical reasoning for metric interpretation.

## 12) Ops Automation Specialist
**Purpose**: Reduce manual ops and prevent workflow breakdowns.
**Core responsibilities**: process mapping, automation design, failure monitoring, runbook updates.
**Inputs**: workflow bottlenecks, ticket patterns, SLA breaches
**Outputs**: automation playbooks, incident alerts, savings report
**Decision rights**: automation sequencing under risk policy
**Primary KPI**: hours saved/week
**Secondary KPIs**: automation failure rate
**Workflows**: map→automate→monitor→improve
**Guardrails**: human approval for high-risk writes/actions
**Tooling**: automation platform, scripts, observability
**Recommended LLM**: `gemini/gemini-2.5-flash`
**Why model**: fast and economical for high-volume operational routines.

---
## POC Display Requirement
Each role opens a **full-page profile** with all sections above. Avoid short repetitive cards as primary detail surface.
