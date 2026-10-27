1. `export NODE_URL=https://rpc.testnet.aztec-labs.com`
2. `aztec-wallet create-account -a main --register-only --node-url $NODE_URL`
3. `aztec-wallet deploy-account accounts:main --payment method=fee_juice --node-url $NODE_URL`
4. `aztec-wallet deploy --node-url $NODE_URL --from accounts:main --payment method=fee_juice --alias counter counter@Counter --init "initialize_public" --args 10 accounts:main`
5. `aztec-wallet simulate get_public_counter --node-url $NODE_URL --from accounts:main --contract-address counter --args accounts:main`