
 -> connects apps together

*UI* - user interface
- works for user
*API* - application programming interface
- works for code

![[Pasted image 20260408165250.png]]

#### How To Use It
- we use APIs (public/keys) to get data from app directly (like low-level calls)
	- make a request -> get a response
- we build APIs as a *door* to that data (from backend)

Frontend  →  API      →  Database (indexed chain data)
	            →  Solana RPC (faucet claims)
                →  anything else later


almost any data-related processes are done via API.
- Bolt - Google Maps
- Sign via Gmail - Google
- Apple Weather - some weather apps API
- Claude, GPT - we can build AIs on top of them
> logic: someone has data/service - they expose it through API. So you build on top, instead of building from scratch.

#### How To Build It
frontend -> API <-> database
- what data we can give
- what goes back
- filters
- auth
this all declared in API, so via API calls we will update database, for example.

```
db/              # database
    schema.ts
    index.ts
services/        # all logic (what to do)
    poolsService.ts
    positionsService.ts
routes/          # only HTTP, controller (how accept?)
    pools.ts
    positions.ts
```

Frontend
   ↓
Routes (HTTP layer)
   ↓
Services (business logic)
   ↓
DB (queries / schema)

##### Ideas:
- Web3 Job & Alpha Monitor

now i know, that if i need to get some data and analyze it, i can just take API and use it to build a full system.
