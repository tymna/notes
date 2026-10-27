“Trust this piece of hardware to execute this code correctly and keep its inputs/outputs protected.”


**prover → verifier** shape like in ZK
Off-chain prover
      │
      │ computation + cryptographic proof
      ↓
On-chain verifier
      │
      ↓
"Mathematically, this computation was correct."

TEE:
Off-chain TEE
      │
      │ computation + attestation
      ↓
On-chain verifier
      │
      ↓
"This computation happened inside
 genuine trusted hardware running this code."