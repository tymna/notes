- organization that builds infrastructure around [[MEV]] market
- designed [[mev-boost-protocol]]

now their idea shifter from:
**“Let’s build infrastructure that makes MEV work.”**
to
**“Let’s prevent MEV from centralizing Ethereum.”**

current major project - BuilderNet

before in [[mev-boost-protocol]]: operated one centralized block builder
builderNet = decentralized block-building network using TEEs

```
Searchers
	↓  
BuilderNet (currently here are builders)  
	↓  
Block
	↓  
Proposer
```

so MEV is still there but it is *decentralized*
- validator must decide to use this infrastructure (must be adopted)
- **BuilderNet** could not be built into Ethereum protocol
- **ePBS** potentially would be built