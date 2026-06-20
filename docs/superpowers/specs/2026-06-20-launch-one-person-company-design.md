# launch-one-person-company Skill Design

Date: 2026-06-20

## Purpose

Create a reusable Codex skill named `launch-one-person-company` that helps a user turn a vague one-person company idea into a launch readiness pack.

The skill is for AI, software, productized service, consulting, and digital product one-person companies. It defaults to a United States launch environment, while still allowing the user's language and business context to drive the interaction.

The skill does not perform legal, tax, or compliance work for the user. It provides decision support, operational planning, risk classification, external-process SOPs, and locally generated launch-pack files.

## Target User

The default user is a solo founder, solopreneur, or one-person company founder with an early or vague idea.

The skill should work when the user has not decided:

- The exact customer segment.
- The business archetype.
- The pricing or revenue model.
- Whether to register a legal entity now.
- Whether a website is needed.
- Which tools, accounts, or compliance checks are required.

The skill is not optimized for heavy physical businesses, restaurants, medical practices, regulated financial businesses, brick-and-mortar retail, or venture-backed team startups. If a user describes one of those cases, the skill should flag the mismatch and adapt cautiously.

## Launch Stage Boundary

Launch readiness means the user can start validating, selling, or delivering the idea with a clear operating plan and a clear view of external requirements.

The skill includes:

- Idea and ICP clarification.
- Customer validation planning.
- Business model and pricing decision support.
- Startup sequencing for registration, accounts, tools, website, CRM, finance, payment, and contracts.
- Social account and community-distribution operating advice.
- State-aware and industry-aware external SOPs for U.S. setup tasks.
- Compliance and licensing risk classification.
- Blocked-decision tracking.
- A 30/60/90 day execution roadmap.

The skill excludes:

- Guaranteeing legal, tax, or regulatory compliance.
- Completing actual company registration, bank account opening, tax filings, or certifications.
- Replacing an attorney, CPA, or licensed professional.
- Guaranteeing customer acquisition.
- Fundraising strategy.
- Long-term growth operations beyond the launch plan.
- Full product development or full brand design.

## Core Workflow

The skill uses a guided workflow:

1. Intake
   Collect the minimum inputs needed to classify the idea, assess risk, and decide what can safely be planned.

2. Decision support
   When the user does not know an answer, list plausible options, advantages, disadvantages, costs, risks, and a recommended default. Continue with a marked assumption when safe.

3. Assumption review
   Summarize the inferred business archetype, launch stage, risks, recommended defaults, and blocked decisions. Ask the user to confirm before generating final files.

4. Official-source research
   For external processes that can change over time, search official sources before producing SOPs.

5. Launch-pack generation
   Generate local Markdown and CSV files under a date-and-slug folder. Generate a static website draft only when the business type and stage call for it.

6. Local blocking
   Block only the affected high-risk SOP or task when critical information is missing. Do not block the full launch pack unless the entire request is unsafe or impossible to scope.

## Minimum Intake Fields

The skill must collect or infer these eight fields before final launch-pack generation:

1. `idea`: one-sentence description.
2. `state`: U.S. state for registration or default operations.
3. `business_archetype`: B2B SaaS, AI tool, productized service, consulting, digital product, or unclear.
4. `target_customer`: B2B, B2C, prosumer, creator, developer, enterprise, or unclear.
5. `revenue_model`: subscription, project fee, retainer, usage-based, one-time, pre-sale, or unclear.
6. `data_risk`: whether the business handles personal information, customer business data, health, financial, child, biometric, location, or other sensitive data.
7. `launch_stage`: idea only, customer conversations, MVP, already charging, or unclear.
8. `budget_and_timeline`: available launch budget and intended launch timeline.

The user may answer "unknown" or equivalent. Unknown answers trigger decision support rather than immediate failure.

## Business Archetypes

The skill should classify the idea into one primary archetype and, when helpful, one secondary archetype:

- B2B SaaS or micro-SaaS.
- AI tool, AI agent, or automation service.
- Productized service.
- Consulting or freelance expert business.
- Digital product, template, course, or paid knowledge product.

Each archetype changes the recommended validation plan, website decision, account stack, compliance review, CRM design, payment setup, and launch roadmap.

## Decision Support Rules

For any unresolved choice, the skill must provide:

- The available options.
- Advantages and disadvantages.
- Best-fit context for each option.
- Approximate cost and complexity.
- Risk implications.
- A recommended default.
- Whether the default is a reversible assumption or a blocking decision.

Examples of decisions requiring this treatment include entity timing, revenue model, website need, CRM tool, payment processor, accounting tool, social account strategy, state uncertainty, data risk, and whether professional review is needed.

## Risk Classification

The skill uses risk levels to decide whether to proceed, warn, or block:

- Low risk: reversible operating choices such as early CRM tooling, simple landing page, customer interview plan, or spreadsheet finance tracking.
- Medium risk: choices with operational or financial consequences such as paid advertising, payment processors, refund terms, recurring billing, contractor use, or B2B contract language.
- High risk: legal, tax, licensing, privacy, security, regulated-industry, sensitive-data, consumer-protection, or state-specific compliance decisions.

High-risk uncertainty blocks the affected SOP or task. The skill must still generate low-risk and medium-risk portions of the launch pack when possible.

## External SOP Requirements

External SOPs must be generated for relevant setup work such as:

- Entity formation or decision to delay entity formation.
- State business registration.
- EIN application.
- Business bank account preparation.
- Sales tax or state tax account checks.
- Local city or county licensing checks.
- BOI or FinCEN status checks.
- Privacy, data handling, and AI disclosure checks.
- Industry-specific licensing or certification checks.

For each SOP, include:

- Purpose.
- Prerequisites.
- Official source links.
- Step-by-step procedure.
- Required information or documents.
- Expected output.
- Decision points.
- Risks and when to consult a CPA, attorney, or licensed professional.
- Done definition.

For U.S. external processes, the skill must prioritize official sources such as state business portals, secretary of state sites, IRS, FinCEN, FTC, state attorneys general, and city or county portals.

## Tool and Account Recommendations

Tool recommendations should default to a lean, bootstrapped setup and still show substitutes.

Each tool category should include Lean, Standard, and Regulated or Pro options where relevant:

- Domain and email.
- Website or no-website path.
- CRM.
- Payment processor.
- Accounting or bookkeeping.
- Contract and e-signature.
- Support inbox or helpdesk.
- Analytics.
- Scheduling.
- Social or distribution channels.
- AI providers and automation tools.

Each recommendation should include advantages, disadvantages, approximate cost, suitable stage, and migration triggers.

## Social Account Operations

The skill should include social account and community-distribution advice as part of the launch pack.

The advice should be operational, not generic. It should include:

- Whether the user needs a founder account, brand account, both, or neither at the current stage.
- Recommended channels by archetype and customer type, such as LinkedIn, X, Reddit, Hacker News, Indie Hackers, YouTube, TikTok, newsletter, Slack or Discord communities, cold email, or niche forums.
- The advantages, disadvantages, effort level, and risk of each viable channel.
- A recommended default channel mix for the first 30 days.
- Account positioning, bio, pinned post, credibility signals, and profile setup checklist.
- Content pillars based on the idea, ICP, and validation stage.
- A lightweight posting cadence and interaction routine.
- Community participation SOPs, including how to ask questions, share progress, avoid spam, and convert conversations into customer interviews.
- Lead-capture path from social activity into CRM, email list, waitlist, demo call, or direct outreach.
- Metrics to track, such as replies, qualified conversations, waitlist signups, demo calls, trials, paid conversions, and content-to-lead ratio.
- Privacy, endorsement, advertising, platform-rule, and regulated-claims cautions when relevant.

The skill should also state when not to prioritize social account operations. Examples include businesses that can validate faster through warm introductions, direct outbound, existing communities, or customer interviews before public positioning is clear.

## Website Decision

The skill should not always generate a website.

Generate a website brief or static website draft when the business type and stage need one:

- B2B SaaS, AI tools, and digital products usually need at least a landing page, waitlist, demo, or checkout path.
- Productized services and consulting usually need a positioning page, proof, offer description, and booking or contact path.
- Early customer-discovery work through warm networks, Reddit, X, LinkedIn, Hacker News, email, or direct outreach may not need a website yet.
- If the user already has Webflow, Framer, Squarespace, Notion, or an existing website, generate a website brief and copy instead of a static HTML draft unless the user asks for one.

When generated, the static website draft should be simple HTML/CSS and should avoid collecting sensitive information by default.

## Output Contract

The skill should create launch packs in the current workspace under:

```text
opc-launch-packs/YYYY-MM-DD-project-slug/
```

Default files:

```text
00-executive-summary.md
01-intake-and-assumptions.md
02-validation-plan.md
03-business-model-and-pricing.md
04-launch-roadmap.csv
05-operations-stack.md
06-legal-tax-compliance-sop.md
07-accounts-and-tools-checklist.csv
08-website-brief.md
09-crm-pipeline.csv
10-finance-tracker.csv
11-blocked-decisions.md
12-social-account-ops.md
```

Optional folder:

```text
website-draft/
```

CSV outputs should use English field names so they can be imported into spreadsheet, CRM, Notion, Airtable, or project-management tools.

## Language Behavior

The skill follows the user's language by default.

If the user writes in Chinese, explanations should be in Chinese. If the user writes in English, explanations should be in English. The user can explicitly request any output language.

For U.S. execution materials, retain necessary English terms, official form names, button labels, and field names such as `Articles of Organization`, `EIN`, `Responsible Party`, and `registered agent`.

## Skill File Structure

Initial implementation should use a workflow-oriented skill with reference templates:

```text
launch-one-person-company/
  SKILL.md
  references/
    intake.md
    archetypes.md
    decision-support.md
    output-contract.md
    us-external-sop.md
    tool-substitutes.md
    social-account-ops.md
    risk-classification.md
    validation-scenarios.md
```

`SKILL.md` should stay concise and include trigger conditions, the core workflow, mandatory research rules, and when to load each reference file.

The reference files should hold reusable templates and detailed guidance. The first version should not include automation scripts.

## Validation Scenarios

The initial skill should be validated with three representative prompts:

1. Low-risk B2B SaaS
   "I want to build an AI invoice follow-up tool for independent consultants in California."

   Expected behavior: classify as B2B SaaS with AI-tool aspects, produce validation plan, California-aware external SOPs, account stack, CRM and finance templates, a landing-page brief or draft, and a social distribution plan focused on consultant communities and direct founder-led outreach.

2. Productized service with healthcare-adjacent risk
   "I want to help dental clinics set up an AI receptionist and charge monthly."

   Expected behavior: classify as productized service with AI automation and healthcare-adjacent data risk, recommend service packages and operational setup, provide cautious social and community outreach guidance for dental-practice decision makers, and block or escalate patient-data, HIPAA, consent, privacy, insurance, and regulated-claims questions.

3. Highly uncertain idea
   "I have an AI automation idea, but I do not know the customer, state, or pricing yet."

   Expected behavior: provide option matrices and recommended defaults, generate low-risk validation and discovery tasks, recommend low-commitment social listening and customer-discovery channels, and block state-specific registration SOPs until the state is known.

## Acceptance Criteria

The skill is successful when:

- It triggers for OPC, one-person company, solo founder, solopreneur, AI business, software business, productized service, consulting, and digital product launch requests.
- It asks for the minimum intake fields without forcing premature decisions.
- It handles unknown answers with option matrices and recommended defaults.
- It uses official-source research for current U.S. registration, tax, BOI, license, and compliance SOPs.
- It locally blocks high-risk uncertain SOPs while still generating safe parts of the launch pack.
- It produces the agreed Markdown, CSV, and optional static website files in a date-and-slug folder.
- It provides operational social account and community-distribution advice with channel trade-offs, profile setup, content pillars, cadence, interaction SOPs, lead-capture path, and metrics.
- It follows the user's language while preserving necessary English execution terminology.
- It avoids legal, tax, or compliance overclaiming.
