
`cast wallet import dev --private-key xxx`
`cast wallet address --keystore ~/.foundry/keystores/dev`
`forge script ... --account <name>`
`cast call <contract_addr> "func_selector()"`
`cast send <contract_addr> "func_selector()" <args> --from <your_account>`


```
script:
uint256 amount = vm.envUint("AMOUNT");
token.transfer(0xabc..., amount);

command:
AMOUNT=500000000000000000 forge script script/MyScript.s.sol:MyScript --broadcast --rpc-url $RPC_URL --private-key $KEY
```
