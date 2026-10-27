current [[MEV]] mitigation:
PBS - Proposer-Builder separation
new tx flow:
```
mempool -> block builder -> proposer / validator -> block -> ...
```

builders: assemle blocks
proposers: choose+propose the block

why:
- MEV competition happens among builders
- so now validators don't need to maintain MEV infrastructure
- and now MEV extraction is a specialized competetive market

mev flow
```
		|---searchers---|
		|				|
		|				v
mempool ------------> block builder -> proposer / validator -> block -> ...
```
searcher discovers the profitable strategy (for the builder)
builder decides block composition

```
Alice's tx creates an arbitrage opportunity worth 1 ETH.

Searcher:
  executes the arbitrage
  → earns 1 ETH
Searcher → Builder:
  "Include my transaction/bundle.
   I'll give you 0.7 ETH."
Builder:
  → receives 0.7 ETH
Searcher:
  → keeps 0.3 ETH
```