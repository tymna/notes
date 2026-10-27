1. Resources
	- Good: GET /positions/0xabc
    - Bad: GET /getPositionForAddress?addr=0xabc
 2. HTTP verbs mean something
    - GET — read, never modifies data
    - POST — create
    - PUT/PATCH — update
    - DELETE — delete
3. Stateless (serve does not hold the state between requests)
4. Consistent response shape — always return the same structure. Either
   { data: [...] } or an error { error: "message" }. Never mix.
5. Correct HTTP status codes
    - 200 — success
    - 400 — bad request (invalid address)
    - 404 — not found
    - 500 — server error