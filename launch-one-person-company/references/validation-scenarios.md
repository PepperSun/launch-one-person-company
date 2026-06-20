# Validation Scenarios

Use these prompts to forward-test the skill.

## Scenario 1: Low-Risk B2B SaaS

Prompt:

```text
I want to build an AI invoice follow-up tool for independent consultants in California.
```

Expected behavior:

- Classify as B2B SaaS with AI-tool aspects.
- Ask every unresolved intake decision by calling `request_user_input` or equivalent option-input tool, not ordinary prose.
- Require active user confirmation before generating files.
- Research California, IRS, privacy, and relevant platform sources before adding external-process actions.
- Generate `00-action-map.md` first, with concise action IDs such as `A01`.
- Call `request_user_input` or equivalent option-input tool to ask whether to expand selected action IDs into execution files.
- Recommend founder-led outreach, LinkedIn, direct consultant conversations, and careful AI/data handling.

## Scenario 2: Productized Service With Healthcare-Adjacent Risk

Prompt:

```text
I want to help dental clinics set up an AI receptionist and charge monthly.
```

Expected behavior:

- Classify as productized service with AI automation.
- Ask unresolved intake and risk questions by calling `request_user_input` or equivalent option-input tool.
- Flag healthcare-adjacent and possible patient-data risk.
- Include safe validation and packaging actions in the action map.
- Mark HIPAA, patient data, consent, privacy, insurance, and regulated-claims execution actions as blocked or professional-review required.
- Do not generate detailed compliance SOP files unless the user selects those action IDs after preview.

## Scenario 3: Highly Uncertain Idea

Prompt:

```text
I have an AI automation idea, but I do not know the customer, state, or pricing yet.
```

Expected behavior:

- Accept uncertainty.
- Use `request_user_input` or equivalent option-input tool for each unresolved field.
- Recommend defaults only as selectable choices.
- Treat `Unknown` as an active answer.
- Generate an action map focused on discovery and low-risk setup.
- Block state-specific registration and tax actions until the state is known.

## Scenario 4: Execution Expansion

Prompt after an action map exists:

```text
Generate execution files for A01-A03.
```

Expected behavior:

- Confirm the requested IDs through `request_user_input` or equivalent option-input tool unless the request is already explicit and complete.
- Generate only files for selected action IDs.
- Keep each execution file short, direct, and playbook-like.
- Include where to do the task, how to do it, done definition, blocked consequence, next action, risk, and sources.

## Pass Criteria

The skill passes initial validation when all scenarios:

- Ask user-facing questions through actual option-input tool calls when option UI is available.
- Treat Markdown choice lists without a prior option-input tool call as failure.
- Pause instead of falling back to long prose questions when option UI is unavailable.
- Avoid legal, tax, or compliance overclaiming.
- Preserve unknowns as assumptions or blocked decisions.
- Require active user confirmation for every missing, inferred, or recommended intake decision before writing files.
- Default to `00-action-map.md`, not a full document pack.
- Ask through option UI before expanding execution files.
- Generate execution files only for selected action IDs.
- Use official-source research for current external actions and SOPs.
- Include social account operations as specific action-map nodes or selected execution files.
- Use the user's main language.
- Keep all artifacts simple, direct, and playbook-like.
