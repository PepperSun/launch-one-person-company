---
name: launch-one-person-company
description: "Use when a user wants to turn a vague OPC, one-person company, solo founder, solopreneur, AI/software, productized service, consulting, or digital product idea into a U.S.-default launch plan, visual HTML action map, setup SOPs, compliance triage, social operations, or selected execution files."
---

# Launch One-Person Company

Guide a user from a vague one-person company idea to a visual HTML launch action map, then optionally to selected execution playbook files. Default to U.S. launch context and to AI, software, productized service, consulting, and digital product businesses.

Do not treat this as legal, tax, financial, or compliance advice. Provide decision support, risk classification, official-source SOPs, and clear next actions. Mark work that needs a CPA, attorney, licensed professional, or official agency confirmation.

## Non-Negotiables

- Classify each user-facing decision as `user-provided` or `unresolved` before asking. Do not re-ask clearly provided fields.
- For unresolved decisions, use an option-input tool such as `request_user_input` when available. If unavailable, use the text-choice fallback in `references/intake.md`.
- Follow the user's main conversation language for questions, summaries, and all visible action-map text. Preserve official U.S. terms such as `Articles of Organization`, `EIN`, `Responsible Party`, and `registered agent`.
- Default output is `00-action-map.html`, not a Markdown map or full document pack.
- Generate execution files only after the user previews the map and chooses action IDs, ranges, or all actions.
- Browse current official sources before including U.S. registration, EIN, tax, license, BOI, privacy, AI disclosure, regulated-industry, platform-policy, or compliance SOPs.
- Block only the affected high-risk task when facts are missing. Keep safe validation and setup work moving.
- Show realistic substitutes and tradeoffs when recommending tools, accounts, websites, CRM, payments, finance, or social channels.

## Core Workflow

1. Collect and confirm the eight minimum intake fields from `references/intake.md`.
2. Classify one primary archetype, plus one secondary archetype when useful, using `references/archetypes.md`.
3. Shape unresolved choices with `references/decision-support.md`.
4. Classify risk and blocked work with `references/risk-classification.md`.
5. Research current official and platform sources for external-process actions.
6. Create the default visual action map under `opc-launch-packs/YYYY-MM-DD-project-slug/` using `references/output-contract.md`.
7. Ask whether to expand selected action IDs, then generate only the requested execution files.

## Reference Routing

| Need | Read |
|---|---|
| Intake, option UI, text fallback, unknowns | `references/intake.md` |
| Business type and launch path | `references/archetypes.md` |
| Option tradeoffs and substitutes | `references/decision-support.md` |
| Legal, tax, privacy, data, regulated, or compliance risk | `references/risk-classification.md` |
| Registration, EIN, license, tax, BOI, privacy, AI disclosure, external SOPs | `references/us-external-sop.md` |
| Tools, accounts, website, CRM, finance, payment stack | `references/tool-substitutes.md` |
| Founder/brand accounts, communities, cadence, social distribution | `references/social-account-ops.md` |
| HTML action map and execution files | `references/output-contract.md` |
| Validation and forward tests | `references/validation-scenarios.md` |

## Operating Checks

- Before writing files, verify every minimum field is `user-provided`, `user-confirmed`, or `user-marked unknown`.
- Keep outputs playbook-like: direct verbs, short lines, clear done definitions, minimal explanation.
- Do not always recommend a website; decide from archetype, stage, acquisition path, and credibility needs.
- Include social operations as concrete launch work when useful, and state when social should not be the priority.
- Never claim a user definitely needs or does not need an entity, license, tax account, insurance, privacy policy, professional review, or compliance certification unless current official sources and user facts support that cautious statement.
- Include source names and links beside external-process action nodes or SOP steps.
