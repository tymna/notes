Aztec also has something like Anvil in Foundry (we spin a local network): 
```
aztec start --local-network
```
This is a local environment, so same experience as mainnet or testnet, but just faster (proof generation can be disabled).

- we can write tests, that will run against local network (Aztec.js)
- but without them, i can **test deployment and interact directly**

1. Add test accounts that will interact with local network
```
aztec-wallet import-test-accounts
|or create|
aztec-wallet create-account -a my-wallet -f test0
```

Local network has some contracts:
- token
```
aztec-wallet deploy TokenContractArtifact --from accounts:test0 --args accounts:test0 TestToken TST 18 -a testtoken
```

- `aztec-wallet simulate` - utility, private, public (no tx and no gas)
- `aztec-wallet send` - creates tx, spends gas
- `aztec-wallet create-authwit` - authwits creation

- To interact on local network we need fee juice. Test accounts are pre funded