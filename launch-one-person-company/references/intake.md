# Intake

Collect enough information to generate a useful action map while making the user actively confirm every unresolved decision through option UI. The goal is to help the user think, not to silently replace their judgment with agent assumptions.

## Minimum Fields

Collect these eight fields before action-map generation. Do not re-ask a field that the user has already clearly answered in the current conversation.

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

## Option-UI Confirmation Protocol

This protocol requires a real tool call. If `request_user_input` or an equivalent option-input tool is available, call it. Writing a Markdown question with options is not option UI.

Use this protocol only for fields that are not already `user-provided`.

1. Start from the fields the user explicitly provided.
2. Mark clear user answers as `user-provided`; do not ask those fields again.
3. For each missing, unclear, inferred, or recommended field, ask the user to confirm it by calling `request_user_input` before generation.
4. Ask one decision at a time by default. A single option-UI prompt may combine only tightly related decisions, such as `budget_and_timeline`.
5. Each option must include the practical tradeoff in its description: advantage, disadvantage, cost or effort, risk, and whether it is reversible or blocking.
6. Put the recommended choice first and suffix its label with `(Recommended)`.
7. Include an `Unknown` option when the decision can safely remain unresolved. Treat the UI's free-form `Other` path as the place for corrections or custom answers.
8. The user can answer with a choice, a correction, or `Unknown`.
9. If `request_user_input` or equivalent option UI is not available, use the free-form completion fallback. Do not convert the same question into a prose multiple-choice prompt.
10. Do not generate the action map until every minimum field is user-provided, user-confirmed, or user-marked unknown.

When using `request_user_input` or equivalent option UI:

- Ask 1-3 short questions.
- Use 2-3 mutually exclusive choices per question.
- Keep labels to 1-5 words.
- Put tradeoffs in one-sentence descriptions.
- Do not include an `Other` option manually if the UI adds it automatically.
- Use the user's main language for prompts and labels.

Minimal tool-call shape:

```text
request_user_input({
  questions: [{
    header: "short label",
    id: "field_name",
    question: "one short question in the user's language",
    options: [
      { label: "Default (Recommended)", description: "Advantage, disadvantage, effort, risk, reversible/blocking." },
      { label: "Substitute", description: "Advantage, disadvantage, effort, risk, reversible/blocking." },
      { label: "Unknown", description: "Keeps safe work moving and blocks only dependent actions." }
    ]
  }]
})
```

Failure condition: if the assistant message contains selectable choices but no option-input tool call happened first, stop and correct the flow before continuing.

## No-Option Fallback

Use this only when option UI is unavailable.

1. List the missing fields as plain field names.
2. Do not include multiple-choice options.
3. Do not recommend defaults inside the fallback.
4. Let the user answer freely in their own words.
5. After the user supplies enough information, mark those fields as `user-provided` and continue.
6. If a field remains missing, keep only the dependent action blocked; continue safe action-map work when possible.

Fallback shape:

```text
Option UI is not available here. You can still continue by filling these fields in free form:

state:
target_customer:
revenue_model:
data_risk:
launch_stage:
budget_and_timeline:
```

This is not a questionnaire with choices. Do not add A/B/C options or option tradeoffs in this fallback.

## Field Prompt Guidance

- `idea`: If missing, ask the user to use the free-form Other answer with a one-sentence idea. Offer broad categories only as fallback choices.
- `state`: Offer likely state, `Unknown`, and "not U.S. yet" when relevant.
- `business_archetype`: Offer the inferred archetype, the strongest substitute, and `Unknown`.
- `target_customer`: Offer 2-3 likely customer segments.
- `revenue_model`: Offer the recommended validation model, one substitute, and `Unknown`.
- `data_risk`: Offer "low/no sensitive data", "customer/business data", and "sensitive/regulated data".
- `launch_stage`: Offer likely current stage, closest next stage, and `Unknown`.
- `budget_and_timeline`: Offer lean default, standard default, and `Unknown`.

## Unknown Handling

When the user chooses `Unknown`:

1. Mark the field as confirmed unknown.
2. Keep safe actions in the action map.
3. Block only the affected action-map node or execution SOP.
4. State what information would unblock it.

## Completion Rule

Before writing the action map, every minimum field must be one of:

- User-provided.
- Confirmed through option UI.
- Confirmed unknown through option UI.

Do not treat an agent inference as complete without active user confirmation.
Do not ask option UI for fields that are already user-provided.

## Old Behavior To Avoid

Do not use this style as the primary interaction:

```markdown
Here are the assumptions. Reply if correct.
```

Do not present a long markdown option matrix and ask the user to reply in prose. Use option UI instead.

## Intake Style

Use option UI for unresolved questions. Keep the visible text around the popup short: one sentence of context is enough.

When the user says "I do not know" or chooses `Unknown`:

1. Show practical choices in option UI if the field still needs a decision.
2. Recommend a default only when safe.
3. Mark the default as an assumption only after user confirmation.
4. Identify whether the decision is reversible or blocking.

When the user gives a rough idea but leaves other fields unresolved, do not jump directly to a full assumption review. First walk through the missing fields with the option-UI confirmation protocol or no-option fallback.

## Assumption Review Template

Before writing the action map, summarize:

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
- Confirmation status:
```

Ask the final confirmation through option UI only after the confirmation protocol is complete. Do not use this final review to skip unresolved confirmations.
