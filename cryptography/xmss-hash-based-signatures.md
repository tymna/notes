when creating a XMSS key, we choose the limit (how much signatures would it produce) - keys are stateful

so wallet needs to track how many txes it signed and replace the key when allowance is ran out (via some index)

- key manager (how many signing keys and what to use next)
- each tx uses different from that keys
- tree height - total supply of signing keys (20 gives 1,048,576)
>For each transaction, the wallet takes the next unused one-time signing key, signs, then saves the updated counter.

- [[merkle-trees]]