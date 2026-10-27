 - website can be built and stored in IPFS, so hosting is decentralized
	it works because website is the same for everyone
 - same could be done to indexing (The Graph)
	 but it works, because data is already public

> you can't decentralize the access layer of an app whose _data layer_ isn't already decentralized


i need to pay for:
1. Frontend (Vercel)
2. Indexer + postgres ([[railway]])
3. RPC

IaaS (Raw machine) - AWS, bare linux box, system that i must configure
PaaS (Managed platfrom) - Railway, Vercel -> i give code, they handle OS -> i manage my code, but not the machine
SaaS (Fully managed service) - Gmail, Notion


Vercel - stateless static sites
Railway - stateful (indexer, database)
