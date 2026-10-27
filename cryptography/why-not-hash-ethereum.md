- why to make Ethereum rely on [[eliptic curve cryptography in Ethereum]] if it is not quantum resistant?

- not so big problem in 2014-2015
- [[hash-based-signatures]] are huge (100x - 500x bigger, so blocks are more expensive)
- "one-time" Lamport signatures
- extra features of ECC - ecrecover and [[BLS-signatures]]
- Bitcoin used it

but it is possible to make a hash-based blockchain:
- [[ZK-STARK]] fix the size problem (signatures compressed)
- overall improvements

hash-based isn't the only [[post-quantum-ethereum]] option