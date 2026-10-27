
1. **Mirror** — Chain → your Postgres (EVM only) (it can take an existing subgraph's entities as a source)
2. **Turbo** — Same as Mirror, newer + non-EVM chains

3. **Subgraphs** — Chain → GraphQL API (Goldsky owns the DB) 
4. **Edge RPC** — Fast node access (read the chain directly)
5. **Compose** — Run TypeScript logic on a schedule/trigger

- we don't decentralize the cache, because it is no a *public good*. It is used only by my program, not like in Uniswap