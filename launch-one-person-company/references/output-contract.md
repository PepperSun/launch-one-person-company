# Output Contract

Default to an action-map playbook. Do not generate a large document pack unless the user previews the map and chooses execution files through option UI.

Generate artifacts in the current workspace under:

```text
opc-launch-packs/YYYY-MM-DD-project-slug/
```

Use a lowercase slug derived from the idea. Avoid overwriting existing folders; append `-2`, `-3`, or a short timestamp if needed.

## Stage 1: Default Action Map

Required default file:

```text
00-action-map.md
```

The action map is a global overview. Keep it short enough to scan in one pass.

### Required Sections

```markdown
# [Project Name] Action Map

## Snapshot
- Idea:
- State:
- Customer:
- Revenue test:
- Data risk:
- Stage:
- Blocked:

## Action Map
```

Then include 7-12 numbered actions. Use stable IDs:

```text
A01, A02, A03...
```

Each action must include:

- `When`: the node or trigger when this action should happen.
- `Do`: the concrete action.
- `How`: 1-3 direct steps.
- `Where`: website, platform, account, community, agency, or local file.
- `Done`: observable completion standard.
- `If blocked`: what happens if the user cannot complete it.
- `Next`: next action ID.
- `Risk`: low, medium, high, or blocked.
- `Source`: official or platform source link when the action depends on external rules.

Use this compact shape:

```markdown
### A01 - [Action Name]
- When:
- Do:
- How:
  1.
  2.
  3.
- Where:
- Done:
- If blocked:
- Next:
- Risk:
- Source:
```

## Stage 1 Style Rules

- Use the user's main language.
- Use short sentences.
- Use direct verbs.
- Avoid long explanations.
- Avoid motivational copy.
- Do not include long option matrices.
- Keep legal, tax, and compliance caveats short and attached to the relevant action.

## Stage 2: Ask Whether To Expand

After the user previews `00-action-map.md`, decide whether expansion choices are already `user-provided`.

- If the user explicitly says not to expand, stop after the action map.
- If the user explicitly provides action IDs and output format, generate those files without asking again.
- If action IDs, range, "all", or output format are missing or ambiguous and option UI is available, call `request_user_input` or an equivalent option-input tool for only the missing decision.
- If option UI is unavailable, use a free-form completion fallback with only these field names: `expand_action_ids` and `execution_format`.

Ask:

1. Whether to generate execution files.
2. Which action IDs to expand.
3. Preferred format.

Recommended option choices:

- `Priority only (Recommended)`: expand the next 1-3 unblocked actions.
- `Selected IDs`: user provides IDs through the free-form Other path, such as `A01,A03-A05`.
- `All actions`: expand every action, including blocked actions as blocked SOPs.
- `Not now`: stop after the action map.

Preferred format choices:

- `Markdown playbook (Recommended)`: best for SOPs and step-by-step execution.
- `CSV checklist`: best for task tracking.
- `Both`: higher output volume.

If option UI is unavailable, do not ask for action IDs through a plain text multiple-choice questionnaire. Let the user provide `expand_action_ids` and `execution_format` freely, then continue. A Markdown list of expansion choices without a prior option-input tool call is a failure.

## Stage 2: Execution Files

Generate only the files selected by action ID. Put them under:

```text
execution/
```

Use this naming pattern:

```text
execution/A01-short-action-name.md
execution/A02-short-action-name.md
execution/A03-short-action-name.csv
```

Each Markdown execution file must include:

```markdown
# A01 - [Action Name]

## Goal

## Before You Start
- Inputs needed:
- Accounts needed:
- Decisions needed:

## Steps
1.
2.
3.

## Where To Do It

## Done Definition

## If You Cannot Finish

## Next Action

## Sources
```

Each CSV checklist must use these columns:

```csv
action_id,task,where_to_do_it,input_needed,done_definition,dependency,risk_level,source,status
```

## Optional Execution Modules

Map action IDs to only the modules the user selected:

- Validation and customer discovery.
- Business model and pricing.
- Registration, EIN, tax, licenses, BOI, and compliance SOPs.
- Accounts and tools checklist.
- Website or waitlist brief.
- CRM pipeline.
- Finance tracker.
- Social account operations.
- Static website draft.

Create `website-draft/` only when the selected action ID calls for a website or the user asks for it.

Default website draft files:

```text
website-draft/
  index.html
  styles.css
  copy.md
```

Do not collect sensitive information by default. Prefer a mailto link, waitlist placeholder, or scheduling link placeholder.
