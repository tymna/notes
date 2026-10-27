https://www.paradigm.xyz/writing/the-dangers-of-surprising-code
- code must behave in a way that user expects
- external calls are unpredictable
	- before implementing them even from well-known standards and libraries, we must be absolutely sure of how that code behaves at the EVM level
- `safe...` from what?

**Whenever I introduce callbacks/hooks/external calls, I’m not just adding functionality — I’m introducing a new control-flow boundary and must re-check my invariants around it.**

[[cross-function-reentrancy-security]]
[[unexpected-control-flow]]