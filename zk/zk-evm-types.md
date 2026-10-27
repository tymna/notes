---
url: https://vitalik.eth.limo/general/2022/08/04/zkevm.html
---
1. *Type 1:* Fully-compatible, Ethereum-equivalent
	- prover time
2. *Type 2:* EVM-equivalent (remove ZK-unfriendly cryptography)
	- [[poseidon-instead-of-keccak]]
	- sill slow prover time
	- Scroll
3. *Type 2.5:* EVM-equivalent, except gas costs 
	- greatly increase gas costs for operations that are hard for ZK-prove
4. *Type 3:* almost EVM-equivalent (transitional stage)
	- remove what is hard for ZK-prove
	- Scroll, Polygon
5. *Type 4:* HLL equivalent
	- code in Solidity compiled to [[ZK-STARK]]-friendly language
	- [[ZKSync]]


