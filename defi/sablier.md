what: ready solution for handling: vesting, airdrops, etc
why: not to create custom vesting SC


- *lockup* (stream) - vesting (+vested airdrops)
	- req: fixed dates & amounts
	- +Variable Claim airdrops (later - more, else is refunded)
	- startTime, endTime, tokenAmount
	- TODO: check math:
		- linear
		- unlock linear (immediate release + linear later)![[Pasted image 20260825083635.png|290]]
		- cliff (no tokens at the beginning + unlock linear)![[Pasted image 20260825083622.png|292]]
		- unlock cliff (unlock + nothing + unlock + linear)![[Pasted image 20260825083604.png|292]]
		- exponential
		- exponential cliff
		- in steps
		- backweighted (%)
		- timelock
		- segments (exponent -> jump -> exponent -> jump)
		  ![[Pasted image 20260827083840.png|189]]
		- tranched - linear with cliff (wait -> jump -> wait -> jump)
		  ![[Pasted image 20260827083621.png|182]]
- *merkle airdrops* - on-chain airdrops
- *flow* - recurring payments, grants
	- can be topped over time
	- open-ended
	- agreement
	- amount owed=rps⋅elapsed time
- *bob* - lock tokens until specific price is reached
	- shares + interest

- permissionless, non-upgradeable

SMART CONTRACTS:
- structure:
	- monorepo with each solution as separate foundry repo
	| - airdrops
	| - bob
	| - flow
	| - lockup
		- periphery (batching)
		- core
	- one "DataTypes.sol" for every library
	- libraries for Helpers, Errors (Errors used only in Helpers and SablierV2Lockup.sol  - base abstract contract (not shared interface))
	- exploitable path: delegatecall spoofing
	  prevention: no Delegate Call, allowToHook admin only and exact return selector
- lockup:
	- linear
	  separate structs (we can use them to represent Broker (address, fee), but not as a mapping (mapping is good for some general state of the protocol)):
		- with durations (block.timestamp as a starting point)
		- with timestamps
	- dynamic
		- Segment[] = amount + exponent + timestamp
		- bigger e → less early, more late
	- tranched (jumps, repeated cliff)
		- Tranche[] = amount + timestamp
	- NFT
	- all this parts was merged into one SC
- tests:
	- categories:
		- unit (no interactions with other contracts)
		- integration
		- fork
		- invariant
	- sub-categories:
		- concrete
		- fuzz
	- separate folder for each function
	- [[branching tree technique]]

https://docs.sablier.com/concepts/streaming