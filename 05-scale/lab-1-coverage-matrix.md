# Module 5 · Coverage Matrix · Competitor Signal Tracker

## Coverage Row

| Product | Hallucination Rate | Fairness | Latency | UX Trust | Robustness |
|---|---|---|---|---|---|
| Competitor Signal Tracker | ❌ Gap | ❌ Gap | ✅ Covered | ✅ Covered | ❌ Gap |

## What Runs Today

- A timer alerts if the nightly scoring run takes more than 2 hours.
- A style check flags summaries written in a casual or alarmist tone before they reach the sales team.

## Accepted Gap

**Fairness.** We accept this gap because it's an internal tool used by our own sales and strategy teams, and most of the news and posts it scores are in English from US sources. A fairness audit would cost more than the risk right now.

We’ll look again: We'll look again if it starts scoring non-English sources or if its output ever goes to clients, or at the next quarterly eval budget review.

## Critical Gap

We've flagged Hallucination Rate as the most critical gap for Competitor Signal Tracker because nothing checks if a summary matches its source. A misread price cut ends up on a client call, and the client catches it, costing us credibility and deals. We'll close it with an LLM judge that checks a weekly sample of summaries against their sources, after first testing the judge against 50 human-reviewed examples. If more than 5% of a weekly sample fails, the strategy lead reviews before summaries go out.

## After the Pressure Test

I kept my marks and my accepted gap, but tightened the hallucination plan. The reviewer was right that an untested LLM judge is just another unchecked AI, so I added a step to validate it against human-reviewed examples first, plus a 5% failure threshold and an owner who acts on it.
