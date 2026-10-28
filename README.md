# Restful Booker API Testing

**Portfolio owner: Akshay Wagh**

Postman testing project for the public [Restful Booker booking API](https://restful-booker.herokuapp.com/). The collection checks authentication, booking CRUD operations, filters, response schemas, invalid inputs and saved data.

## Execution status

**Personally executed by Akshay Wagh in Postman for Windows 11.110.0 on 28 October 2026.**

| Run | Case/iteration outcomes | Assertion outcomes |
|---|---|---|
| Main: 85 cases, one iteration | 16 Pass / 69 Fail | 331 Pass / 148 Fail (479) |
| Data: one request, ten iterations | 0 Pass / 10 Fail | 92 Pass / 12 Fail (104) |

Outcomes include cleanup failures. They are not confirmed-defect totals. The main failures include token-based operations returning 403; Basic-auth operations succeeded. Root-cause investigation and fresh-data reproduction remain pending. [Execution summary](reports/execution-summary.md) · [Investigation register](bug-reports/findings.md) · [Data results](reports/data-driven-results.md).

The uploaded runs, not historical results, are the source for these numbers. Documentation was reconciled from supplied evidence; no new service run was performed for this revision.

This is a practice project, not a production client assessment.

## Test approach

Every update or delete uses a booking created by that test. Tokens and booking IDs are captured at runtime. After a write, a GET request checks the saved values; after a denied update, a read checks that the data stayed unchanged.

Expected results have three labels:
- **contract:** based on documented fields, types and operation behavior;
- **observation:** exploratory checks where the error contract is incomplete;
- **proposed:** sensible validation rules that the provider has not explicitly promised.

An assertion failure is not automatically a confirmed defect. Reproduce it on a fresh booking and record its requirement basis first.

## Run in Postman

1. Import both JSON files from `collections/` and the environment from `environments/`.
2. Select **Restful Booker public practice**.
3. Run the **Smoke** folder first. It checks reachability, not a complete booking workflow.
4. Run the main collection in Collection Runner, with a 750 ms delay and one iteration.
5. Run the data-driven collection separately using `test-data/create-bookings.json` as its iteration data.
6. Export results and capture sanitized responses for failures; keep retests separate from the recorded run.

Start each new run with runtime collection variables (`token`, `runTag`, owned IDs) cleared and review the Postman cookie jar. If an intended protected operation returns 403, investigate token/header and cookie state before treating later saved-value checks as separate defects. This is a troubleshooting step, not a verified fix.

Postman assertions use JavaScript. No separate Java or Python framework is needed for this project.

## Run with Newman

Install Node.js 22 LTS, then open a terminal in this folder:

```sh
npm ci
npm run test:smoke
npm run test:regression
npm run test:exploratory
npm run test:data
```

Regression and exploratory are separate folder selections; together they cover the main collection. The data run is separate. Commands return a nonzero exit code when assertions fail. Do not suppress that exit code or weaken an expectation to make a report green.

To save a complete personal run locally:

```sh
npx newman run collections/restful-booker.postman_collection.json -e environments/public-practice.postman_environment.json --delay-request 750 --timeout-request 20000 --reporters cli,json,junit --reporter-json-export reports/latest-full.json --reporter-junit-export reports/latest-full.xml
npx newman run collections/data-driven.postman_collection.json -e environments/public-practice.postman_environment.json -d test-data/create-bookings.json --delay-request 750 --timeout-request 20000 --reporters cli,json,junit --reporter-json-export reports/latest-data.json --reporter-junit-export reports/latest-data.xml
```

Raw exports can contain tokens and authentication headers. They are ignored by Git but must also be excluded from browser uploads. Only add reviewed, redacted copies under `evidence/requests-responses/`.

## Files

| Folder | Contents |
|---|---|
| `collections/` | Main collection and data-driven collection |
| `environments/` | Public base URL, without captured tokens |
| `test-data/` | Synthetic booking rows |
| `schemas/` | Booking response schema |
| `docs/` | Plan, endpoint inventory, traceability and scope limits |
| `test-cases/` | 85-case workbook, CSV and detailed case steps |
| `bug-reports/` | Evidence-backed observations and reproduction checklist |
| `reports/` | Personal execution summary and data iteration results |
| `evidence/` | Reviewed assertion exports and run/version screenshots |
| `.github/workflows/` | Manually triggered smoke workflow |

[Cases](test-cases/test-cases.md) · [Test plan](docs/test-plan.md) · [Traceability](docs/traceability-matrix.md) · [Scope limits](docs/coverage-and-limitations.md)

## Public-service limits

The provider states that shared data resets every 10 minutes. Use serial runs and only synthetic records created by the collection. A reset or another tester's activity can affect results. Record interference separately and investigate before calling it a defect.

The collection uses best-effort cleanup; an already absent ID does not prove whether deletion or a reset removed it. No load tests, brute force or intrusive security checks are in scope.


## Sources

[Provider homepage](https://restful-booker.herokuapp.com/) · [Official API documentation](https://restful-booker.herokuapp.com/apidoc/) · [Endpoint definitions](https://restful-booker.herokuapp.com/apidoc/api_data.json)
