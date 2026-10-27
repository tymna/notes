- it must read events from blockchain (via Viem, RPC calls) and write them to database
- also after indexing it must write last indexed block numberA

1) getLogs - for backfill
2) watchContractEvent - subscribes in real time
3) publicClient - RPC calls


backend/src/indexer/
  ├── client.ts    ← viem publicClient
  └── index.ts     ← backfill + watch logic

before we must have a publicClient
- start indexer -> read last_indexed_block
- getLogs from last_indexed_block -> write events
- update last_indexed_block
- watchContractEvent -> write each event+update last_indexed_block