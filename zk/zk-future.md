longterm: [[zk-block-verification]]

move from Keccak-based [[merkle-patritia-tree]] to a binary tree with a more provable hash (Poseidon2 / BLAKE3) ([[poseidon-instead-of-keccak]])


- different clients have different logic of proving, but they are proving the same thing:
```

Implementation A  |  Proves Ethereum block execution using zkVM A
Implementation B  |  Proves the same execution using zkVM B
Implementation C  |  Proves the same execution using zkVM C
```


clients are now verifiers [[zk-block-verification]]