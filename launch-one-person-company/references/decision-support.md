# Decision Support

Use this reference to shape unresolved choices. Ask those choices through the protocol in `references/intake.md`; this file defines what tradeoffs to include.

## Option-UI Format

For each unresolved decision, prepare 2-3 mutually exclusive options:

- Put the recommended default first and suffix its label with `(Recommended)`.
- Keep option labels short.
- Put the practical tradeoff in the option description: best for, advantage, disadvantage, cost or effort, risk, and whether it is reversible.
- Include `Unknown` only when the decision can safely remain unresolved.
- Use the UI's free-form Other path for custom answers.
- If option UI is unavailable, use the text-choice fallback from `references/intake.md`.
- If the user has already made a clear choice, record it as `user-provided` and do not ask again.

For artifacts, you may summarize the decision in a compact table after the user has chosen. The artifact summary should state:

- Recommended default.
- Why the default fits the user's current facts.
- Whether it is reversible.
- What would trigger changing the decision.
- Whether any part is blocked.

## Common Decisions

### Register Entity Now vs Later

- **Delay registration:** Good for low-risk customer discovery with no payments, no sensitive data, and no contracts. Fast and cheap, but limited for banking, contracts, and liability separation.
- **Single-member LLC:** Common for U.S. solo founders who want liability separation and a more formal business setup. Requires state filing, registered agent, fees, ongoing state obligations, and tax/admin work.
- **Corporation:** Usually premature unless fundraising, equity issuance, or specific investor requirements are likely.
- **CPA or attorney review first:** Use for regulated, high-liability, multi-state, employee/contractor, or high-revenue situations.

### Website Need

- **No website yet:** Good when validation is through warm intros, interviews, and direct messages. Lowest cost, but less credible for cold traffic.
- **Landing page:** Good for SaaS, AI tools, digital products, and waitlists. Clear offer and conversion path, but needs copy and maintenance.
- **Service profile page:** Good for consulting and productized service. Builds credibility without overbuilding.
- **Static website draft:** Good when the user wants local files or a developer-owned starting point.
- **No-code builder:** Good when the user wants to edit without code.

### Revenue Model

- **Project fee:** Easiest for early service validation. Less recurring revenue.
- **Retainer:** Better cash predictability for ongoing service. Needs scope control.
- **Subscription:** Fits SaaS and recurring value. Requires retention and support.
- **Usage-based:** Fits measurable variable consumption. Harder to explain and forecast.
- **One-time sale:** Fits templates and courses. Needs ongoing acquisition.
- **Pre-sale:** Strong validation. Requires clear promise and trust.

### Social Account Strategy

- **Founder account:** Best when trust, expertise, and learning in public matter.
- **Brand account:** Best when the product needs separation from the founder or multiple future contributors.
- **Both:** Useful after positioning is clear. More maintenance.
- **Neither for now:** Correct when direct interviews or outbound are faster than public content.

### State Uncertainty

If the state is unknown, do not invent state-specific registration, tax, or license SOPs. Generate validation work and a state-selection decision matrix. Block state-specific SOPs until the user chooses the operating or registration state.
