- prover executes the tx and generates a proof
- clients-verifiers check instead of re-executing
=> nodes does not need to re-execute each txs
	- they can just verify the proof

```
With execution proofs:

- A prover executes the 1,000 transactions and generates a proof.
- Node A verifies the proof.
- Node B verifies the proof.
- Node C verifies the proof.
```