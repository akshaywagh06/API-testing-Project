# Data-driven iteration results

Akshay confirms using the supplied 10-row JSON file. Labels below follow its original order; the run export does not preserve iteration input snapshots. All create-status assertions passed at HTTP 200; the export preserves only one response-code summary, not individual response bodies.

| Iteration | Original row label | Pass assertions | Fail assertions | Outcome | Failed checks |
|---|---|---:|---:|---|---|
| 1 | Standard booking | 10 | 1 | Fail | Cleanup: owned record removed or already absent |
| 2 | No optional additional needs | 10 | 1 | Fail | Cleanup: owned record removed or already absent |
| 3 | Deposit false | 10 | 1 | Fail | Cleanup: owned record removed or already absent |
| 4 | Integer price | 10 | 1 | Fail | Cleanup: owned record removed or already absent |
| 5 | Decimal price | 9 | 2 | Fail | Saved totalprice equals submitted value; Cleanup: owned record removed or already absent |
| 6 | Unicode name | 10 | 1 | Fail | Cleanup: owned record removed or already absent |
| 7 | Spaces in name | 10 | 1 | Fail | Cleanup: owned record removed or already absent |
| 8 | Longer name | 10 | 1 | Fail | Cleanup: owned record removed or already absent |
| 9 | Later dates | 3 | 2 | Fail | Read-back: saved booking available; Cleanup: owned record removed or already absent |
| 10 | Empty optional needs | 10 | 1 | Fail | Cleanup: owned record removed or already absent |

Iteration 9 contains only five assertions. Six saved-field comparisons were not generated after read-back failed. Their absence is not a passing result.

[Reviewed export](../evidence/requests-responses/2026-10-28-data-reviewed.json).
