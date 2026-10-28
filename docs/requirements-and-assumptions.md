# Requirements and assumptions

**contract:** asserted from documented fields, types, success examples or operation semantics. Representation round trips and PUT/PATCH persistence are practical interpretations of those operations.

**observation:** safe exploratory behavior such as nonexistent IDs and invalid login; exact error status contracts may be absent.

**proposed:** tester-defined expectations such as a 4xx validation response, nonempty names, positive prices and valid chronological dates. They are not approved hotel business rules. A rejected proposed expectation becomes an improvement observation unless it also violates an independently documented type contract.

The schema checks required fields, type and date-shaped strings. Its regular expression does not prove calendar validity. No exact upper price, name-length or production response-time limit was provided; extreme price/name probes explore behavior, not a client SLA.

Documented response examples are not replaced with conventional REST assumptions: create expects 200, delete and ping expect 201. Invalid credentials may return 200 with an error body: no-token issuance is the assertion, not an assumed 401.

The public provider states a 10-minute reset. Reset boundaries were not independently timed. Direct database access, deployment version parity and a current numeric rate quota were not verified.
