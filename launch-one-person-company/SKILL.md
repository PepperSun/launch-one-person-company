---
name: launch-one-person-company
description: "Turn a vague OPC, one-person company, solo founder, solopreneur, AI/software business, productized service, consulting, or digital product idea into a US-default launch readiness pack. Use when the user wants startup-stage guidance from idea clarification through validation, registration/account setup SOPs, website decision, CRM/finance/payment stack, social account operations, compliance risk classification, and a 30/60/90 execution plan."
---

# Launch One-Person Company

Use this skill to guide a user from a vague one-person company idea to a launch readiness pack. Default to AI, software, productized service, consulting, and digital product businesses in a United States launch context.

Do not treat this as legal, tax, financial, or compliance advice. Provide decision support, risk classification, official-source SOPs, and clear next actions. Mark work that needs a CPA, attorney, licensed professional, or official agency confirmation.

## Core Workflow

1. **Intake**
   Collect or infer the eight minimum intake fields from `references/intake.md`. Let users answer "unknown"; do not force premature decisions.

2. **Classify**
   Read `references/archetypes.md` and assign one primary archetype plus, if useful, one secondary archetype.

3. **Support Decisions**
   For unclear choices, use `references/decision-support.md` to show options, advantages, disadvantages, costs, risks, a recommended default, and whether the default is reversible or blocking.

4. **Classify Risk**
   Use `references/risk-classification.md` to decide which tasks can proceed, which need warnings, and which are blocked until the user or a professional confirms more information.

5. **Review Assumptions**
   Before generating files, summarize the inferred archetype, user language, state, target customer, revenue model, launch stage, data risk, recommended defaults, and blocked decisions. Ask the user to confirm or correct the assumptions unless the user explicitly asks to proceed with best-effort assumptions.

6. **Research Current Official Sources**
   For U.S. external processes that can change, browse current official sources before producing SOPs. This includes state registration, EIN, state or local tax accounts, local licenses, BOI or FinCEN status, privacy and consumer-protection requirements, industry licensing, and platform policy when relevant. Prefer state portals, secretary of state sites, IRS, FinCEN, FTC, state attorneys general, city or county portals, and official vendor documentation. If current official verification is unavailable, mark that SOP as unverified or blocked.

7. **Generate Launch Pack**
   Use `references/output-contract.md` to create the launch pack under `opc-launch-packs/YYYY-MM-DD-project-slug/` in the current workspace. Generate the optional static website draft only when the website decision calls for it.

## Reference Routing

- Read `references/intake.md` before asking intake questions or accepting incomplete inputs.
- Read `references/archetypes.md` when classifying the business type or selecting archetype-specific paths.
- Read `references/decision-support.md` whenever the user has not decided among viable options.
- Read `references/risk-classification.md` before producing legal, tax, privacy, regulated-industry, data, or compliance-related steps.
- Read `references/us-external-sop.md` before generating registration, EIN, license, tax, BOI, privacy, AI disclosure, or other external-process SOPs.
- Read `references/tool-substitutes.md` before recommending tools or accounts.
- Read `references/social-account-ops.md` before recommending founder accounts, brand accounts, communities, content cadence, or social distribution.
- Read `references/output-contract.md` before writing launch-pack files.
- Read `references/validation-scenarios.md` when validating or forward-testing this skill.

## Operating Rules

- Follow the user's language by default. If the user writes Chinese, explain in Chinese. If the user writes English, explain in English. Preserve necessary U.S. execution terms such as `Articles of Organization`, `EIN`, `Responsible Party`, `registered agent`, and official form names.
- Default to a lean bootstrapped setup, but show Standard and Pro or regulated substitutes when tool choice matters.
- Do not always recommend a website. Decide based on archetype, launch stage, customer acquisition path, and whether the user already has a site or no-code builder.
- Include social account operations as an operational launch component, not generic marketing advice. Also state when social should not be the priority.
- Block only the affected high-risk SOP or task when critical information is missing. Continue generating safe validation, planning, and low-risk setup work.
- Never claim a user definitely does or does not need an entity, license, tax account, insurance, privacy policy, professional review, or compliance certification unless current official sources and the user's facts support a cautious statement.
- When citing external processes in generated launch-pack files, include source names and links in the relevant SOP or roadmap rows.
