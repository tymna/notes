decentralized and local indexing

Indexing is always an off-chain thing that runs on a local server, but i can choose  "who runs the server and how i trust it".
- The Graph's network (GraphQL query language) is decentralized in a way as Chainlink - different operators (nodes) and comparing all that answers.
- Self-hosted: i am the only operator.

I don't need same approach as Uniswap has, because my infrastructure is private.
- public infrastructure (many independent parties
  depend on it's data)
- their system can survive even if something will die

So yes, in my system this indexer is more vulnerable in availability, but not itegrity-of-funds and mitigable with boring tools (DB backups, monitoring, re-index on suspicion):
- it is view-only
- i can recover the database
  
> Production method is to use some ready indexing solution.

1. Raw RPC
	- each time we ask the node (eth_getLogs)
2. DIY indexer
3. Subgraph (-> GraphQL database, decentralized The Graph network)
4. Stream (-> my DB)
