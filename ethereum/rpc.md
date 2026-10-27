RPC - the only way to communicate with blockchain
RPC endpoint is basically your **database query layer for Ethereum**.
JSON-RPC API:
- POST JSON request -> node returns result

providers run nodes and rent a URL
so RPC is like outsourced node

send JSON-RPC request to node
node exposes JSON-RPC [[API]]
so we can use that methods to interact with chain

? what is client


rabby wallet:
when i send tx in rabby:
1. Build & sign tx
2. Send JSON‑RPC request to a node
3. Node gossips & block gets proposed/finalized
4. Read back status via JSON‑RPC

- I always need a signature, tx must always be signed with private key
	- browser wallet
	- hardware wallet
	- backend script

usually we sign locally and then call `eth_sendRawTransaction`
read-only rpc - no signing (reads don’t move funds or change state, so no signature is needed)
- use JSON‑RPC, but they’re just queries. No state change → no fee → no signature.
state-changing (need signing)
- to be valid, they must be signed with the private key of the `from` address and then sent via `eth_sendRawTransaction`.


RPC provider = *Ethereum node-as-a-service*
> they can run RPC nodes without staking any ETH (not in validator mode)
- they run and maintain Ethereum nodes
- i can do same thing from my pc
- they run standard client on server

1. **Run execution + consensus clients**  
2. **Put them on serious hardware**  
3. **Add a gateway in front** 
4. **Scale horizontally**  
5. **Operate and monitor**