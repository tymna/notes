- still based on ECC
- same interface, but more complicated logic than ECDSA
- if several people signed the same message, that signatures can be aggregated into one short signature => verifier can check only one signature against the group's public keys

| **Step**             | **ECDSA**                      | **BLS**          |
| -------------------- | ------------------------------ | ---------------- |
| Generate private key | random integer                 | random integer   |
| Generate public key  | sk × G                         | sk × G₁          |
| Sign message         | use private key + random nonce | sk × H(m)        |
| Verify               | elliptic curve equations       | pairing equation |
difference: what is the signature and how verification works (it is longer)
*signature aggregation*

| Validators | Without Aggregation | With Aggregation |
| ---------- | ------------------- | ---------------- |
| 100        | 4.8 KB              | 48 bytes         |
| 1,000      | 48 KB               | 48 bytes         |
| 100,000    | 4.8 MB              | 48 bytes         |