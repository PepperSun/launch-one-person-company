# Risk Classification

Use risk classification to decide whether to proceed, warn, block, or require professional confirmation.

## Levels

### Low Risk

Usually reversible and safe to plan:

- Customer interviews.
- Problem surveys.
- Simple CRM spreadsheet.
- Basic finance tracker.
- Landing page without sensitive-data collection.
- Warm outreach.
- Public learning posts without regulated claims.

Proceed and include done definitions.

### Medium Risk

Operational or financial consequences:

- Paid ads.
- Payment processor setup.
- Refund and cancellation policies.
- Recurring billing.
- Contractor use.
- Service contracts.
- Customer data storage.
- Public claims about results.

Proceed with warnings, assumptions, and review triggers.

### High Risk

Block affected SOPs or require professional confirmation:

- Legal entity and liability decisions with material risk.
- Tax obligations, sales tax, nexus, or payroll.
- Licenses, permits, and certifications.
- Health, financial, legal, employment, housing, credit, insurance, education, or child-directed use cases.
- Sensitive personal data, biometrics, precise location, or government IDs.
- Patient, student, employee, consumer credit, or financial account data.
- AI outputs that affect eligibility, care, legal rights, financial decisions, employment, housing, or safety.
- Security commitments, enterprise procurement, DPA, SOC 2, HIPAA, GLBA, FERPA, COPPA, or similar frameworks.

Generate safe adjacent planning work, but mark the risky task as blocked or needing confirmation.

## Blocking Format

```markdown
### Blocked: [Decision or SOP]

**Why blocked:**
**Information needed:**
**Who should confirm:**
**Official sources to check:**
**Safe tasks that can proceed now:**
```

## Data Risk Prompts

Ask whether the business will handle:

- Names, email addresses, phone numbers, addresses, payment identifiers, or account IDs.
- Customer confidential business information.
- Health, medical, dental, therapy, fitness, or wellness data.
- Financial, tax, credit, investment, or insurance data.
- Children, students, employees, tenants, job applicants, or consumers in eligibility decisions.
- Biometric, precise location, government ID, or authentication data.

If the user is unsure, classify as at least medium risk and block regulated-data SOPs until clarified.
