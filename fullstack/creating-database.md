
1. Postgres - databases.
2. Drizzle - to get data from Postgres with TS.

in repo:
```
backend/src/db/
			├── schema.ts
			├── index.ts
```

indexer and api are separate folder, but they share 1 database, so that is why we but it in /src, cause both import from it

1. schema.ts
2. index.ts (db client)
	1) Postgres connection
	2) Drizzle wrapper
3. docker compose (spin up Postgres)
4. run migration (create tables in db)