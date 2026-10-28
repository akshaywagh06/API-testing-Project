# Interview reference tied to this project

| Question | Answer and project anchor |
|---|---|
| How do you start testing an API? | Read contracts, identify risks, map endpoints and design data; see API inventory and traceability. |
| Is HTTP 200 sufficient? | No. API-027 compares a submitted decimal price with its saved value; success alone cannot prove that they match. Check body, types and saved state. |
| POST vs PUT vs PATCH? | POST creates; PUT replaces the submitted representation; PATCH changes selected fields. API-061–072 verify values and untouched fields. |
| Are all DELETE responses 204? | No. This provider documents 201. Assert the provider contract and discuss unusual conventions. |
| Path vs query parameter? | /booking/{id} identifies a resource; /booking?firstname=... filters an ID list. |
| Authentication vs authorization? | Auth identifies/validates access; authorization decides allowed operations. This shared API supports operation-level token checks, not demonstrated tenant roles. |
| Is this a JWT token? | No documented JWT format. Treat it as opaque; Cookie token and Basic auth are tested. |
| Basic auth security? | Base64 is encoding, not encryption. Use HTTPS; do not publish private credential values. |
| How do you chain requests? | Capture token and bookingid into collection variables; use callbacks for owned setup and read-back. |
| Collection vs environment variables? | Collection runtime variables hold run-specific IDs/token; environment holds baseUrl. Scope and cleanup matter. |
| Pre-request vs test scripts? | Pre-request prepares state/data; post-response checks actual behavior. Both must surface errors. |
| JSON Schema vs business validation? | Schema checks structure/types; calendar validity and date order need separate business assertions. |
| Positive vs negative tests? | Valid CRUD establishes baseline; wrong types/missing fields explore rejection and robustness. |
| Equivalence partitioning? | Group valid, missing, null, wrong-type and empty inputs; each is not automatically the same defect. |
| Boundary testing? | Numeric zero/negative/large values and dates around limits. Undocumented limits remain proposed, not approved rules. |
| How do you verify persistence without SQL? | GET the created/updated ID and compare values. This is API-level verification, not direct database validation. |
| What is idempotency? | Repetition has the same intended state effect. PUT repeats compare representations; repeat DELETE verifies absence, not identical status. |
| Content-Type vs Accept? | Content-Type labels request representation; Accept requests response format. JSON/XML checks and unsupported-media observations exercise this. |
| How do you diagnose failure? | Inspect request, response, assertion, setup and environment; reproduce on fresh owned data before classifying. |
| What is data-driven testing? | One collection executes independent rows; compare submitted and saved values for each row. |
| What does CI prove here? | Workflow can repeat smoke after upload; hosted execution is unverified now. One smoke case is not full regression. |
| Why not retry every failure? | Retries can hide defects; distinguish public reset/availability issues and record reruns explicitly. |
| What is a good bug report? | Contract/assumption basis, reproducible input, actual output, impact, environment, evidence and triage status. |
| Does timing equal performance testing? | No. Single-request latency is not concurrency/throughput capacity or an SLA. |
| What is not covered? | OAuth/JWT refresh, pagination, roles, SQL, rate limits and load/security need another supported or owned environment. |

## Further concepts—not executed here

- **OAuth 2.0:** delegated authorization flows, scopes, redirect/state validation; JWT is a token format, not OAuth itself. OIDC adds identity.
- **Pagination:** validate limits/offsets or cursors, boundary pages, duplicates and stable ordering using a supported contract.
- **Rate limits:** verify documented quota, 429 and Retry-After in an authorized controlled environment, not by flooding this service.
- **Idempotency keys:** same-key retries should not duplicate effects; conflicting payload behavior comes from the provider contract.
- **Consumer contracts:** Pact-style consumer/provider interactions differ from validating a single JSON response schema.
- **Mocks:** isolate unavailable dependencies, simulate failures and verify calls; passing a mock does not prove the live provider works.
- **SOAP/GraphQL:** SOAP needs XML/WSDL and fault checks; GraphQL may return HTTP 200 with errors and needs query-level assertions.
- **Async/webhooks:** test delivery signatures, retries, duplicates, eventual consistency and timeout states on a supported service.
- **Security:** authorization/tenant isolation, injection and resource consumption require explicit authorization and controlled data.
- **Load:** define realistic workload, concurrency, latency percentiles, throughput and error budgets; use an owned deployment.
