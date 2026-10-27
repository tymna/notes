- 'Field' data type
	- integers only for comparing

1) generate witness
``` bash
   nargo execute
```
3) generate vk
```bash
	bb write_vk -b ./target/*.json -o ./target
```
2) generate proof
```bash
	bb prove -b ./target/*.json -w ./target/*.gz -o ./target
```
4) verify proof with vk
```bash
	bb verify -k ./target/vk -p ./target/proof 
```

```bash
bb write_vk --oracle_hash keccak -b ./target/*.json -o ./target

bb write_solidity_verifier -k ./target/vk -o ./target/Verifier.sol
```

- every `pub` input is automatically used in building/verifying a proof