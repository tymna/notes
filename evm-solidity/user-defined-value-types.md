`PoolId as bytes32`
- so now it is not bytes, it is redefined in another value type
- type safety (correct function inputs)

```
PoolId
   │
   ├── wrap()
   ├── unwrap()
   └── PoolIdLibrary operations
```

native [[solidity]] functions:
but to print that UDVT, i need to `unwrap()` it into `bytes32`
also i can `wrap()`back to `PoolId`

- often combined with libraries
- in [[solidity]] 0.8.8

useful for good interface/API: [[unit-testing-2026-vladimir-khorikov]]
