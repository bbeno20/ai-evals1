# AI Evaluation Strategy Canvas

> Repo file `ai-evals/01-evaluation-strategy/strategy-canvas.md` (the repo is your submission).

## 1. Product Strategy, The Context

**Who it's for:** VP-level strategists and product leaders at Fortune 500 companies who pay upward of $50,000 a year for verified market intelligence.

**What they use it for:** Asking plain-language questions, like “Compare the pricing models of Stripe and Adyen,” and getting answers in seconds instead of digging through the platform.

**What's at stake:** Engagement is dropping, Q4 retention is at risk, and the CPO wants Ascend IQ live for the top 50 enterprise accounts next month. One poor answer to the wrong client can do lasting damage to the relationship.

## 2. Measurements, The Execution

**User promise.** For VP-level strategists at Fortune 500 companies, Ascend IQ promises competitive intelligence they can trust without fact-checking, delivered in seconds, so the top 50 enterprise accounts stay engaged and renew through Q4.

**Top 3 trust metrics:**
- **Hallucination Rate**, % of outputs that are confidently false or fabricated.
- **Robustness**, Coherence on messy, adversarial, out-of-scope inputs.
- **UX Trust**, Subjective predictability and consistency over time.

**Why these three:** - Hallucination Rate: these clients pay $50k+ a year for verified intel, so one made-up number to the wrong account can end the relationship.
- Robustness: VPs ask vague, messy questions, not clean ones. If quality falls apart on a sloppy prompt, it fails when they need it most.
- UX Trust: a VP has to get the same answer to the same question today and next week. Inconsistency reads as unreliable, and they quietly stop using it.

## 3. Strategic Trade-Offs, The Cost

### Trade-off 1 · Hallucination Rate ↔ Robustness
We prioritize Hallucination Rate over Robustness because a confident wrong answer is worse than a weak answer on a messy question. A VP can work with "I'm not sure," but a made-up number in front of a top-50 account does lasting damage.

### Trade-off 2 · Hallucination Rate ↔ UX Trust
We prioritize Hallucination Rate over UX Trust because being consistent means nothing if the answer is wrong. I'd rather it be occasionally uneven than smoothly confident about something false.

---
_Generated from the AI Evaluation Strategy Canvas, M1 lab tool, AI Evals Certification._
