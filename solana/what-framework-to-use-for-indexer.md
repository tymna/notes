
1. Index data - get transactions from Solana into our system (indexer)
2. Store data - save it in a database (in database) (Postgres)
3. Query data — serve it to the frontend (via routes) (Fastify)

levels:
1. **Legacy JSON‑RPC + custom script**
2. **SQD (Subsquid) – TS, data lake, Orca templates**
3. **Carbon – Rust, validator‑level gRPC streaming**
4. **Substreams – Rust, massively parallel big‑history engine**

**WHAT IS THE BEST WAY TO INDEX DATA?**
##### Carbon:
- separate *rust* proj, that writes to Postgres
- has orca whirlpool decoder
- can be generated from idl
- need to manage restart recovery
- gRPC/can be used with regular RPC
	- if used with regular RPC = regular indexing, like our "onLogs" approach (but with ready pattern and later can be upgraded to gRPC)
- Gayser skips RPC layer
	- Carbon connects to Gayser (plugin inside Solana validator)
	- **gets data directly**

- before indexing, we need to get data (from LazerStream for example)
- but Carbon solves both of this problems
	$streaming + decoding = indexing$
> from "push" to "pull"
(we are not pulling the data, but use push validators, that give us this data)
- Datasources -> Pipes -> Decoders -> Processors
- `carbon-orca-whirlpool-decoder`

##### SQD (Subsquid):
- stores blockchain data in compressed binary format
- have template for orca
- fast for historical data, but "near real-time"
##### Substreams (parallel indexing):
- for "big data"