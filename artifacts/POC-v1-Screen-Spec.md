# POC v1 Screen-by-Screen Spec — "Generate the Company"

Base: https://idea-one-psi.vercel.app/
Goal: Convert buyer intent into a generated "company of agents" and a purchase/deployment request.

## Scope Lock (v1)
- In scope: brief form, generated org chart, Souls visibility, process snapshot, CTA.
- Out of scope: real VPS provisioning, runtime orchestration, RBAC, full billing.

## Screen 1 — Hero + Value
**Headline:** Build your AI company in minutes.
**Sub:** Enter your business specifics and instantly get a tailored org chart of agents with roles, Souls, and processes.
**Primary CTA:** Generate My Company
**Secondary CTA:** See Example Company

## Screen 2 — Buyer Brief Form
Fields (required unless marked optional):
1. Business type / industry
2. Main objective (e.g., increase sales, automate support)
3. Team size target (small/medium/large or numeric)
4. Budget mode (lean / balanced / aggressive)
5. Speed vs quality (slider)
6. Channels (web, email, whatsapp, phone, etc.)
7. Optional notes

**Action:** Generate Company

## Screen 3 — Generated Company (Org Chart)
- Visual org chart (clickable nodes)
- Node fields:
  - Agent name
  - Role title
  - KPI chip
  - Confidence chip
- Edge labels for handoffs

Top bar actions:
- Regenerate
- Lock/Unlock role
- Export preview

## Screen 4 — Agent Soul Drawer
On node click/hover:
- Mission
- Scope (in/out)
- KPIs
- Tools/Permissions (POC level)
- Handoffs
- Guardrails
- Soul Summary (short)
- Optional: "Show full Soul"

## Screen 5 — Process Snapshot
Show 3–5 core process flows, e.g.:
- Lead → Qualification → Proposal → Close
- Ticket → Triage → Solve → QA → Close
- Content idea → Draft → Review → Publish

Each flow shows involved agents and SLA/KPI hint.

## Screen 6 — Catalog View
List/grid of all generated roles with quick search/filter.
- Card: role, mission, KPI, process ownership
- Open Soul in modal/drawer

## Screen 7 — Conversion Block
**Primary CTA:** Buy This Company Setup
**Secondary CTA:** Request Deployment Plan

Capture:
- Email
- Company name
- Preferred go-live timeline

## Copy Style
- Clear, direct, business-value first
- Avoid technical jargon unless in "advanced" sections

## Acceptance Criteria
1. User can go from form to generated company in one session.
2. User can inspect all agent Souls from chart.
3. User can view process snapshot without confusion.
4. CTA for purchase/request is visible and actionable.
