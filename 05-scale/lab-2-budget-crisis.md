# Module 5 · Eval Budget · Ascend IQ

**Quarterly budget cap:** $200,000
**Online eval spend:** $155,000 (2 of at most 3 online evals)

## Budget

| Failure | Trust metric | Risk | Level | Cost |
| --- | --- | :---: | :---: | ---: |
| Data Fabrication | Hallucination Rate | P0 | Online eval | $85,000 |
| Context Specificity | Robustness | P1 | Online eval | $70,000 |
| Overconfident Tone | UX Trust | P1 | Periodic audit | $6,500 |
| Data Bias | Fairness | P2 | Periodic audit | $5,500 |
| Slow Answers | Latency | P3 | Code-based check | $1,250 |

## Downgrades

### Periodic audit · Overconfident Tone (UX Trust · P1)
- **Cheaper check:** Every week, look at 50 answers and flag any that sound sure but have no source.
- **Why it’s enough:** If it keeps happening, a weekly check will spot it. The online fabrication check already catches the guesses that are actually wrong.

### Periodic audit · Data Bias (Fairness · P2)
- **Cheaper check:** Compare APAC and US answers once a week.
- **Why it’s enough:** Most clients ask about the US, so this rarely matters.

### Code-based check · Slow Answers (Latency · P3)
- **Cheaper check:** A timer that flags anything over 10 seconds.
- **Why it’s enough:** Slow answers are annoying, not wrong.
