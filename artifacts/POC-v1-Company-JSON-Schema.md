# POC v1 Minimal Company JSON Schema

```json
{
  "companyName": "string",
  "objective": "string",
  "constraints": {
    "budgetMode": "lean|balanced|aggressive",
    "teamSizeTarget": "number",
    "speedVsQuality": "0-100",
    "channels": ["string"]
  },
  "org": {
    "nodes": [
      {
        "id": "agent_001",
        "name": "Ava",
        "role": "Revenue Strategist",
        "reportsTo": "agent_000|null",
        "kpi": "Qualified pipeline per month",
        "confidence": 0.87,
        "soul": {
          "mission": "string",
          "scopeIn": ["string"],
          "scopeOut": ["string"],
          "tools": ["string"],
          "handoffs": [
            { "to": "agent_002", "output": "qualified leads" }
          ],
          "guardrails": ["string"],
          "summary": "string",
          "full": "string"
        }
      }
    ],
    "edges": [
      {
        "from": "agent_001",
        "to": "agent_002",
        "type": "handoff|approval|service"
      }
    ]
  },
  "processes": [
    {
      "id": "proc_001",
      "name": "Lead-to-Close",
      "steps": [
        { "order": 1, "label": "Capture lead", "owner": "agent_003" },
        { "order": 2, "label": "Qualify", "owner": "agent_001" },
        { "order": 3, "label": "Propose", "owner": "agent_004" }
      ],
      "slaHint": "<48h first response"
    }
  ],
  "pricingTeaser": {
    "plan": "free|pro|team",
    "cta": "Buy This Company Setup"
  }
}
```

## Validation Rules (POC)
- Max agents: 12
- Every node must have role + KPI + soul.summary
- Every process must have >= 3 steps
- Every process step must have owner
- Every node (except top) should have reportsTo
