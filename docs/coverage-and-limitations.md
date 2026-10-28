# Coverage and limitations

## Designed coverage — personal run recorded
GET/POST/PUT/PATCH/DELETE, query/path parameters, JSON fields and nested dates, token Cookie and Basic auth, missing/invalid token denial, positive/negative/boundary partitions, JSON Schema, JSON/XML negotiation, read-after-write, unchanged fields, deletion, repeated PUT/DELETE, dynamic variables, asynchronous setup callbacks, CSV/JSON-ready data design and JSON iteration runs.

## Limited or outside collection scope
- Filters: name combinations and representative lower-bound dates; exact equality boundaries, malformed date filters and case sensitivity are not exhaustive.
- XML: read representation and create round trip only, not every XML update combination. Form encoding not executed.
- Response time: runner timing can be recorded; no asserted SLA or load model.
- CI: smoke workflow is configured; hosted execution and  Newman results are unverified.
- Negative validation: representative inputs; no exhaustive combinatorial coverage.


## Interview reference only
JWT/OAuth/refresh sessions, pagination/sorting, roles and object-level authorization, SQL/database validation, rate-limit 429 contracts, idempotency keys, SOAP/GraphQL, webhooks/queues, consumer-driven contracts and mocks, load/stress/security assessments. This API does not expose the needed contracts or access for those claims.


