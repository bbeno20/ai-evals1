# Module 4 · Launch Strategy · Ascend IQ Copilot

## 4.0 Release Criteria

| Gate | Failure | Metric | Threshold | Dataset | Method | Runs at |
|---|---|---|---|---|---|---|
| Hard | Flipped competitor comparison (#HALLUCINATION) | Share of competitor comparison answers that state the reference figure for both companies | 100% of competitor comparison answers pass the safety rule. Zero flipped comparisons allowed at launch. | Ascend IQ golden set | Code-based check | Release |
| Soft | Row 5 · Hallucination: lists an unconfirmed speaker as confirmed | Share of answers that list a person as confirmed when the reference says invited or tentative | 0% | Ascend IQ golden set | LLM judge | Staging |
| Advisory | Row 3 · Latency: exceeded the maximum response time | P95 response time on the golden set | Less than 2.0 seconds | Ascend IQ golden set | Code-based check | Staging |

## CI Gate Request for Engineering

- **Hard gate · Flipped competitor comparison (#HALLUCINATION).** Check: the code-based check, run on the Ascend IQ golden set at Release. Measures: Share of competitor comparison answers that state the reference figure for both companies. Passes when: 100% of competitor comparison answers pass the safety rule. Zero flipped comparisons allowed at launch.. On a fail: block the release.
- **Soft gate · Row 5 · Hallucination: lists an unconfirmed speaker as confirmed.** Check: the LLM judge, run on the Ascend IQ golden set at Staging. Measures: Share of answers that list a person as confirmed when the reference says invited or tentative. Passes when: 0%. On a fail: pause the release until the PM signs off on an override.
- **Advisory gate · Row 3 · Latency: exceeded the maximum response time.** Check: the code-based check, run on the Ascend IQ golden set at Staging. Measures: P95 response time on the golden set. Passes when: Less than 2.0 seconds. On a fail: post a warning, and don't block.

## Mitigation Plan · Soft Gate

If our Soft gate fails (it says a speaker is confirmed when they're not), I'd launch to just 5 of our top 50 accounts first. That way only a few clients see it while we gather more data, and we pull it back if the mistake shows up again.
