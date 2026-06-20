# Intake

Collect enough information to generate a useful launch pack without forcing the user to finish every decision upfront.

## Minimum Fields

Collect or infer these eight fields before final file generation:

| Field | Ask For | Acceptable Unknown Handling |
|---|---|---|
| `idea` | One-sentence description of the business idea | Ask the user to write a rough sentence; do not proceed without at least a rough idea |
| `state` | U.S. state for registration or default operations | If unknown, block state-specific registration and tax SOPs |
| `business_archetype` | B2B SaaS, AI tool, productized service, consulting, digital product, or unclear | Infer from the idea and confirm as an assumption |
| `target_customer` | B2B, B2C, prosumer, creator, developer, enterprise, or unclear | Offer 2-4 likely customer options |
| `revenue_model` | Subscription, project fee, retainer, usage-based, one-time, pre-sale, or unclear | Recommend a reversible validation model |
| `data_risk` | Personal, customer business, health, financial, child, biometric, location, or other sensitive data | If uncertain and the idea may touch sensitive data, mark related SOPs high risk |
| `launch_stage` | Idea only, customer conversations, MVP, already charging, or unclear | Infer from the user's facts and confirm |
| `budget_and_timeline` | Launch budget and intended timeline | Use low-budget defaults if unknown |

## Intake Style

Ask for missing information in a compact batch when the user wants speed. Ask one question at a time when the user is uncertain or overwhelmed.

When the user says "I do not know":

1. Show the practical options.
2. List advantages and disadvantages.
3. Recommend a default.
4. Mark the default as an assumption.
5. Identify whether the decision is reversible or blocking.

## Assumption Review Template

Before writing files, summarize:

```markdown
## Assumptions To Confirm

- Idea:
- State:
- Primary archetype:
- Secondary archetype:
- Target customer:
- Revenue model:
- Data risk:
- Launch stage:
- Budget and timeline:
- Website decision:
- Social distribution priority:
- Blocked decisions:
```

Ask the user to confirm, correct, or approve best-effort generation.
