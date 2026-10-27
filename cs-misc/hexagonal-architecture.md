idea:
	- keep the business logic in the center (independent of external systems)
	- everything else is connected through ports (interfaces) and adapters (implementations)
	- each consists of 2 layers: domain (logic, should not depend on ->) and application service 

```
Port (interface)
      │
      ├──→ Adapter 1 (implementation)
      ├──→ Adapter 2
      └──→ Adapter 3
```

```
IPriceOracle
    │
    ├──→ ChainlinkAdapter
    ├──→ UniswapAdapter
    └──→ MockOracle
```

```
Business Core
     ↓
   Port
     ↓
   Adapter
     ↓
External system
```