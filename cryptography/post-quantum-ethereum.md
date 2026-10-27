quantum computers can mathematically break traditional cryptography.
for example, private key:
- take G
- mul by secret d
- get a new point Q
*logic:* easy to compute, really hard to reverse.
now it is hard to solve, but not for quantum computers because they know an 
"easy" algorithm.

Ethereum is built on private keys (validators), signatures (**asymmetric cryptography**).

cryptographic agility - ability to upgrade core primitives without destabilizing the network

### Consensus Layer (who runs the network?)
*if validators are compomised, the whole chain is*
- validator signatures [[BLS-signatures]](they sign blocks) -> [[leanSig]] [[leanVM]]
- key registry -> attestations + real-time CL proofs -> full consensus
### Data Layer (what is stored/verified?)
*data integrity can be broken*
- replace KZG commitments
- cryptography for blob handling
### Execution Layer
- [[ECDSA]] -> [[XMSS-hash-based-signatures]]
- [[leanVM]]
- safe authentication <- account abstraction (new sig verification, wallets are not hardcoded to old crypto)
- sig precompiles (efficient verification) -> transactions -> sig aggregation


[[ethreum-signature-schemes]]

ALSO:
[[ZK-rollups]] mostly use [[ZK-SNARK]]s, so they are vulnerable as well.