**Concentrated Liquidity**
- liq bounded within some price range
- much less tokens needed to create "green curve" that on Uni V2

**DIFFERENCES:**
- tracks $liquidity$ and $price$ -> calculates reserves between price ranges
$$
x = \frac{L}{\sqrt{P_a}} - \frac{L}{\sqrt{P_b}}
$$
$$
y = L\sqrt{P_b} - L\sqrt{P_a}
$$
- active liquidity management (*ERC721*, not ERC20)
- several fee tires (0.01, 0.05, 0.3, 1%)
- TWAP - geometric (not arithmetic)
- single sided liquidity supported

- bigger price range - less liquidity (0 -> inf = [[uniswap v2]])

higher price = higher tick 
tick - ratios between tokens
    token Y   token X
![[Pasted image 20260831122847.png|183]]

[[calculate price in Uniswap V3]]

[[structure - Uniswap V3]]

- Pool contract does not implement functions directly. Instead it has a callback function that is responsible for calling back the msg.sender, which must implement some code to execute the function that is expected.
- no security issues because the callback function verifies inputs that are provided by the Router contract or my contract

- curve of real reserves - curve of virtual reserves
  [[calculate price in Uniswap V3]]
![[Pasted image 20260902083743.png]]
 - to get real curve we slide *to the left by Xv*, to the *bottom by Yv*

[[liquidity net - Uniswap V3]]

- swap fees charged from amount in
	- problem: price ranges, price crosses ticks -> which liquidity earned each fees?
	- cumulative accounting + snapshots
![[swap flow - Uniswap V3]]
![[factory flow - Uniswap V3]]
![[liquidity math - Uniswap V3]]

[[tick spacing - Uniswap V3]]

[[liquidity flow - Uniswap V3]]
- add / increase in one function
- use $int$ (+ increase, - decrease)
	- we can't use int $int$ in [[uniswap v2]] 
- when decrease:
	- burn() - only updates the state
	- later we need to call collect() - transfer tokens back to user
		- collect() - collect fees & transfer tokens (amountOwed)
- in Pool - position owner is Manager, in Manager - owners are tracked separately

- [[The Periphery vs. Core Pattern]]

[[tick bitmap - Uniswap V3]] - fast index/search (optimization)
- 1 word identifies 256 possible *initialized ticks*
- bitmap answers -> Is tick *initialized*?
- when performing a swap, function needs to find the next *initialized tick* it will cross, flow:
```
	swap(...)
	  ↓
	current price/tick
	  ↓
	find next *initialized* tick
	  ↓
	tickBitmap helps find it efficiently
	  ↓
	cross that tick
	  ↓
	update liquidity
	  ↓
	continue swapping
```

[[fees - Uniswap V3]]
- global fees accumulators

![[fee math - Uniswap V3]]
![[fee growth - Uniswap V3]]
![[fee growth outside - Uniswap V3]]
![[position fee - Uniswap V3]]

![[TWAP - Uniswap V3]]

- needs it's own [[flash loan]] for inside-arbitrage

[[just-in-time-liquidity]]


Arbitrage:
- every pool / exchange = independent market (so no mater between which we do that)