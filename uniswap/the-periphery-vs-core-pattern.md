- functions in Pool contract (Core contracts, [[uniswap-v3]]) are really gas-optimized with minimum amount of checks
- *Core* contract assumes, that the *one who interacts* (Router, UI, SDK = Perimeter) responsible for input validation and handling user-level abstractions
	- no user-friendly error messages
	- no input validations
- *Core* = pure State Machine & Math Engine

WHY IS IT SAFE FOR PROTOCOL?
- bad inputs harm the caller (not protocol)
- low-lever arithmetic just reverts silently
- hard invariants ARE verified
user can harm himself, but for protocol everything is secure

**Periphery** (Router) - protects user
**Core** (Pool) - protects protocol


- secure
- gas-optimized
- flexible

[[gas]]