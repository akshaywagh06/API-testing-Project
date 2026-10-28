# Test plan

## Objective
Check the documented booking operations and investigate differences between expected and actual behavior.

## Environment
Public Restful Booker HTTPS playground. Use Postman or Newman with Node.js 22 LTS. Record actual tool versions and UTC start/end times when executing. Personal execution was completed in Postman for Windows 11.110.0 on 28 October 2026. See the execution summary for actual times and settings.

## Data and setup
Use synthetic names and dates. Each mutation captures an ID from a booking created by that test. Authentication uses the provider's public practice credentials. Never put private credentials or captured tokens in the repository.

## Order of execution
Run smoke, then auth/list/read, create and persistence, full/partial updates, authorization, deletion and headers. Run the 10-row collection separately. In Newman, regression and exploratory folder selections together cover the main collection.

## Priorities
High: saved values, update correctness, denied mutations and deletion. Medium: schema, filters and content negotiation. Exploratory: undocumented input boundaries.

## Entry and completion criteria
Before testing, check availability and confirm a fresh booking can be created and cleaned up. Execution reporting requires actual results for the planned cases and sanitized evidence. Investigation completion additionally requires response captures, reviewed assertion errors and fresh-data reproduction of suspected findings; those gates remain pending. Passing every assertion is not a completion requirement on this practice service.

## Cleanup and shared data
Only delete IDs captured during setup or creation. Cleanup accepts an already absent ID, which can also indicate a reset. Do not silently retry failing checks. Use serial runs with 750 ms between main requests; callbacks add setup and verification traffic.

## Evidence and reporting
Record who ran the tests, tools, dates, case totals, assertion totals and request totals separately. Update the workbook, CSV, Markdown cases and traceability consistently. Redact tokens, Cookie, Authorization and Set-Cookie values before publishing. Findings need a requirement basis and a second run on fresh data.
