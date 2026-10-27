- change the RPC => change where wallet sends transactions

standard [[rpc]]:
- `public node -> public mempool -> block construction (builder -> proposer -> execution)

private [[rpc]]:
- `private RPC provider ->` [[private-transaction-routing-system]] `-> block construction (builder -> proposer -> execution)
[[proposer-builder-separation]] created a market from that, so we can build blocks according to our 'private' policies.