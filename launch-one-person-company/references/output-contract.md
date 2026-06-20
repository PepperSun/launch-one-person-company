# Output Contract

Default to a visual HTML action-map playbook. Do not generate execution files unless the user previews the map and chooses action IDs through option UI or the text-choice fallback.

Generate artifacts in the current workspace under:

```text
opc-launch-packs/YYYY-MM-DD-project-slug/
```

Use a lowercase slug derived from the idea. Avoid overwriting existing folders; append `-2`, `-3`, or a short timestamp if needed.

## Stage 1: Default Visual Action Map

Required default file:

```text
00-action-map.html
```

The action map is a standalone global overview with inline CSS and no required external assets. Keep it short enough to scan in one pass.

### Required HTML Shape

Use semantic HTML. All visible text must use the user's main conversation language, except stable action IDs and necessary official U.S. terms.

```html
<!doctype html>
<html lang="[user-language-code]">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  <title>[Project Name] [Action Map label]</title>
  <style>
    /* Inline, responsive, print-friendly CSS only. */
  </style>
</head>
<body>
  <main>
    <header>
      <p>[OPC / launch stage label]</p>
      <h1>[Project Name] [Action Map label]</h1>
    </header>

    <section aria-labelledby="snapshot-title">
      <h2 id="snapshot-title">[Snapshot label]</h2>
      <!-- Idea, state, customer, revenue test, data risk, stage, blocked -->
    </section>

    <section aria-labelledby="map-title">
      <h2 id="map-title">[Action Map label]</h2>
      <!-- Flow row, timeline, or dependency map plus action cards. -->
    </section>
  </main>
</body>
</html>
```

### Visual Requirements

- Show a compact snapshot panel.
- Show a visual flow, timeline, lane view, or dependency map for the full launch path.
- Use 7-12 numbered action cards with stable IDs:

```text
A01, A02, A03...
```

- Each card must be readable without opening another file.
- Cards may use compact labels, badges, and connecting arrows.
- Use responsive CSS so the map works on desktop and mobile.
- Include print-friendly CSS with useful page breaks.
- Do not require JavaScript. Use it only if the static HTML still reads correctly without it.
- Do not use a marketing landing-page style. This is a playbook surface.

Each action card must include:

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

```html
<article class="action-card" id="A01">
  <div class="action-head">
    <span class="action-id">A01</span>
    <h3>[Action Name]</h3>
    <span class="risk risk-low">[Risk label]</span>
  </div>
  <dl>
    <dt>[When]</dt><dd>...</dd>
    <dt>[Do]</dt><dd>...</dd>
    <dt>[How]</dt><dd><ol><li>...</li></ol></dd>
    <dt>[Where]</dt><dd>...</dd>
    <dt>[Done]</dt><dd>...</dd>
    <dt>[If blocked]</dt><dd>...</dd>
    <dt>[Next]</dt><dd><a href="#A02">A02</a></dd>
    <dt>[Source]</dt><dd><a href="...">...</a></dd>
  </dl>
</article>
```

## Stage 1 Style Rules

- Use the user's main conversation language for every visible label, heading, and sentence.
- Use short sentences.
- Use direct verbs.
- Avoid long explanations.
- Avoid motivational copy.
- Do not include long option matrices.
- Keep legal, tax, and compliance caveats short and attached to the relevant action.
- Keep CSS restrained and utilitarian. The map should feel like an operating playbook, not a landing page.
- Use color only to clarify status, risk, sequence, and blocked items.
- Keep all source links visible and clickable.

## Stage 2: Ask Whether To Expand

After the user previews `00-action-map.html`, decide whether expansion choices are already `user-provided`.

- If the user explicitly says not to expand, stop after the action map.
- If the user explicitly provides action IDs and output format, generate those files without asking again.
- If action IDs, range, "all", or output format are missing or ambiguous and option UI is available, call `request_user_input` or an equivalent option-input tool for only the missing decision.
- If option UI is unavailable, ask one simple text-choice question at a time for `expand_action_ids` and `execution_format`.

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

If option UI is unavailable, use short numbered text choices and accept free-form answers.

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
