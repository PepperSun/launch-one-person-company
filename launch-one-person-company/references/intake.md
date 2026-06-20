# Intake

Collect enough information to build the action map while making the user actively confirm unresolved decisions. The goal is to help the user think, not to silently replace judgment with agent assumptions.

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

## Decision States

- `user-provided`: clear usable answer already given in the current conversation.
- `user-confirmed`: user selected or confirmed an option.
- `user-marked unknown`: user chose `Unknown` or said the field is not decided.
- `unresolved`: missing, ambiguous, inferred by the agent, or only recommended by the agent.

Do not ask again for `user-provided`, `user-confirmed`, or `user-marked unknown` fields.

## Question Protocol

This protocol requires a real tool call. If `request_user_input` or an equivalent option-input tool is available, call it. Writing a Markdown question with options is not option UI.

1. Start from the fields the user explicitly provided.
2. Mark each minimum field with a decision state.
3. Ask only unresolved fields.
4. Ask one decision at a time by default. Combine only tightly related decisions, such as `budget_and_timeline`.
5. Give tradeoffs for each option: advantage, disadvantage, effort or cost, risk, and whether it is reversible or blocking.
6. Put the recommended safe default first and suffix its label with `(Recommended)`.
7. Include `Unknown` when the field can safely remain unresolved.
8. Use the UI's free-form Other path for corrections or custom answers.
9. If option UI is unavailable, use the text-choice fallback below.
10. Do not generate the action map until every minimum field is `user-provided`, `user-confirmed`, or `user-marked unknown`.

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

Failure condition: if an option-input tool is available and the assistant message contains selectable choices without calling it first, stop and redo the decision with the tool.

## Text-Choice Fallback

Use this only when option UI is unavailable.

1. Ask one unresolved question at a time.
2. Use simple language in the user's main language.
3. Give 2-3 numbered choices.
4. Put the recommended choice first when there is a safe default.
5. Keep each choice to one short line.
6. Include `Unknown` when the field can safely remain unresolved.
7. Let the user answer with a number, label, or their own text.
8. After the user answers, mark the field as `user-provided`, `user-confirmed`, or `user-marked unknown`.
9. If a field remains missing, ask the next required question or block only the dependent action.

Fallback shape:

```text
Option UI is not available here. I will ask one question at a time.

Question: Which state should this launch use?
1. California (Recommended) - Use this if you live or operate there.
2. Unknown - Continue validation; state registration and tax steps stay blocked.
3. Other - Reply with the state.
```

Do not use long tables. Do not ask several unrelated questions in one message.

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

1. Mark the field as `user-marked unknown`.
2. Keep safe actions in the action map.
3. Block only the affected action-map node or execution SOP.
4. State what information would unblock it.

## Completion Rule

Before writing the action map, every minimum field must be one of:

- `user-provided`.
- `user-confirmed`.
- `user-marked unknown`.

Do not treat an agent inference as complete without active user confirmation.
Do not ask again for fields that are already complete.

## Intake Style

Use option UI for unresolved questions. Keep the visible text around the popup short: one sentence of context is enough.

When the user says "I do not know" or chooses `Unknown`:

1. Show practical choices in option UI if the field still needs a decision.
2. Recommend a default only when safe.
3. Mark the default as an assumption only after user confirmation.
4. Identify whether the decision is reversible or blocking.

When the user gives a rough idea but leaves other fields unresolved, do not jump directly to a full assumption review. First walk through the missing fields with the option-UI confirmation protocol or text-choice fallback.

## Readback Before Files

Before writing the action map, give a short readback in the user's language: idea, state, archetype, customer, revenue model, data risk, launch stage, budget and timeline, and blocked decisions.

Do not use the readback to skip unresolved confirmations. If the readback asks the user to approve a remaining decision, use option UI when available or the text-choice fallback when unavailable.
