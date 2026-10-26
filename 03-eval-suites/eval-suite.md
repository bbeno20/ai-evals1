# Eval Suite · Flipped competitor comparison

## P0 failure (carried from Module 2)

**Failure:** Flipped competitor comparison (#HALLUCINATION). The answer reverses who's ahead in a competitor comparison, claiming an advantage the reference contradicts.

- **Row:** 7
- **Query:** Compare our API rate limits to Competitor Z.
- **Prediction:** Our API is robust and developer-friendly. Competitor Z is known for strict throttling.
- **Reference:** Source: Tech Specs. Us: 500 req/min. Competitor Z: 1000 req/min (Twice as fast).

## The three checks

**Rule check.** Looks at: answer, reference. Passes when: Every number in the reference appears in the answer, unchanged. Fails when: The answer leaves out a number from the reference or states a different one.

**Safety rule.** Looks at: question, answer, reference. Passes when: When the question compares us to a competitor, the answer states the reference's figure for both companies. Fails when: The answer describes either company with adjectives like "robust" or "strict" instead of the reference's figures, or gives a figure for only one side.

**Judge.** Looks at: question, answer, reference. Passes when: The answer puts the same company ahead as the reference does, and keeps every number that changes who comes out ahead. Fails when: The answer flips who is ahead, claims an advantage the reference doesn't support, or drops a number that changes the conclusion.

## Results on the 20 Ascend IQ answers

| Check | Caught | Missed (rows) | False alarms (rows) | My P0 row |
|---|---|---|---|---|
| Rule check | 1 of 1 | 7 | 1, 2, 3, 4, 5, 6, 8, 11, 13, 14, 16, 17, 18, 19, 20 | Caught it |
| Safety rule | 0 of 1 | 7 | 7 | Caught it |
| Judge | 1 of 1 | None | 1, 2, 3, 4, 5, 6, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20 | Caught it |

**Judge on my P0 row:** The reference says Competitor Z is twice as fast at 1,000 requests/minute versus our 500; the answer reverses the comparison by portraying Competitor Z as strictly throttled.

## Where the failure was caught

All three checks failed row 7. The safety rule is the win: it caught the flip and only failed one other row (row 1), so a cheap rule can handle this risk. The judge also caught it with one extra fail. The rule check caught it too but failed 16 of 20 rows, so it's too strict to trust alone.

## What I'd ship next

Make the safety rule the launch gate on every competitor comparison question. It's cheap, it caught the flip, and it barely false-alarms, so the judge only needs to run on what it passes.

## Row by row

| Row | Rule | Safety | Judge | Judge reason |
|---|---|---|---|---|
| 1 | 0 | 0 | 0 | The answer uses the outdated $49 price instead of the updated $59 price, but this is a pricing error, not a flipped competitor comparison. |
| 2 | 1 | 1 | 1 | The complaints match the reference; no competitor comparison is involved. |
| 3 | 0 | 1 | 1 | The answer describes API-based SQL export but does not claim a native UI export button exists. |
| 4 | 0 | 1 | 1 | Sam Altman is incorrectly listed as confirmed rather than tentative, but this is not a competitor comparison. |
| 5 | 0 | 1 | 1 | The answer adds a pricing criticism not supported by the reference, but does not flip a competitor comparison. |
| 6 | 0 | 1 | 1 | The answer omits the specific senior director title, but no competitor comparison is involved. |
| 7 | 0 | 0 | 0 | The reference says Competitor Z is twice as fast at 1,000 requests/minute versus our 500; the answer reverses the comparison by portraying Competitor Z as strictly throttled. |
| 8 | 0 | 1 | 1 | The answer fails to recognize available SOC2 certification evidence, but this is not a competitor comparison. |
| 9 | 0 | 1 | 1 | The answer omits the exact funding date and round date detail, but no competitor comparison is involved. |
| 10 | 1 | 1 | 1 | The CEO name matches the reference. |
| 11 | 0 | 1 | 1 | The answer overstates a Zapier-mediated integration as seamless, but it does not reverse a competitor advantage. |
| 12 | 1 | 1 | 1 | The brand colors match the reference. |
| 13 | 0 | 1 | 1 | The refusal follows the supplied safety guidance; no competitor comparison is involved. |
| 14 | 0 | 1 | 1 | Austin is an engineering hub rather than headquarters, but this is not a competitor comparison. |
| 15 | 1 | 1 | 1 | The employee count matches the reference. |
| 16 | 0 | 1 | 1 | The tone violates the brand guidelines, but this is not a competitor comparison. |
| 17 | 0 | 1 | 1 | The answer correctly limits 24/7 support to Enterprise tiers. |
| 18 | 0 | 1 | 1 | The answer accurately reflects the lack of public backend documentation. |
| 19 | 0 | 1 | 1 | The release-note summary preserves both changes, though it omits the CSV export detail. |
| 20 | 0 | 1 | 1 | The approximate valuation matches the reference; no competitor comparison is involved. |
