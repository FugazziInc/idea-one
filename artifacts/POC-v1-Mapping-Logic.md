# POC v1 Mapping Logic (Fast Implementation)

## Inputs
- industry
- objective
- teamSizeTarget
- budgetMode (lean|balanced|aggressive)
- speedVsQuality
- channels

## Output
`company` JSON matching `artifacts/POC-v1-Company-JSON-Schema.md`

## Algorithm (pseudo)

1) Identify archetype
```ts
archetype = bestMatch(archetypes, input.industry, input.objective)
```

2) Seed candidate roles
```ts
candidates = roles
  .map(r => ({
    role: r,
    score:
      0.45 * objectiveMatch(r.fit.objectives, input.objective) +
      0.35 * industryMatch(r.fit.industries, input.industry) +
      0.20 * budgetFit(r.seniority, input.budgetMode)
  }))
  .sort(desc score)
```

3) Enforce cluster coverage from archetype
```ts
selected = []
for each clusterRule in archetype.roleClusters:
  take top scoring candidates in clusterRule.cluster up to clusterRule.min
```

4) Fill to team size cap (max 12)
```ts
while selected.size < min(input.teamSizeTarget, 12):
  add next highest scoring candidate that does NOT violate no-overlap rule
```

5) Attach processes
```ts
processes = processBlueprints.filter(p => archetype.mustHaveProcesses includes p.id)
```

6) Validate coverage
- every process step ownerRole exists in selected roles
- if missing owner, add matching role OR remap to nearest compatible role and flag `confidence -= 0.1`

7) Build org links
- top role = Company Strategist (or highest leadership score)
- set `reportsTo` by cluster:
  - sales/marketing/support/ops/data/finance -> leadership
  - specialists -> cluster lead when available

8) Build Soul summary
```ts
summary = `${mission}. Owns ${firstKPI}. Hands off to ${firstHandoff.toRole}.`
```

9) Final validations (ERR codes)
- `ERR_MAX_AGENTS_EXCEEDED`
- `ERR_ROLE_WITHOUT_KPI`
- `ERR_MISSING_HANDOFF`
- `ERR_PROCESS_STEP_UNOWNED`
- `ERR_DUPLICATE_PRIMARY_KPI`

10) Return generated company package

## Confidence Heuristic (simple)
Base 0.75
- +0.05 if role matches industry
- +0.05 if role matches objective
- +0.05 if process coverage complete
- -0.10 if owner role remapped
Clamp [0.4, 0.95]

## Dev Notes
- Keep generation deterministic for demos (fixed random seed per input hash)
- Expose `regen_reason_codes[]` for partial regenerate UI
- Log telemetry: generate_started/completed, soul_opened, node_locked, regen_partial, cta_clicked
