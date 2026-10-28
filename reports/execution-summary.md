# Personal execution summary

**Executed by Akshay Wagh on 28 October 2026.** This report uses his uploaded Postman exports and screenshots. No new API execution was performed while preparing this revision.

## Recorded results

| Measure | Main collection | Data-driven collection |
|---|---:|---:|
| Iterations | 1 | 10 |
| Distinct case/request definitions | 85 | 1 |
| Primary request executions | 85 | 10 |
| Cases/iterations with no failed assertions | 16 | 0 |
| Cases/iterations with at least one failed assertion | 69 | 10 |
| Assertions passed | 331 | 92 |
| Assertions failed | 148 | 12 |
| Assertions executed | 479 | 104 |
| Blocked / Not Run primary cases | 0 / 0 | 0 / 0 |

Combined assertion executions: **583 (423 passed, 160 failed)**. Do not confuse assertion totals with case totals or defect counts. These records contain 95 primary executions; the total including script-issued setup/read-back/cleanup traffic cannot be verified from the exports.

## Environment and timing

- Service: https://restful-booker.herokuapp.com — public shared practice API.
- Postman for Windows 11.110.0, UI 11.110.0-ui-260812-0631, desktop platform 11.99.0; x64; OS platform win32 10.0.26300 (version screenshot).
- Main start: 2026-10-28 09:23:57.205 UTC (14:53:57.205 IST); export timestamp: 09:26:11.554 UTC. Screenshot duration: 2m 14s. Export request delay: 750 ms.
- Data start: 2026-10-28 09:20:41.045 UTC (14:50:41.045 IST); export timestamp: 09:20:57.677 UTC. Screenshot duration: 16s 632ms. Export request delay: 0 ms.
- `timestamp` is preserved as labelled in the export, not asserted to be an independently verified end time. `totalTime` is summed primary response timing, not full run duration.
- Screenshots show zero runner errors; that does not mean zero assertion failures.
- Hosted GitHub Actions and local Newman execution remain unverified for this personal run.

## Main-run interpretation

52 cleanup assertions failed. Intended token-based PUT/PATCH operations and deletion returned 403, while Basic-auth replacement, patch and deletion returned expected success statuses. This suggests an authentication/session or request-configuration issue, but the exports do not establish its cause. Do not report each downstream equality or schema failure as a separate product defect.

15 primary requests returned 500. Thirteen exploratory invalid-input cases returned 200 instead of the proposed 4xx expectation. API-015 failed the checkout-filter inclusion check. API-027 failed saved-price equality. Actual saved values and response bodies are unavailable.

## Data-file reconciliation

Akshay confirms using the data file supplied in the previous version. The repository retains that original 10-row `test-data/create-bookings.json`. The export does not embed the selected file or resolved request bodies, so row labels are mapped by original order with that limitation stated.

All ten create-status assertions passed at 200, and all ten created-response schema assertions passed. **This uploaded data run does not show the earlier 400 response.** A separate earlier execution is not incorporated as this run’s result.

All ten cleanup checks failed. Iteration 5 also failed price equality; iteration 9 failed read-back availability. The sixth-field comparisons for iteration 9 were not generated because the read-back branch did not run: six comparisons absent, not passed or recorded as skipped by Postman. Nine iterations have 11 assertions; iteration 9 has 5, giving 104.

The template appends a run tag to firstname and sends an empty additionalneeds string when the row omits that field. Thus row 2 does not demonstrate omission of the optional field in the outgoing request.

## Evidence and release judgement

[Main reviewed export](../evidence/requests-responses/2026-10-28-main-reviewed.json) · [Data reviewed export](../evidence/requests-responses/2026-10-28-data-reviewed.json) · [Screenshots](../evidence/screenshots/) · [Investigation register](../bug-reports/findings.md) · [Data iterations](data-driven-results.md).

Execution records are complete for the supplied primary runs; investigation is incomplete. The portfolio can demonstrate an actual run and failure analysis, but must not claim all tests passed, confirmed defects, successful cleanup, a completed token-auth lifecycle or verified CI. Retest candidates on fresh owned data before promoting observations to confirmed findings.

