# API test cases

85 cases executed by Akshay Wagh in Postman on 28 October 2026: 16 Pass, 69 Fail. A case fails if any recorded assertion fails, including cleanup. Proposed expectations are not automatically provider defects. Exports retain assertion outcomes, not response bodies or detailed assertion errors.

## API-001 — Health check matches documented 201
- Suite: Smoke; requirement: REQ-01; expectation basis: **contract**.
- Request: `GET /ping`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `null`.
- Actual: Main response HTTP 201. Personal execution status: **Pass**.
- Recorded checks: Response received without server error; Documented status 201.
- Failed assertions: None recorded. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-001`.

## API-002 — Valid login returns a nonempty token
- Suite: Authentication; requirement: REQ-02; expectation basis: **contract**.
- Request: `POST /auth`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"username": "admin", "password": "password123"}`.
- Actual: Main response HTTP 200. Personal execution status: **Pass**.
- Recorded checks: Response received without server error; Nonempty authentication token.
- Failed assertions: None recorded. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-002`.

## API-003 — Wrong password
- Suite: Authentication; requirement: REQ-02; expectation basis: **observation**.
- Request: `POST /auth`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"username": "admin", "password": "wrong-qa"}`.
- Actual: Main response HTTP 200. Personal execution status: **Pass**.
- Recorded checks: Response received without server error; Invalid credentials never issue a token.
- Failed assertions: None recorded. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-003`.

## API-004 — Wrong username
- Suite: Authentication; requirement: REQ-02; expectation basis: **observation**.
- Request: `POST /auth`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"username": "not-a-user", "password": "password123"}`.
- Actual: Main response HTTP 200. Personal execution status: **Pass**.
- Recorded checks: Response received without server error; Invalid credentials never issue a token.
- Failed assertions: None recorded. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-004`.

## API-005 — Missing username
- Suite: Authentication; requirement: REQ-02; expectation basis: **observation**.
- Request: `POST /auth`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"password": "password123"}`.
- Actual: Main response HTTP 200. Personal execution status: **Pass**.
- Recorded checks: Response received without server error; Invalid credentials never issue a token.
- Failed assertions: None recorded. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-005`.

## API-006 — Missing password
- Suite: Authentication; requirement: REQ-02; expectation basis: **observation**.
- Request: `POST /auth`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"username": "admin"}`.
- Actual: Main response HTTP 200. Personal execution status: **Pass**.
- Recorded checks: Response received without server error; Invalid credentials never issue a token.
- Failed assertions: None recorded. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-006`.

## API-007 — Empty credentials
- Suite: Authentication; requirement: REQ-02; expectation basis: **observation**.
- Request: `POST /auth`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"username": "", "password": ""}`.
- Actual: Main response HTTP 200. Personal execution status: **Pass**.
- Recorded checks: Response received without server error; Invalid credentials never issue a token.
- Failed assertions: None recorded. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-007`.

## API-008 — Null credentials
- Suite: Authentication; requirement: REQ-02; expectation basis: **observation**.
- Request: `POST /auth`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"username": null, "password": null}`.
- Actual: Main response HTTP 200. Personal execution status: **Pass**.
- Recorded checks: Response received without server error; Invalid credentials never issue a token.
- Failed assertions: None recorded. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-008`.

## API-009 — Booking ID list has numeric IDs
- Suite: Read and filters; requirement: REQ-03 / REQ-04; expectation basis: **contract**.
- Request: `GET /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `null`.
- Actual: Main response HTTP 200. Personal execution status: **Pass**.
- Recorded checks: Response received without server error; Booking list contract.
- Failed assertions: None recorded. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-009`.

## API-010 — Read newly created booking
- Suite: Read and filters; requirement: REQ-03 / REQ-04; expectation basis: **contract**.
- Request: `GET /booking/{{ownedId}}`.
- Setup: create a fresh owned synthetic booking and capture ID/token.
- Input: `null`.
- Actual: Main response HTTP 200. Personal execution status: **Fail**.
- Recorded checks: Setup: fresh owned booking created; Response received without server error; Documented status 200; Booking schema; Read matches owned input; Cleanup: owned record removed or already absent.
- Failed assertions: Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-010`.

## API-011 — First name filter contains owned booking
- Suite: Read and filters; requirement: REQ-03 / REQ-04; expectation basis: **contract**.
- Request: `GET /booking?firstname={{ownedFirst}}`.
- Setup: create a fresh owned synthetic booking and capture ID/token.
- Input: `null`.
- Actual: Main response HTTP 200. Personal execution status: **Fail**.
- Recorded checks: Setup: fresh owned booking created; Response received without server error; Booking list contract; Filter includes freshly created booking; Cleanup: owned record removed or already absent.
- Failed assertions: Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-011`.

## API-012 — Last name filter contains owned booking
- Suite: Read and filters; requirement: REQ-03 / REQ-04; expectation basis: **contract**.
- Request: `GET /booking?lastname={{ownedLast}}`.
- Setup: create a fresh owned synthetic booking and capture ID/token.
- Input: `null`.
- Actual: Main response HTTP 200. Personal execution status: **Fail**.
- Recorded checks: Setup: fresh owned booking created; Response received without server error; Booking list contract; Filter includes freshly created booking; Cleanup: owned record removed or already absent.
- Failed assertions: Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-012`.

## API-013 — Both names filter contains owned booking
- Suite: Read and filters; requirement: REQ-03 / REQ-04; expectation basis: **contract**.
- Request: `GET /booking?firstname={{ownedFirst}}&lastname={{ownedLast}}`.
- Setup: create a fresh owned synthetic booking and capture ID/token.
- Input: `null`.
- Actual: Main response HTTP 200. Personal execution status: **Fail**.
- Recorded checks: Setup: fresh owned booking created; Response received without server error; Booking list contract; Filter includes freshly created booking; Cleanup: owned record removed or already absent.
- Failed assertions: Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-013`.

## API-014 — Check-in lower bound filter contains owned booking
- Suite: Read and filters; requirement: REQ-03 / REQ-04; expectation basis: **contract**.
- Request: `GET /booking?checkin=2026-11-09`.
- Setup: create a fresh owned synthetic booking and capture ID/token.
- Input: `null`.
- Actual: Main response HTTP 200. Personal execution status: **Fail**.
- Recorded checks: Setup: fresh owned booking created; Response received without server error; Booking list contract; Filter includes freshly created booking; Cleanup: owned record removed or already absent.
- Failed assertions: Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-014`.

## API-015 — Checkout lower bound filter contains owned booking
- Suite: Read and filters; requirement: REQ-03 / REQ-04; expectation basis: **contract**.
- Request: `GET /booking?checkout=2026-11-11`.
- Setup: create a fresh owned synthetic booking and capture ID/token.
- Input: `null`.
- Actual: Main response HTTP 200. Personal execution status: **Fail**.
- Recorded checks: Setup: fresh owned booking created; Response received without server error; Booking list contract; Filter includes freshly created booking; Cleanup: owned record removed or already absent.
- Failed assertions: Filter includes freshly created booking; Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-015`.

## API-016 — Unique unmatched name produces empty list
- Suite: Read and filters; requirement: REQ-03 / REQ-04; expectation basis: **contract**.
- Request: `GET /booking?firstname=QA_NO_MATCH_{{runTag}}`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `null`.
- Actual: Main response HTTP 200. Personal execution status: **Pass**.
- Recorded checks: Response received without server error; Booking list contract; No-match list is empty.
- Failed assertions: None recorded. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-016`.

## API-017 — Read nonexistent or malformed ID not-a-number
- Suite: Read and filters; requirement: REQ-03 / REQ-04; expectation basis: **observation**.
- Request: `GET /booking/not-a-number`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `null`.
- Actual: Main response HTTP 404. Personal execution status: **Pass**.
- Recorded checks: Response received without server error; Unknown ID is not a successful booking read.
- Failed assertions: None recorded. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-017`.

## API-018 — Read nonexistent or malformed ID 0
- Suite: Read and filters; requirement: REQ-03 / REQ-04; expectation basis: **observation**.
- Request: `GET /booking/0`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `null`.
- Actual: Main response HTTP 404. Personal execution status: **Pass**.
- Recorded checks: Response received without server error; Unknown ID is not a successful booking read.
- Failed assertions: None recorded. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-018`.

## API-019 — Read nonexistent or malformed ID -1
- Suite: Read and filters; requirement: REQ-03 / REQ-04; expectation basis: **observation**.
- Request: `GET /booking/-1`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `null`.
- Actual: Main response HTTP 404. Personal execution status: **Pass**.
- Recorded checks: Response received without server error; Unknown ID is not a successful booking read.
- Failed assertions: None recorded. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-019`.

## API-020 — Read nonexistent or malformed ID 999999999999
- Suite: Read and filters; requirement: REQ-03 / REQ-04; expectation basis: **observation**.
- Request: `GET /booking/999999999999`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `null`.
- Actual: Main response HTTP 404. Personal execution status: **Pass**.
- Recorded checks: Response received without server error; Unknown ID is not a successful booking read.
- Failed assertions: None recorded. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-020`.

## API-021 — Read response XML negotiation
- Suite: Read and filters; requirement: REQ-03 / REQ-04; expectation basis: **contract**.
- Request: `GET /booking/{{ownedId}}`.
- Setup: create a fresh owned synthetic booking and capture ID/token.
- Input: `null`.
- Actual: Main response HTTP 200. Personal execution status: **Fail**.
- Recorded checks: Setup: fresh owned booking created; Response received without server error; Documented status 200; XML representation returned; Cleanup: owned record removed or already absent.
- Failed assertions: Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-021`.

## API-022 — Read response JSON negotiation
- Suite: Read and filters; requirement: REQ-03 / REQ-04; expectation basis: **contract**.
- Request: `GET /booking/{{ownedId}}`.
- Setup: create a fresh owned synthetic booking and capture ID/token.
- Input: `null`.
- Actual: Main response HTTP 200. Personal execution status: **Fail**.
- Recorded checks: Setup: fresh owned booking created; Response received without server error; Documented status 200; Booking schema; Cleanup: owned record removed or already absent.
- Failed assertions: Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-022`.

## API-023 — Standard booking
- Suite: Create and persistence; requirement: REQ-05; expectation basis: **contract**.
- Request: `POST /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"firstname": "AkshayQA", "lastname": "Portfolio", "totalprice": 123, "depositpaid": true, "bookingdates": {"checkin": "2026-11-10", "checkout": "2026-11-12"}, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 200. Personal execution status: **Fail**.
- Recorded checks: Response received without server error; Documented status 200; Created response booking schema; Read-back: saved booking available; Saved firstname equals submitted value; Saved lastname equals submitted value; Saved totalprice equals submitted value; Saved depositpaid equals submitted value; Saved bookingdates equals submitted value; Saved additionalneeds equals submitted value; Cleanup: owned record removed or already absent.
- Failed assertions: Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-023`.

## API-024 — No optional additional needs
- Suite: Create and persistence; requirement: REQ-05; expectation basis: **contract**.
- Request: `POST /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"firstname": "AkshayQA", "lastname": "Portfolio", "totalprice": 123, "depositpaid": true, "bookingdates": {"checkin": "2026-11-10", "checkout": "2026-11-12"}}`.
- Actual: Main response HTTP 200. Personal execution status: **Fail**.
- Recorded checks: Response received without server error; Documented status 200; Created response booking schema; Read-back: saved booking available; Saved firstname equals submitted value; Saved lastname equals submitted value; Saved totalprice equals submitted value; Saved depositpaid equals submitted value; Saved bookingdates equals submitted value; Cleanup: owned record removed or already absent.
- Failed assertions: Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-024`.

## API-025 — Deposit false
- Suite: Create and persistence; requirement: REQ-05; expectation basis: **contract**.
- Request: `POST /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"firstname": "AkshayQA", "lastname": "Portfolio", "totalprice": 123, "depositpaid": false, "bookingdates": {"checkin": "2026-11-10", "checkout": "2026-11-12"}, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 200. Personal execution status: **Fail**.
- Recorded checks: Response received without server error; Documented status 200; Created response booking schema; Read-back: saved booking available; Saved firstname equals submitted value; Saved lastname equals submitted value; Saved totalprice equals submitted value; Saved depositpaid equals submitted value; Saved bookingdates equals submitted value; Saved additionalneeds equals submitted value; Cleanup: owned record removed or already absent.
- Failed assertions: Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-025`.

## API-026 — Integer price
- Suite: Create and persistence; requirement: REQ-05; expectation basis: **contract**.
- Request: `POST /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"firstname": "AkshayQA", "lastname": "Portfolio", "totalprice": 500, "depositpaid": true, "bookingdates": {"checkin": "2026-11-10", "checkout": "2026-11-12"}, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 200. Personal execution status: **Fail**.
- Recorded checks: Response received without server error; Documented status 200; Created response booking schema; Read-back: saved booking available; Saved firstname equals submitted value; Saved lastname equals submitted value; Saved totalprice equals submitted value; Saved depositpaid equals submitted value; Saved bookingdates equals submitted value; Saved additionalneeds equals submitted value; Cleanup: owned record removed or already absent.
- Failed assertions: Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-026`.

## API-027 — Decimal price
- Suite: Create and persistence; requirement: REQ-05; expectation basis: **contract**.
- Request: `POST /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"firstname": "AkshayQA", "lastname": "Portfolio", "totalprice": 123.5, "depositpaid": true, "bookingdates": {"checkin": "2026-11-10", "checkout": "2026-11-12"}, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 200. Personal execution status: **Fail**.
- Recorded checks: Response received without server error; Documented status 200; Created response booking schema; Read-back: saved booking available; Saved firstname equals submitted value; Saved lastname equals submitted value; Saved totalprice equals submitted value; Saved depositpaid equals submitted value; Saved bookingdates equals submitted value; Saved additionalneeds equals submitted value; Cleanup: owned record removed or already absent.
- Failed assertions: Saved totalprice equals submitted value; Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-027`.

## API-028 — Unicode name
- Suite: Create and persistence; requirement: REQ-05; expectation basis: **contract**.
- Request: `POST /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"firstname": "Akshay_日本", "lastname": "Portfolio", "totalprice": 123, "depositpaid": true, "bookingdates": {"checkin": "2026-11-10", "checkout": "2026-11-12"}, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 200. Personal execution status: **Fail**.
- Recorded checks: Response received without server error; Documented status 200; Created response booking schema; Read-back: saved booking available; Saved firstname equals submitted value; Saved lastname equals submitted value; Saved totalprice equals submitted value; Saved depositpaid equals submitted value; Saved bookingdates equals submitted value; Saved additionalneeds equals submitted value; Cleanup: owned record removed or already absent.
- Failed assertions: Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-028`.

## API-029 — Spaces in name
- Suite: Create and persistence; requirement: REQ-05; expectation basis: **contract**.
- Request: `POST /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"firstname": "Akshay QA", "lastname": "Portfolio", "totalprice": 123, "depositpaid": true, "bookingdates": {"checkin": "2026-11-10", "checkout": "2026-11-12"}, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 200. Personal execution status: **Fail**.
- Recorded checks: Response received without server error; Documented status 200; Created response booking schema; Read-back: saved booking available; Saved firstname equals submitted value; Saved lastname equals submitted value; Saved totalprice equals submitted value; Saved depositpaid equals submitted value; Saved bookingdates equals submitted value; Saved additionalneeds equals submitted value; Cleanup: owned record removed or already absent.
- Failed assertions: Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-029`.

## API-030 — Longer name
- Suite: Create and persistence; requirement: REQ-05; expectation basis: **contract**.
- Request: `POST /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"firstname": "QAQAQAQAQAQAQAQAQAQAQAQAQAQAQAQAQAQAQAQAQAQAQAQAQAQAQAQAQAQA", "lastname": "Portfolio", "totalprice": 123, "depositpaid": true, "bookingdates": {"checkin": "2026-11-10", "checkout": "2026-11-12"}, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 200. Personal execution status: **Fail**.
- Recorded checks: Response received without server error; Documented status 200; Created response booking schema; Read-back: saved booking available; Saved firstname equals submitted value; Saved lastname equals submitted value; Saved totalprice equals submitted value; Saved depositpaid equals submitted value; Saved bookingdates equals submitted value; Saved additionalneeds equals submitted value; Cleanup: owned record removed or already absent.
- Failed assertions: Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-030`.

## API-031 — Later dates
- Suite: Create and persistence; requirement: REQ-05; expectation basis: **contract**.
- Request: `POST /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"firstname": "AkshayQA", "lastname": "Portfolio", "totalprice": 123, "depositpaid": true, "bookingdates": {"checkin": "2027-01-01", "checkout": "2027-01-05"}, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 200. Personal execution status: **Fail**.
- Recorded checks: Response received without server error; Documented status 200; Created response booking schema; Read-back: saved booking available; Saved firstname equals submitted value; Saved lastname equals submitted value; Saved totalprice equals submitted value; Saved depositpaid equals submitted value; Saved bookingdates equals submitted value; Saved additionalneeds equals submitted value; Cleanup: owned record removed or already absent.
- Failed assertions: Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-031`.

## API-032 — Empty optional needs
- Suite: Create and persistence; requirement: REQ-05; expectation basis: **contract**.
- Request: `POST /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"firstname": "AkshayQA", "lastname": "Portfolio", "totalprice": 123, "depositpaid": true, "bookingdates": {"checkin": "2026-11-10", "checkout": "2026-11-12"}, "additionalneeds": ""}`.
- Actual: Main response HTTP 200. Personal execution status: **Fail**.
- Recorded checks: Response received without server error; Documented status 200; Created response booking schema; Read-back: saved booking available; Saved firstname equals submitted value; Saved lastname equals submitted value; Saved totalprice equals submitted value; Saved depositpaid equals submitted value; Saved bookingdates equals submitted value; Saved additionalneeds equals submitted value; Cleanup: owned record removed or already absent.
- Failed assertions: Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-032`.

## API-033 — firstname = omitted
- Suite: Exploratory validation; requirement: REQ-05; expectation basis: **proposed**.
- Request: `POST /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"lastname": "Portfolio", "totalprice": 123, "depositpaid": true, "bookingdates": {"checkin": "2026-11-10", "checkout": "2026-11-12"}, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 500. Personal execution status: **Fail**.
- Recorded checks: Response received without server error; Proposed expectation: invalid request rejected with 4xx.
- Failed assertions: Response received without server error; Proposed expectation: invalid request rejected with 4xx. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-033`.

## API-034 — lastname = omitted
- Suite: Exploratory validation; requirement: REQ-05; expectation basis: **proposed**.
- Request: `POST /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"firstname": "AkshayQA", "totalprice": 123, "depositpaid": true, "bookingdates": {"checkin": "2026-11-10", "checkout": "2026-11-12"}, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 500. Personal execution status: **Fail**.
- Recorded checks: Response received without server error; Proposed expectation: invalid request rejected with 4xx.
- Failed assertions: Response received without server error; Proposed expectation: invalid request rejected with 4xx. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-034`.

## API-035 — totalprice = omitted
- Suite: Exploratory validation; requirement: REQ-05; expectation basis: **proposed**.
- Request: `POST /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"firstname": "AkshayQA", "lastname": "Portfolio", "depositpaid": true, "bookingdates": {"checkin": "2026-11-10", "checkout": "2026-11-12"}, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 500. Personal execution status: **Fail**.
- Recorded checks: Response received without server error; Proposed expectation: invalid request rejected with 4xx.
- Failed assertions: Response received without server error; Proposed expectation: invalid request rejected with 4xx. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-035`.

## API-036 — depositpaid = omitted
- Suite: Exploratory validation; requirement: REQ-05; expectation basis: **proposed**.
- Request: `POST /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"firstname": "AkshayQA", "lastname": "Portfolio", "totalprice": 123, "bookingdates": {"checkin": "2026-11-10", "checkout": "2026-11-12"}, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 500. Personal execution status: **Fail**.
- Recorded checks: Response received without server error; Proposed expectation: invalid request rejected with 4xx.
- Failed assertions: Response received without server error; Proposed expectation: invalid request rejected with 4xx. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-036`.

## API-037 — bookingdates = omitted
- Suite: Exploratory validation; requirement: REQ-05; expectation basis: **proposed**.
- Request: `POST /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"firstname": "AkshayQA", "lastname": "Portfolio", "totalprice": 123, "depositpaid": true, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 500. Personal execution status: **Fail**.
- Recorded checks: Response received without server error; Proposed expectation: invalid request rejected with 4xx.
- Failed assertions: Response received without server error; Proposed expectation: invalid request rejected with 4xx. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-037`.

## API-038 — firstname = null
- Suite: Exploratory validation; requirement: REQ-05; expectation basis: **proposed**.
- Request: `POST /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"firstname": null, "lastname": "Portfolio", "totalprice": 123, "depositpaid": true, "bookingdates": {"checkin": "2026-11-10", "checkout": "2026-11-12"}, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 500. Personal execution status: **Fail**.
- Recorded checks: Response received without server error; Proposed expectation: invalid request rejected with 4xx.
- Failed assertions: Response received without server error; Proposed expectation: invalid request rejected with 4xx. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-038`.

## API-039 — lastname = null
- Suite: Exploratory validation; requirement: REQ-05; expectation basis: **proposed**.
- Request: `POST /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"firstname": "AkshayQA", "lastname": null, "totalprice": 123, "depositpaid": true, "bookingdates": {"checkin": "2026-11-10", "checkout": "2026-11-12"}, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 500. Personal execution status: **Fail**.
- Recorded checks: Response received without server error; Proposed expectation: invalid request rejected with 4xx.
- Failed assertions: Response received without server error; Proposed expectation: invalid request rejected with 4xx. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-039`.

## API-040 — totalprice = null
- Suite: Exploratory validation; requirement: REQ-05; expectation basis: **proposed**.
- Request: `POST /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"firstname": "AkshayQA", "lastname": "Portfolio", "totalprice": null, "depositpaid": true, "bookingdates": {"checkin": "2026-11-10", "checkout": "2026-11-12"}, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 500. Personal execution status: **Fail**.
- Recorded checks: Response received without server error; Proposed expectation: invalid request rejected with 4xx.
- Failed assertions: Response received without server error; Proposed expectation: invalid request rejected with 4xx. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-040`.

## API-041 — depositpaid = null
- Suite: Exploratory validation; requirement: REQ-05; expectation basis: **proposed**.
- Request: `POST /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"firstname": "AkshayQA", "lastname": "Portfolio", "totalprice": 123, "depositpaid": null, "bookingdates": {"checkin": "2026-11-10", "checkout": "2026-11-12"}, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 500. Personal execution status: **Fail**.
- Recorded checks: Response received without server error; Proposed expectation: invalid request rejected with 4xx.
- Failed assertions: Response received without server error; Proposed expectation: invalid request rejected with 4xx. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-041`.

## API-042 — bookingdates = null
- Suite: Exploratory validation; requirement: REQ-05; expectation basis: **proposed**.
- Request: `POST /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"firstname": "AkshayQA", "lastname": "Portfolio", "totalprice": 123, "depositpaid": true, "bookingdates": null, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 500. Personal execution status: **Fail**.
- Recorded checks: Response received without server error; Proposed expectation: invalid request rejected with 4xx.
- Failed assertions: Response received without server error; Proposed expectation: invalid request rejected with 4xx. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-042`.

## API-043 — firstname = 123
- Suite: Exploratory validation; requirement: REQ-05; expectation basis: **proposed**.
- Request: `POST /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"firstname": 123, "lastname": "Portfolio", "totalprice": 123, "depositpaid": true, "bookingdates": {"checkin": "2026-11-10", "checkout": "2026-11-12"}, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 500. Personal execution status: **Fail**.
- Recorded checks: Response received without server error; Proposed expectation: invalid request rejected with 4xx.
- Failed assertions: Response received without server error; Proposed expectation: invalid request rejected with 4xx. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-043`.

## API-044 — lastname = false
- Suite: Exploratory validation; requirement: REQ-05; expectation basis: **proposed**.
- Request: `POST /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"firstname": "AkshayQA", "lastname": false, "totalprice": 123, "depositpaid": true, "bookingdates": {"checkin": "2026-11-10", "checkout": "2026-11-12"}, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 200. Personal execution status: **Fail**.
- Recorded checks: Response received without server error; Proposed expectation: invalid request rejected with 4xx; Created response booking schema; Cleanup: owned record removed or already absent.
- Failed assertions: Proposed expectation: invalid request rejected with 4xx; Created response booking schema; Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-044`.

## API-045 — totalprice = "abc"
- Suite: Exploratory validation; requirement: REQ-05; expectation basis: **proposed**.
- Request: `POST /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"firstname": "AkshayQA", "lastname": "Portfolio", "totalprice": "abc", "depositpaid": true, "bookingdates": {"checkin": "2026-11-10", "checkout": "2026-11-12"}, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 200. Personal execution status: **Fail**.
- Recorded checks: Response received without server error; Proposed expectation: invalid request rejected with 4xx; Created response booking schema; Cleanup: owned record removed or already absent.
- Failed assertions: Proposed expectation: invalid request rejected with 4xx; Created response booking schema; Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-045`.

## API-046 — depositpaid = "yes"
- Suite: Exploratory validation; requirement: REQ-05; expectation basis: **proposed**.
- Request: `POST /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"firstname": "AkshayQA", "lastname": "Portfolio", "totalprice": 123, "depositpaid": "yes", "bookingdates": {"checkin": "2026-11-10", "checkout": "2026-11-12"}, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 200. Personal execution status: **Fail**.
- Recorded checks: Response received without server error; Proposed expectation: invalid request rejected with 4xx; Created response booking schema; Cleanup: owned record removed or already absent.
- Failed assertions: Proposed expectation: invalid request rejected with 4xx; Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-046`.

## API-047 — bookingdates = "tomorrow"
- Suite: Exploratory validation; requirement: REQ-05; expectation basis: **proposed**.
- Request: `POST /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"firstname": "AkshayQA", "lastname": "Portfolio", "totalprice": 123, "depositpaid": true, "bookingdates": "tomorrow", "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 500. Personal execution status: **Fail**.
- Recorded checks: Response received without server error; Proposed expectation: invalid request rejected with 4xx.
- Failed assertions: Response received without server error; Proposed expectation: invalid request rejected with 4xx. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-047`.

## API-048 — firstname = ""
- Suite: Exploratory validation; requirement: REQ-05; expectation basis: **proposed**.
- Request: `POST /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"firstname": "", "lastname": "Portfolio", "totalprice": 123, "depositpaid": true, "bookingdates": {"checkin": "2026-11-10", "checkout": "2026-11-12"}, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 200. Personal execution status: **Fail**.
- Recorded checks: Response received without server error; Proposed expectation: invalid request rejected with 4xx; Created response booking schema; Cleanup: owned record removed or already absent.
- Failed assertions: Proposed expectation: invalid request rejected with 4xx; Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-048`.

## API-049 — lastname = ""
- Suite: Exploratory validation; requirement: REQ-05; expectation basis: **proposed**.
- Request: `POST /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"firstname": "AkshayQA", "lastname": "", "totalprice": 123, "depositpaid": true, "bookingdates": {"checkin": "2026-11-10", "checkout": "2026-11-12"}, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 200. Personal execution status: **Fail**.
- Recorded checks: Response received without server error; Proposed expectation: invalid request rejected with 4xx; Created response booking schema; Cleanup: owned record removed or already absent.
- Failed assertions: Proposed expectation: invalid request rejected with 4xx; Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-049`.

## API-050 — totalprice = -1
- Suite: Exploratory validation; requirement: REQ-05; expectation basis: **proposed**.
- Request: `POST /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"firstname": "AkshayQA", "lastname": "Portfolio", "totalprice": -1, "depositpaid": true, "bookingdates": {"checkin": "2026-11-10", "checkout": "2026-11-12"}, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 200. Personal execution status: **Fail**.
- Recorded checks: Response received without server error; Proposed expectation: invalid request rejected with 4xx; Created response booking schema; Cleanup: owned record removed or already absent.
- Failed assertions: Proposed expectation: invalid request rejected with 4xx; Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-050`.

## API-051 — totalprice = 0
- Suite: Exploratory validation; requirement: REQ-05; expectation basis: **proposed**.
- Request: `POST /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"firstname": "AkshayQA", "lastname": "Portfolio", "totalprice": 0, "depositpaid": true, "bookingdates": {"checkin": "2026-11-10", "checkout": "2026-11-12"}, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 200. Personal execution status: **Fail**.
- Recorded checks: Response received without server error; Proposed expectation: invalid request rejected with 4xx; Created response booking schema; Cleanup: owned record removed or already absent.
- Failed assertions: Proposed expectation: invalid request rejected with 4xx; Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-051`.

## API-052 — totalprice = 1000000000000
- Suite: Exploratory validation; requirement: REQ-05; expectation basis: **proposed**.
- Request: `POST /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"firstname": "AkshayQA", "lastname": "Portfolio", "totalprice": 1000000000000, "depositpaid": true, "bookingdates": {"checkin": "2026-11-10", "checkout": "2026-11-12"}, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 200. Personal execution status: **Fail**.
- Recorded checks: Response received without server error; Proposed expectation: invalid request rejected with 4xx; Created response booking schema; Cleanup: owned record removed or already absent.
- Failed assertions: Proposed expectation: invalid request rejected with 4xx; Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-052`.

## API-053 — Check-in omitted
- Suite: Exploratory validation; requirement: REQ-05; expectation basis: **proposed**.
- Request: `POST /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"firstname": "AkshayQA", "lastname": "Portfolio", "totalprice": 123, "depositpaid": true, "bookingdates": {"checkout": "2026-11-12"}, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 500. Personal execution status: **Fail**.
- Recorded checks: Response received without server error; Proposed expectation: invalid request rejected with 4xx.
- Failed assertions: Response received without server error; Proposed expectation: invalid request rejected with 4xx. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-053`.

## API-054 — Checkout omitted
- Suite: Exploratory validation; requirement: REQ-05; expectation basis: **proposed**.
- Request: `POST /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"firstname": "AkshayQA", "lastname": "Portfolio", "totalprice": 123, "depositpaid": true, "bookingdates": {"checkin": "2026-11-10"}, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 500. Personal execution status: **Fail**.
- Recorded checks: Response received without server error; Proposed expectation: invalid request rejected with 4xx.
- Failed assertions: Response received without server error; Proposed expectation: invalid request rejected with 4xx. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-054`.

## API-055 — Invalid check-in
- Suite: Exploratory validation; requirement: REQ-05; expectation basis: **proposed**.
- Request: `POST /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"firstname": "AkshayQA", "lastname": "Portfolio", "totalprice": 123, "depositpaid": true, "bookingdates": {"checkin": "not-a-date", "checkout": "2026-11-12"}, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 200. Personal execution status: **Fail**.
- Recorded checks: Response received without server error; Proposed expectation: invalid request rejected with 4xx; Created response booking schema; Cleanup: owned record removed or already absent.
- Failed assertions: Proposed expectation: invalid request rejected with 4xx; Created response booking schema; Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-055`.

## API-056 — Invalid calendar date
- Suite: Exploratory validation; requirement: REQ-05; expectation basis: **proposed**.
- Request: `POST /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"firstname": "AkshayQA", "lastname": "Portfolio", "totalprice": 123, "depositpaid": true, "bookingdates": {"checkin": "2026-02-30", "checkout": "2026-03-03"}, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 200. Personal execution status: **Fail**.
- Recorded checks: Response received without server error; Proposed expectation: invalid request rejected with 4xx; Created response booking schema; Cleanup: owned record removed or already absent.
- Failed assertions: Proposed expectation: invalid request rejected with 4xx; Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-056`.

## API-057 — Reversed dates
- Suite: Exploratory validation; requirement: REQ-05; expectation basis: **proposed**.
- Request: `POST /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"firstname": "AkshayQA", "lastname": "Portfolio", "totalprice": 123, "depositpaid": true, "bookingdates": {"checkin": "2026-11-12", "checkout": "2026-11-10"}, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 200. Personal execution status: **Fail**.
- Recorded checks: Response received without server error; Proposed expectation: invalid request rejected with 4xx; Created response booking schema; Cleanup: owned record removed or already absent.
- Failed assertions: Proposed expectation: invalid request rejected with 4xx; Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-057`.

## API-058 — Same-day stay
- Suite: Exploratory validation; requirement: REQ-05; expectation basis: **proposed**.
- Request: `POST /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"firstname": "AkshayQA", "lastname": "Portfolio", "totalprice": 123, "depositpaid": true, "bookingdates": {"checkin": "2026-11-10", "checkout": "2026-11-10"}, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 200. Personal execution status: **Fail**.
- Recorded checks: Response received without server error; Proposed expectation: invalid request rejected with 4xx; Created response booking schema; Cleanup: owned record removed or already absent.
- Failed assertions: Proposed expectation: invalid request rejected with 4xx; Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-058`.

## API-059 — Numeric date
- Suite: Exploratory validation; requirement: REQ-05; expectation basis: **proposed**.
- Request: `POST /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"firstname": "AkshayQA", "lastname": "Portfolio", "totalprice": 123, "depositpaid": true, "bookingdates": {"checkin": 123, "checkout": "2026-11-12"}, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 200. Personal execution status: **Fail**.
- Recorded checks: Response received without server error; Proposed expectation: invalid request rejected with 4xx; Created response booking schema; Cleanup: owned record removed or already absent.
- Failed assertions: Proposed expectation: invalid request rejected with 4xx; Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-059`.

## API-060 — Malformed JSON body
- Suite: Exploratory validation; requirement: REQ-05; expectation basis: **proposed**.
- Request: `POST /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `"{\"firstname\":"`.
- Actual: Main response HTTP 400. Personal execution status: **Pass**.
- Recorded checks: Response received without server error; Proposed expectation: invalid request rejected with 4xx.
- Failed assertions: None recorded. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-060`.

## API-061 — Replace every field
- Suite: Update and workflow; requirement: REQ-06 / REQ-07; expectation basis: **contract**.
- Request: `PUT /booking/{{ownedId}}`.
- Setup: create a fresh owned synthetic booking and capture ID/token.
- Input: `{"firstname": "UpdatedQA", "lastname": "UpdatedPortfolio", "totalprice": 999, "depositpaid": false, "bookingdates": {"checkin": "2026-11-10", "checkout": "2026-11-12"}, "additionalneeds": "Dinner"}`.
- Actual: Main response HTTP 403. Personal execution status: **Fail**.
- Recorded checks: Setup: fresh owned booking created; Response received without server error; Documented status 200; Booking schema; Read-back: saved booking available; Saved firstname equals submitted value; Saved lastname equals submitted value; Saved totalprice equals submitted value; Saved depositpaid equals submitted value; Saved bookingdates equals submitted value; Saved additionalneeds equals submitted value; Cleanup: owned record removed or already absent.
- Failed assertions: Documented status 200; Booking schema; Saved firstname equals submitted value; Saved lastname equals submitted value; Saved totalprice equals submitted value; Saved depositpaid equals submitted value; Saved additionalneeds equals submitted value; Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-061`.

## API-062 — Replace price
- Suite: Update and workflow; requirement: REQ-06 / REQ-07; expectation basis: **contract**.
- Request: `PUT /booking/{{ownedId}}`.
- Setup: create a fresh owned synthetic booking and capture ID/token.
- Input: `{"firstname": "AkshayQA", "lastname": "Portfolio", "totalprice": 456, "depositpaid": true, "bookingdates": {"checkin": "2026-11-10", "checkout": "2026-11-12"}, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 403. Personal execution status: **Fail**.
- Recorded checks: Setup: fresh owned booking created; Response received without server error; Documented status 200; Booking schema; Read-back: saved booking available; Saved firstname equals submitted value; Saved lastname equals submitted value; Saved totalprice equals submitted value; Saved depositpaid equals submitted value; Saved bookingdates equals submitted value; Saved additionalneeds equals submitted value; Cleanup: owned record removed or already absent.
- Failed assertions: Documented status 200; Booking schema; Saved firstname equals submitted value; Saved lastname equals submitted value; Saved totalprice equals submitted value; Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-062`.

## API-063 — Replace dates
- Suite: Update and workflow; requirement: REQ-06 / REQ-07; expectation basis: **contract**.
- Request: `PUT /booking/{{ownedId}}`.
- Setup: create a fresh owned synthetic booking and capture ID/token.
- Input: `{"firstname": "AkshayQA", "lastname": "Portfolio", "totalprice": 123, "depositpaid": true, "bookingdates": {"checkin": "2027-02-01", "checkout": "2027-02-03"}, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 403. Personal execution status: **Fail**.
- Recorded checks: Setup: fresh owned booking created; Response received without server error; Documented status 200; Booking schema; Read-back: saved booking available; Saved firstname equals submitted value; Saved lastname equals submitted value; Saved totalprice equals submitted value; Saved depositpaid equals submitted value; Saved bookingdates equals submitted value; Saved additionalneeds equals submitted value; Cleanup: owned record removed or already absent.
- Failed assertions: Documented status 200; Booking schema; Saved firstname equals submitted value; Saved lastname equals submitted value; Saved bookingdates equals submitted value; Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-063`.

## API-064 — Basic auth replacement
- Suite: Update and workflow; requirement: REQ-06 / REQ-07; expectation basis: **contract**.
- Request: `PUT /booking/{{ownedId}}`.
- Setup: create a fresh owned synthetic booking and capture ID/token.
- Input: `{"firstname": "BasicQA", "lastname": "Portfolio", "totalprice": 123, "depositpaid": true, "bookingdates": {"checkin": "2026-11-10", "checkout": "2026-11-12"}, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 200. Personal execution status: **Fail**.
- Recorded checks: Setup: fresh owned booking created; Response received without server error; Documented status 200; Booking schema; Read-back: saved booking available; Saved firstname equals submitted value; Saved lastname equals submitted value; Saved totalprice equals submitted value; Saved depositpaid equals submitted value; Saved bookingdates equals submitted value; Saved additionalneeds equals submitted value; Cleanup: owned record removed or already absent.
- Failed assertions: Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-064`.

## API-065 — Patch First name
- Suite: Update and workflow; requirement: REQ-06 / REQ-07; expectation basis: **contract**.
- Request: `PATCH /booking/{{ownedId}}`.
- Setup: create a fresh owned synthetic booking and capture ID/token.
- Input: `{"firstname": "PatchQA"}`.
- Actual: Main response HTTP 403. Personal execution status: **Fail**.
- Recorded checks: Setup: fresh owned booking created; Response received without server error; Documented status 200; Booking schema; Read-back: saved booking available; Saved firstname equals submitted value; Untouched lastname preserved; Untouched totalprice preserved; Untouched depositpaid preserved; Untouched bookingdates preserved; Untouched additionalneeds preserved; Cleanup: owned record removed or already absent.
- Failed assertions: Documented status 200; Booking schema; Saved firstname equals submitted value; Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-065`.

## API-066 — Patch Last name
- Suite: Update and workflow; requirement: REQ-06 / REQ-07; expectation basis: **contract**.
- Request: `PATCH /booking/{{ownedId}}`.
- Setup: create a fresh owned synthetic booking and capture ID/token.
- Input: `{"lastname": "PatchPortfolio"}`.
- Actual: Main response HTTP 403. Personal execution status: **Fail**.
- Recorded checks: Setup: fresh owned booking created; Response received without server error; Documented status 200; Booking schema; Read-back: saved booking available; Saved lastname equals submitted value; Untouched firstname preserved; Untouched totalprice preserved; Untouched depositpaid preserved; Untouched bookingdates preserved; Untouched additionalneeds preserved; Cleanup: owned record removed or already absent.
- Failed assertions: Documented status 200; Booking schema; Saved lastname equals submitted value; Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-066`.

## API-067 — Patch Price
- Suite: Update and workflow; requirement: REQ-06 / REQ-07; expectation basis: **contract**.
- Request: `PATCH /booking/{{ownedId}}`.
- Setup: create a fresh owned synthetic booking and capture ID/token.
- Input: `{"totalprice": 321}`.
- Actual: Main response HTTP 403. Personal execution status: **Fail**.
- Recorded checks: Setup: fresh owned booking created; Response received without server error; Documented status 200; Booking schema; Read-back: saved booking available; Saved totalprice equals submitted value; Untouched firstname preserved; Untouched lastname preserved; Untouched depositpaid preserved; Untouched bookingdates preserved; Untouched additionalneeds preserved; Cleanup: owned record removed or already absent.
- Failed assertions: Documented status 200; Booking schema; Saved totalprice equals submitted value; Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-067`.

## API-068 — Patch Deposit
- Suite: Update and workflow; requirement: REQ-06 / REQ-07; expectation basis: **contract**.
- Request: `PATCH /booking/{{ownedId}}`.
- Setup: create a fresh owned synthetic booking and capture ID/token.
- Input: `{"depositpaid": false}`.
- Actual: Main response HTTP 403. Personal execution status: **Fail**.
- Recorded checks: Setup: fresh owned booking created; Response received without server error; Documented status 200; Booking schema; Read-back: saved booking available; Saved depositpaid equals submitted value; Untouched firstname preserved; Untouched lastname preserved; Untouched totalprice preserved; Untouched bookingdates preserved; Untouched additionalneeds preserved; Cleanup: owned record removed or already absent.
- Failed assertions: Documented status 200; Booking schema; Saved depositpaid equals submitted value; Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-068`.

## API-069 — Patch Additional needs
- Suite: Update and workflow; requirement: REQ-06 / REQ-07; expectation basis: **contract**.
- Request: `PATCH /booking/{{ownedId}}`.
- Setup: create a fresh owned synthetic booking and capture ID/token.
- Input: `{"additionalneeds": "Lunch"}`.
- Actual: Main response HTTP 403. Personal execution status: **Fail**.
- Recorded checks: Setup: fresh owned booking created; Response received without server error; Documented status 200; Booking schema; Read-back: saved booking available; Saved additionalneeds equals submitted value; Untouched firstname preserved; Untouched lastname preserved; Untouched totalprice preserved; Untouched depositpaid preserved; Untouched bookingdates preserved; Cleanup: owned record removed or already absent.
- Failed assertions: Documented status 200; Booking schema; Saved additionalneeds equals submitted value; Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-069`.

## API-070 — Patch Dates
- Suite: Update and workflow; requirement: REQ-06 / REQ-07; expectation basis: **contract**.
- Request: `PATCH /booking/{{ownedId}}`.
- Setup: create a fresh owned synthetic booking and capture ID/token.
- Input: `{"bookingdates": {"checkin": "2027-03-01", "checkout": "2027-03-04"}}`.
- Actual: Main response HTTP 403. Personal execution status: **Fail**.
- Recorded checks: Setup: fresh owned booking created; Response received without server error; Documented status 200; Booking schema; Read-back: saved booking available; Saved bookingdates equals submitted value; Untouched firstname preserved; Untouched lastname preserved; Untouched totalprice preserved; Untouched depositpaid preserved; Untouched additionalneeds preserved; Cleanup: owned record removed or already absent.
- Failed assertions: Documented status 200; Booking schema; Saved bookingdates equals submitted value; Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-070`.

## API-071 — Patch Two fields
- Suite: Update and workflow; requirement: REQ-06 / REQ-07; expectation basis: **contract**.
- Request: `PATCH /booking/{{ownedId}}`.
- Setup: create a fresh owned synthetic booking and capture ID/token.
- Input: `{"firstname": "TwoQA", "totalprice": 777}`.
- Actual: Main response HTTP 403. Personal execution status: **Fail**.
- Recorded checks: Setup: fresh owned booking created; Response received without server error; Documented status 200; Booking schema; Read-back: saved booking available; Saved firstname equals submitted value; Saved totalprice equals submitted value; Untouched lastname preserved; Untouched depositpaid preserved; Untouched bookingdates preserved; Untouched additionalneeds preserved; Cleanup: owned record removed or already absent.
- Failed assertions: Documented status 200; Booking schema; Saved firstname equals submitted value; Saved totalprice equals submitted value; Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-071`.

## API-072 — Patch Basic auth patch
- Suite: Update and workflow; requirement: REQ-06 / REQ-07; expectation basis: **contract**.
- Request: `PATCH /booking/{{ownedId}}`.
- Setup: create a fresh owned synthetic booking and capture ID/token.
- Input: `{"additionalneeds": "Basic lunch"}`.
- Actual: Main response HTTP 200. Personal execution status: **Fail**.
- Recorded checks: Setup: fresh owned booking created; Response received without server error; Documented status 200; Booking schema; Read-back: saved booking available; Saved additionalneeds equals submitted value; Untouched firstname preserved; Untouched lastname preserved; Untouched totalprice preserved; Untouched depositpaid preserved; Untouched bookingdates preserved; Cleanup: owned record removed or already absent.
- Failed assertions: Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-072`.

## API-073 — PUT with missing token is denied
- Suite: Authorization; requirement: REQ-06 / REQ-07 / REQ-08; expectation basis: **proposed**.
- Request: `PUT /booking/{{ownedId}}`.
- Setup: create a fresh owned synthetic booking and capture ID/token.
- Input: `{"firstname": "AkshayQA", "lastname": "Portfolio", "totalprice": 123, "depositpaid": true, "bookingdates": {"checkin": "2026-11-10", "checkout": "2026-11-12"}, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 403. Personal execution status: **Fail**.
- Recorded checks: Setup: fresh owned booking created; Response received without server error; Proposed expectation: invalid request rejected with 4xx; Read-back: saved booking available; Denied operation left record unchanged; Cleanup: owned record removed or already absent.
- Failed assertions: Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-073`.

## API-074 — PUT with invalid token is denied
- Suite: Authorization; requirement: REQ-06 / REQ-07 / REQ-08; expectation basis: **proposed**.
- Request: `PUT /booking/{{ownedId}}`.
- Setup: create a fresh owned synthetic booking and capture ID/token.
- Input: `{"firstname": "AkshayQA", "lastname": "Portfolio", "totalprice": 123, "depositpaid": true, "bookingdates": {"checkin": "2026-11-10", "checkout": "2026-11-12"}, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 403. Personal execution status: **Fail**.
- Recorded checks: Setup: fresh owned booking created; Response received without server error; Proposed expectation: invalid request rejected with 4xx; Read-back: saved booking available; Denied operation left record unchanged; Cleanup: owned record removed or already absent.
- Failed assertions: Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-074`.

## API-075 — PATCH with missing token is denied
- Suite: Authorization; requirement: REQ-06 / REQ-07 / REQ-08; expectation basis: **proposed**.
- Request: `PATCH /booking/{{ownedId}}`.
- Setup: create a fresh owned synthetic booking and capture ID/token.
- Input: `{"firstname": "UnauthorizedQA"}`.
- Actual: Main response HTTP 403. Personal execution status: **Fail**.
- Recorded checks: Setup: fresh owned booking created; Response received without server error; Proposed expectation: invalid request rejected with 4xx; Read-back: saved booking available; Denied operation left record unchanged; Cleanup: owned record removed or already absent.
- Failed assertions: Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-075`.

## API-076 — PATCH with invalid token is denied
- Suite: Authorization; requirement: REQ-06 / REQ-07 / REQ-08; expectation basis: **proposed**.
- Request: `PATCH /booking/{{ownedId}}`.
- Setup: create a fresh owned synthetic booking and capture ID/token.
- Input: `{"firstname": "UnauthorizedQA"}`.
- Actual: Main response HTTP 403. Personal execution status: **Fail**.
- Recorded checks: Setup: fresh owned booking created; Response received without server error; Proposed expectation: invalid request rejected with 4xx; Read-back: saved booking available; Denied operation left record unchanged; Cleanup: owned record removed or already absent.
- Failed assertions: Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-076`.

## API-077 — DELETE with missing token is denied
- Suite: Authorization; requirement: REQ-06 / REQ-07 / REQ-08; expectation basis: **proposed**.
- Request: `DELETE /booking/{{ownedId}}`.
- Setup: create a fresh owned synthetic booking and capture ID/token.
- Input: `null`.
- Actual: Main response HTTP 403. Personal execution status: **Fail**.
- Recorded checks: Setup: fresh owned booking created; Response received without server error; Proposed expectation: invalid request rejected with 4xx; Read-back: saved booking available; Denied operation left record unchanged; Cleanup: owned record removed or already absent.
- Failed assertions: Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-077`.

## API-078 — DELETE with invalid token is denied
- Suite: Authorization; requirement: REQ-06 / REQ-07 / REQ-08; expectation basis: **proposed**.
- Request: `DELETE /booking/{{ownedId}}`.
- Setup: create a fresh owned synthetic booking and capture ID/token.
- Input: `null`.
- Actual: Main response HTTP 403. Personal execution status: **Fail**.
- Recorded checks: Setup: fresh owned booking created; Response received without server error; Proposed expectation: invalid request rejected with 4xx; Read-back: saved booking available; Denied operation left record unchanged; Cleanup: owned record removed or already absent.
- Failed assertions: Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-078`.

## API-079 — Token-auth deletion removes owned booking
- Suite: Delete and repeatability; requirement: REQ-06 / REQ-08; expectation basis: **contract**.
- Request: `DELETE /booking/{{ownedId}}`.
- Setup: create a fresh owned synthetic booking and capture ID/token.
- Input: `null`.
- Actual: Main response HTTP 403. Personal execution status: **Fail**.
- Recorded checks: Setup: fresh owned booking created; Response received without server error; Documented status 201; Deleted booking cannot be read.
- Failed assertions: Documented status 201; Deleted booking cannot be read. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-079`.

## API-080 — Basic-auth deletion removes owned booking
- Suite: Delete and repeatability; requirement: REQ-06 / REQ-08; expectation basis: **contract**.
- Request: `DELETE /booking/{{ownedId}}`.
- Setup: create a fresh owned synthetic booking and capture ID/token.
- Input: `null`.
- Actual: Main response HTTP 201. Personal execution status: **Pass**.
- Recorded checks: Setup: fresh owned booking created; Response received without server error; Documented status 201; Deleted booking cannot be read.
- Failed assertions: None recorded. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-080`.

## API-081 — Repeated PUT preserves final representation
- Suite: Delete and repeatability; requirement: REQ-06 / REQ-08; expectation basis: **contract**.
- Request: `PUT /booking/{{ownedId}}`.
- Setup: create a fresh owned synthetic booking and capture ID/token.
- Input: `{"firstname": "RepeatQA", "lastname": "Portfolio", "totalprice": 123, "depositpaid": true, "bookingdates": {"checkin": "2026-11-10", "checkout": "2026-11-12"}, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 403. Personal execution status: **Fail**.
- Recorded checks: Setup: fresh owned booking created; Response received without server error; Documented status 200; Read-back: saved booking available; Saved firstname equals submitted value; Saved lastname equals submitted value; Saved totalprice equals submitted value; Saved depositpaid equals submitted value; Saved bookingdates equals submitted value; Saved additionalneeds equals submitted value; Repeated PUT representation unchanged; Cleanup: owned record removed or already absent.
- Failed assertions: Documented status 200; Saved firstname equals submitted value; Saved lastname equals submitted value; Repeated PUT representation unchanged; Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-081`.

## API-082 — Repeated DELETE leaves owned booking absent
- Suite: Delete and repeatability; requirement: REQ-06 / REQ-08; expectation basis: **observation**.
- Request: `DELETE /booking/{{ownedId}}`.
- Setup: create a fresh owned synthetic booking and capture ID/token.
- Input: `null`.
- Actual: Main response HTTP 403. Personal execution status: **Fail**.
- Recorded checks: Setup: fresh owned booking created; Response received without server error; Documented status 201; Deleted booking cannot be read; Repeat DELETE does not resurrect data; Still absent after repeat DELETE.
- Failed assertions: Documented status 201; Deleted booking cannot be read; Still absent after repeat DELETE. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-082`.

## API-083 — XML create and JSON read back
- Suite: Headers; requirement: REQ-04 / REQ-05; expectation basis: **contract**.
- Request: `POST /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `"<booking><firstname>XMLQA</firstname><lastname>Portfolio</lastname><totalprice>123</totalprice><depositpaid>true</depositpaid><bookingdates><checkin>2026-11-10</checkin><checkout>2026-11-12</checkout></bookingdates><additionalneeds>Breakfast</additionalneeds></booking>"`.
- Actual: Main response HTTP 200. Personal execution status: **Fail**.
- Recorded checks: Response received without server error; Documented status 200; Created response booking schema; Read-back: saved booking available; XML creation persisted its data; Cleanup: owned record removed or already absent.
- Failed assertions: Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-083`.

## API-084 — Unsupported Accept is rejected
- Suite: Headers; requirement: REQ-04 / REQ-05; expectation basis: **proposed**.
- Request: `GET /booking/{{ownedId}}`.
- Setup: create a fresh owned synthetic booking and capture ID/token.
- Input: `null`.
- Actual: Main response HTTP 418. Personal execution status: **Fail**.
- Recorded checks: Setup: fresh owned booking created; Response received without server error; Proposed expectation: invalid request rejected with 4xx; Cleanup: owned record removed or already absent.
- Failed assertions: Cleanup: owned record removed or already absent. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-084`.

## API-085 — Unsupported body media type is rejected
- Suite: Headers; requirement: REQ-04 / REQ-05; expectation basis: **proposed**.
- Request: `POST /booking`.
- Setup: acquire a runtime practice token if needed; creation returns its own ID.
- Input: `{"firstname": "AkshayQA", "lastname": "Portfolio", "totalprice": 123, "depositpaid": true, "bookingdates": {"checkin": "2026-11-10", "checkout": "2026-11-12"}, "additionalneeds": "Breakfast"}`.
- Actual: Main response HTTP 500. Personal execution status: **Fail**.
- Recorded checks: Response received without server error; Proposed expectation: invalid request rejected with 4xx.
- Failed assertions: Response received without server error; Proposed expectation: invalid request rejected with 4xx. Detailed error messages and response bodies were not exported.
- Evidence: [main run](../evidence/requests-responses/2026-10-28-main-reviewed.json), case `API-085`.
