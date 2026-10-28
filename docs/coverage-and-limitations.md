# Coverage and limitations

## Designed coverage — personal run recorded
GET/POST/PUT/PATCH/DELETE, query/path parameters, JSON fields and nested dates, token Cookie and Basic auth, missing/invalid token denial, positive/negative/boundary partitions, JSON Schema, JSON/XML negotiation, read-after-write, unchanged fields, deletion, repeated PUT/DELETE, dynamic variables, asynchronous setup callbacks, CSV/JSON-ready data design and JSON iteration runs.

## Limited or outside collection scope
- Filters: name combinations and representative lower-bound dates; exact equality boundaries, malformed date filters and case sensitivity are not exhaustive.
- XML: read representation and create round trip only, not every XML update combination. Form encoding not executed.
- Response time: runner timing can be recorded; no asserted SLA or load model.
- CI: smoke workflow is configured; hosted execution and personal Newman results remain unverified.
- Negative validation: representative inputs; no exhaustive combinatorial coverage.
- Setup callbacks are asynchronous Postman scripting, not proof of an asynchronous server/job API.

## Interview reference only
JWT/OAuth/refresh sessions, pagination/sorting, roles and object-level authorization, SQL/database validation, rate-limit 429 contracts, idempotency keys, SOAP/GraphQL, webhooks/queues, consumer-driven contracts and mocks, load/stress/security assessments. This API does not expose the needed contracts or access for those claims.

Use an owned deployment or separate documented companion API for later practical coverage. No claim that this one project covers every possible interview or establishes senior-level proficiency by itself.

## What this personal run establishes
All 85 primary cases and ten data iterations have exported assertion records. Token-based positive mutations returned 403, so this run does not establish a successful token-auth lifecycle. Basic-auth mutations returned expected statuses. Cleanup failed repeatedly. Reviewed exports omit response bodies and input snapshots; findings are observations pending reproduction. [Summary](../reports/execution-summary.md).
