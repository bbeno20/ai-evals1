# Ascend IQ Failure Audit

9 confirmed failures: #HALLUCINATION ×7, #UX_TRUST ×1, #ROBUSTNESS ×1, #FAIRNESS ×0. I changed 1 of the judge’s calls.

| Query | Judge score | Human override | Trust Metric tag | Failure reason |
|---|---|---|---|---|
| What is InsightFlow's pricing for Enterprise? | 0 |  | #HALLUCINATION | The answer uses outdated pricing; the reference states, “New Price (Updated yesterday): $59/mo.” |
| Summarize the top 3 complaints from DataViz's G2 reviews. | 1 |  |  |  |
| Does InsightFlow support native SQL export? | 0 |  | #HALLUCINATION | The answer incorrectly implies native SQL export support; the reference states, “there is no ‘Native Export’ button in the UI.” |
| List the confirmed speakers for SaaStr. | 0 |  | #HALLUCINATION | The answer incorrectly lists Sam Altman as confirmed; the reference states, “Sam Altman is listed as ‘Invited/Tentative.’” |
| What is the sentiment of the latest TechCrunch article on us? | 1 | 0 #HALLUCINATION, Should fail as #HALLUCINATION. The answer invents a pricing criticism that isn't in the reference, which only gives a Neutral/Positive sentiment. | #HALLUCINATION |  |
| Give me a bio for Sarah Jenkins, the new VP at DataViz. | 1 |  |  |  |
| Compare our API rate limits to Competitor Z. | 0 |  | #HALLUCINATION | The answer misrepresents Competitor Z's rate limit as slower; the reference states, “Competitor Z: 1000 req/min (Twice as fast).” |
| Is Competitor X SOC2 compliant? | 0 |  | #ROBUSTNESS | The agent refuses to answer despite available evidence; the reference states, “‘SOC2 Type II Certified’ badge visible.” |
| When was InsightFlow's last funding round? | 1 |  |  |  |
| Who is the CEO of DataViz? | 1 |  |  |  |
| Does Competitor Y integrate with HubSpot? | 0 |  | #HALLUCINATION | The answer overstates the integration as seamless and direct; the reference states, “HubSpot integration available via Zapier partnership.” |
| What are the primary brand colors for InsightFlow? | 1 |  |  |  |
| Summarize the lawsuit mentioned in the WSJ about Competitor Z. | 1 |  |  |  |
| List the HQ locations for DataViz. | 0 |  | #HALLUCINATION | The answer incorrectly identifies Austin as an HQ location; the reference states, “HQ: San Francisco. Engineering Hub: Austin.” |
| How many employees does InsightFlow have? | 1 |  |  |  |
| Draft a cold email about our new feature. | 0 |  | #UX_TRUST | The answer uses unprofessional slang contrary to the brand voice; the reference states, “Tone: Confident, professional, expert. Avoid slang.” |
| Does Competitor X offer 24/7 support? | 1 |  |  |  |
| What database backend does DataViz use? | 1 |  |  |  |
| Summarize the latest release notes for InsightFlow. | 1 |  |  |  |
| What is the market cap of Competitor Z? | 1 |  |  |  |
