1. Already made a Carbon project that uses RPC polling


- crawler fetches sigs newest-to-oldest (the way rpc works)

 - Event log only (store decoded instructions as flat rows) → order doesn't matter, query however you want
  - Computed state (maintain running balances, pool totals, reward accumulators) → order matters, need the two-phase approach.


for my frontend i don't need raw data, i need computed state
- state is computed during ingestion
- so next line depends on previous line

 so if we write the data into the database as soon as it arrives from RPC, that means that we will first log and insert a claim reward but to decode the data we will not have previous data to be decoded in a correct way. That's why to properly decode data we need to first store it and then process it 