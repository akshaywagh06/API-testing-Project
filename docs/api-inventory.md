# API inventory

Base URL: https://restful-booker.herokuapp.com

| Requirement | Operation | Documented baseline |
|---|---|---|
| REQ-01 | GET /ping | 201 health response |
| REQ-02 | POST /auth | Valid credentials produce a token; success example 200 |
| REQ-03 | GET /booking | Array of numeric booking IDs; name/date filters |
| REQ-04 | GET /booking/{id} | Booking representation; JSON/XML negotiation; success 200 |
| REQ-05 | POST /booking | Numeric bookingid plus booking; success example 200 |
| REQ-06 | PUT /booking/{id} | Full update; Cookie token or Basic auth; success 200 |
| REQ-07 | PATCH /booking/{id} | Partial update; documented auth; success 200 |
| REQ-08 | DELETE /booking/{id} | Authenticated deletion; documented 201 |

Date filters are documented as greater-than-or-equal, including checkout. The docs do not provide a complete error-code contract. Negative-read and auth-denial assertions are therefore not proof of every documented response code. Create supports JSON, XML and form encoding in documentation; the collection includes JSON and one XML create, not form-encoded creation.

Source: https://restful-booker.herokuapp.com/apidoc/api_data.json
