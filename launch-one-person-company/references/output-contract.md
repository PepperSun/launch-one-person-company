# Output Contract

Generate launch packs in the current workspace under:

```text
opc-launch-packs/YYYY-MM-DD-project-slug/
```

Use a lowercase slug derived from the idea. Avoid overwriting existing folders; append `-2`, `-3`, or a short timestamp if needed.

## Required Files

### `00-executive-summary.md`

Include:

- One-paragraph business summary.
- Primary and secondary archetype.
- Target customer and painful workflow.
- Launch stage.
- Recommended default path.
- Top risks.
- Blocked decisions.
- Next 7 days.

### `01-intake-and-assumptions.md`

Include all intake fields, inferred assumptions, unknowns, user-confirmed corrections, and confirmation status for each minimum field.

### `02-validation-plan.md`

Include:

- Riskiest assumptions.
- Interview targets.
- Interview script.
- Outreach scripts.
- Manual MVP or concierge test.
- Success metrics.
- Kill or pivot criteria.

### `03-business-model-and-pricing.md`

Include revenue model options, recommendation, starter pricing, packaging, billing cadence, refund or cancellation assumptions, and validation milestones.

### `04-launch-roadmap.csv`

Use these columns:

```csv
phase,task,why_it_matters,owner,dependency,estimated_effort,cost_range,risk_level,official_source,done_definition,status
```

### `05-operations-stack.md`

Include Lean, Standard, and Pro or regulated tool options for domain, email, CRM, payment, accounting, contracts, support, analytics, scheduling, AI providers, and automation.

### `06-legal-tax-compliance-sop.md`

Include official-source SOPs, blocked SOPs, and professional-review warnings. Use `references/us-external-sop.md`.

### `07-accounts-and-tools-checklist.csv`

Use these columns:

```csv
category,tool_or_account,recommended_tier,purpose,setup_steps,estimated_cost,substitutes,dependency,risk_level,done_definition,status
```

### `08-website-brief.md`

Include whether a website is needed now, why, recommended format, page structure, copy blocks, CTA, lead capture path, privacy cautions, and when to upgrade.

### `09-crm-pipeline.csv`

Use these columns:

```csv
lead_name,segment,source,status,next_action,next_action_date,pain_point,offer_fit,estimated_value,notes
```

### `10-finance-tracker.csv`

Use these columns:

```csv
date,type,category,vendor_or_customer,description,amount,payment_method,tax_relevance,receipt_link,notes
```

### `11-blocked-decisions.md`

Include each blocked item, why it is blocked, what information is needed, what can proceed meanwhile, who should confirm it, and official sources to check.

### `12-social-account-ops.md`

Include platform choice, founder vs brand account decision, profile checklist, content pillars, 30-day cadence, community participation SOPs, lead capture path, metrics, and cautions.

## Optional `website-draft/`

Create static HTML/CSS only when the website decision calls for it or the user asks for it.

Default files:

```text
website-draft/
  index.html
  styles.css
  copy.md
```

Do not collect sensitive information by default. Prefer a mailto link, waitlist placeholder, or scheduling link placeholder.
