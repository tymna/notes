useful for:
- simulate an arb. opportuninty
- calc. optimal trade size
- solve equation
- generate data for a chart


- foundry runs a python script (external process), reads output (simple values / from .json)
```
          Blockchain
              │
              ▼
       collect pool state
              │
              ▼
           Python
              │
       ┌──────┴──────┐
       │             │
    simulate       optimize
       │             │
       └──────┬──────┘
              ▼
       profitable?
              │
              ▼
        Foundry test
              │
              ▼
       Solidity execution
```

- differential testing
```
Python:   384729182
Solidity: 384729181
```