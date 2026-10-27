stripe subscriptions, but onchain
- blockchain = source truth and place where data will go to the dashboard
contracts (Foundry) ->
RPC ->
indexer (Goldsky) ->
database (Postgres (relational model + SQL underneath it) + Drizzle) ->
API (Hono + zod) ->
dashboard (Next.js, wagmi, viem) ->
[[deployment]] ->
monitoring (Tenderly)



**Database layer** = a database (Postgres) 
				+ a tool to talk to it from code
				  (Drizzle = query builder; ORMs hide SQL more).
**API layer** = a router (Hono = handles requests/routing)
			+ a validator (zod = checks input is safe)


in database i must put:
- who, which plan, how much, when (started/renewed/cancelled)
- so i ll calculate: MRR, Active count, Churn
- i ll have tables for history and for current state
	- subscribers (state) (append only)
	- payments (history)
	- plans (state) (append only)
	- subscriptions
	- metrics (history)
	- merchant
##### How to know, what tables to create?
- before writing smart contracts, i need general understanding of tables in database (not deep research)

events fill this tables (nouns = event params)



smart contract is gonna be just settlement layer which accepts payments in usdc.



1. create schemas in drizzle
2. run [[postgres setup]] in [[Docker]]
3. create drizzle config
4. run generate + migrate (drizzle-kit)