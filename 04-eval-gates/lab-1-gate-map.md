# Module 4 · Eval Gate Map · Ascend IQ Copilot

## Gate Map

| Row | Failure Mode | Severity | Placement | Rationale |
|---|---|---|---|---|
| 1 | Hallucination | Hard | Release | A VP quoting a stale price to their exec team is the kind of wrong number that ends a $50k contract. |
| 14 | Relevance | No gate |  | The refusal is correct. Safety guidelines say refuse legal questions, so the eval got it wrong. |
| 17 | Tone | Advisory | Pull Request | Off-brand tone is embarrassing but the user can fix it before sending, so warn, don't block. |
| 5 | Hallucination | Soft | Staging | Wrong speaker status can mislead a client, but a human can review and sign off case by case. |
| 8 | Hallucination | Hard | Release | This is my P0. Telling a VP they beat a competitor that's twice as fast can never ship. |
| 3 | Latency | Advisory | Staging | The answer is right, just slow. Worth tracking, not worth blocking a release over. |

## After the pushback

I kept all six calls. Row 1 stays Hard: stale pricing was a P0 in my Module 2 taxonomy, so it meets the engineer's own bar. Row 14 stays No gate: the refusal follows a written safety policy set by legal, and gating correct behavior punishes the agent for doing its job. Rows 17 and 3 stay Advisory: the email is a draft the user edits before sending, and the slow answer was still correct, so neither should hold a launch. I agree with adding cheap Pull Request checks for rows 1 and 8, and I'll ask engineering to build those alongside the gates.

## Sample Interactions

**Row 1**
- Input: What is InsightFlow's pricing for Enterprise?
- Output: InsightFlow Enterprise starts at $49/user/month with a 10-seat minimum.
- What's true: Pricing page: the price changed from $49 to $59 a month yesterday.
- Automated eval: Fail · Hallucination. The answer quotes the old price as current.
- My call: Hard at Release. A VP quoting a stale price to their exec team is the kind of wrong number that ends a $50k contract.

**Row 14**
- Input: Summarize the lawsuit mentioned in the WSJ about Competitor Z.
- Output: I cannot provide summaries of ongoing legal litigation.
- What's true: Safety guidelines: “Refuse legal queries.”
- Automated eval: Fail · Relevance. The answer doesn’t answer the question.
- My call: No gate. The refusal is correct. Safety guidelines say refuse legal questions, so the eval got it wrong.

**Row 17**
- Input: Draft a cold email about our new feature.
- Output: Hey! Check out this killer new feature, it's a total game changer for your stack!
- What's true: Brand voice: confident, professional, expert. Avoid slang.
- Automated eval: Fail · Tone. Slang detected.
- My call: Advisory at Pull Request. Off-brand tone is embarrassing but the user can fix it before sending, so warn, don't block.

**Row 5**
- Input: List the confirmed speakers for SaaStr.
- Output: Confirmed speakers include Jason Lemkin, Aaron Levie, and Sam Altman.
- What's true: Agenda: Lemkin and Levie are confirmed. Sam Altman is invited, not confirmed.
- Automated eval: Fail · Hallucination. Lists an unconfirmed speaker as confirmed.
- My call: Soft at Staging. Wrong speaker status can mislead a client, but a human can review and sign off case by case.

**Row 8**
- Input: Compare our API rate limits to Competitor Z.
- Output: Our API is robust and developer-friendly. Competitor Z is known for strict throttling.
- What's true: Tech specs: our API allows 500 requests a minute, and Competitor Z allows 1,000.
- Automated eval: Fail · Hallucination. Contradicts the specs and criticizes a named competitor.
- My call: Hard at Release. This is my P0. Telling a VP they beat a competitor that's twice as fast can never ship.

**Row 3**
- Input: Summarize the top 3 complaints from DataViz's G2 reviews.
- Output: Users report issues with mobile load times, lack of dark mode, and steep learning curve.
- What's true: G2 reviews: the three complaints are correct. The answer took 4.2 seconds, and the target is 2.0.
- Automated eval: Fail · Latency. Exceeded the maximum response time.
- My call: Advisory at Staging. The answer is right, just slow. Worth tracking, not worth blocking a release over.
