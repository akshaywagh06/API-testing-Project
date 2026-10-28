# Investigation register

These are observations from Akshay Wagh’s 28 October 2026 run, not maintainer-confirmed product defects. Status for each: **Recorded; fresh-data reproduction pending**. Response bodies and detailed assertion errors were not supplied. Severity and priority are not assigned before causes and impact are verified.

| ID | Observation | Evidence | Classification and next check |
|---|---|---|---|
| OBS-001 | Token-based successful writes/deletes returned 403; 52 main cleanup assertions and all 10 data cleanup checks failed | API-061–063, 065–071, 079, 081–082; main/data reviewed exports | Execution/authentication investigation. Clear runtime variables and cookie jar, obtain a fresh token, inspect resolved Cookie header; compare one owned-record mutation against Basic auth. Cleanup status itself is missing. |
| OBS-002 | Saved decimal price equality failed in main case and data iteration 5 | API-027; data iteration 5 | Contract/value investigation. Capture submitted and saved numbers on a fresh booking; do not infer the saved value from a Boolean failure. |
| OBS-003 | Checkout filter omitted the owned booking according to the assertion | API-015 | Filter investigation. Save setup booking dates/ID and resolved query; compare documented filter semantics and concurrent resets. |
| OBS-004 | Missing, null and selected invalid fields returned HTTP 500 | API-033–043, 047, 053–054 | Error-handling observation; exact 4xx response is tester-proposed. Repeat representative partitions and capture body. |
| OBS-005 | Thirteen exploratory invalid inputs returned 200 rather than proposed rejection | API-044–046, 048–052, 055–059 | Proposed validation improvements, not automatically documented-contract defects. Capture saved values and verify which rules provider promises. |
| OBS-006 | Created schema checks failed | API-044, 045, 055 | Schema observation; these inputs are deliberately invalid. Capture returned fields/type before diagnosing coercion. |
| OBS-007 | Later-dates data iteration failed read-back availability | Data iteration 9 | Environment/persistence investigation. Read-back status and error missing; transport failure, missing record or reset not distinguished. |
| OBS-008 | Unsupported request media type returned HTTP 500 | API-085 | Content-type/error-handling observation. Capture exact request headers/body and response on a fresh repeat. |

## Reproduction record template

For each candidate, record case ID, date/tool, fresh owned setup data, method and URL, resolved headers with secrets redacted, submitted body, expected result and requirement source, actual response status/body, read-back evidence and cleanup outcome. Add a second-run result, classification and proposed impact. 

Primary sources: [main export](../evidence/requests-responses/2026-10-28-main-reviewed.json), [data export](../evidence/requests-responses/2026-10-28-data-reviewed.json), and the unchanged collection definitions. Downstream failures can share one cause; 160 failed assertions do not mean 160 defects.
