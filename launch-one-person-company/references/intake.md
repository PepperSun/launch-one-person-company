# Intake

Collect enough information to generate a useful launch pack while making the user actively confirm every unresolved decision. The goal is to help the user think, not to silently replace their judgment with agent assumptions.

## Minimum Fields

Collect these eight fields before final file generation:

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

## Confirmation Protocol

Use this protocol unless the user has already answered all eight minimum fields in one message.

1. Start from the fields the user explicitly provided.
2. For each missing, unclear, inferred, or recommended field, ask the user to confirm it before final generation.
3. Ask one decision at a time by default. A single message may combine only tightly related decisions, such as `budget_and_timeline`.
4. Each confirmation question must include practical options, advantages, disadvantages, a recommended default, and whether the choice is reversible or blocking.
5. The user can answer with a choice, a correction, or "unknown".
6. Treat "unknown" as an active answer. Keep the item as an assumption or blocked decision instead of trying to resolve it silently.
7. Do not generate the launch-pack files until every minimum field is either user-provided, user-confirmed, or user-marked unknown.

Use this compact format for each unresolved field:

```markdown
## Confirm: [field]

Current assumption:

| Option | Advantages | Disadvantages | Cost / Effort | Risk | Reversible? |
|---|---|---|---|---|---|

Recommended default:
Why this default fits:
What would change the recommendation:

Please choose one option, edit the assumption, or answer "unknown".
```

## Intake Style

Ask one question at a time when the user has not answered all eight fields. Use a compact batch only when the user explicitly asks to answer all questions at once.

When the user says "I do not know":

1. Show the practical options.
2. List advantages and disadvantages.
3. Recommend a default.
4. Mark the default as an assumption.
5. Identify whether the decision is reversible or blocking.

When the user gives a rough idea but leaves other fields unresolved, do not jump directly to a full assumption review. First walk through the missing fields with the confirmation protocol.

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

Ask the user to confirm, correct, or approve generation only after the confirmation protocol is complete. Do not use this final review to skip unresolved confirmations.
