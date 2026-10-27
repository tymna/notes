```
// "Token X" -> "Token Y" -> "Fee" -> "Pool Contract Address" // e.g. USDC -> WETH -> 500 -> 0x0....
mapping(address => mapping(address => mapping(uint24 => address))) public pools;
```

struct can not be used as key:
```
mapping(Pool => address) pools;
```

we can also use:
```
mapping(bytes32 => address) pools;
```