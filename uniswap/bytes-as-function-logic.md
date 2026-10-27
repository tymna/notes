```
[ f ][ r ][ command ]
  1    00    0010
  │          │
  │          └── V4_SWAP
  └───────────── allow failure
```

```
executeOperation(  
    operation,  
    shouldRevert,  
    ...  
)

executeOperation(
    SWAP_V4,
    shouldRevert = false,
    ...
);
```
[[uniswap-v4]]
