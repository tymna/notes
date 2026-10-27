
- Native Rust
- Anchor

#### configs:
```
solana config get
```

```
solana config set --url mainnet-beta
solana config set --url devnet
solana config set --ud
solana config set --url localhost
solana config set --url testnet
```

```
solana-keygen new
```

```
solana address
```
CVTFNroNxYQE8M1fRVdCpYD3NMxwpqGX4QQCEJKSCky4

```
solana airdrop X
```
https://faucet.solana.com/

```
solana-test-validator
```

```
solana program close $PROGRAM_ID
```
- get funds that were used for deploy back (program is closed forever)

- one *instruction* = one struct + one handler

when calling other programs:
  - Account<'info, Whirlpool> — deserializes and reads the data inside. Needs the type
  definition.
  - AccountInfo<'info> — just a raw reference. No deserialization, no type needed.
- every account must be in a struct