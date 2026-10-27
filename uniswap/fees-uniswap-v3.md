problem:
	pool is still represented by curve $x*y=k$
	but lp provider earns only when price is inside his price range (`[tick lower, tick upper]`)
	- we can't use [[uniswap v2]] shares (because everyone earns different amounts)
	- we can't loop through positions afterwards
logic:
	so we need *per-position, range-aware fee accounting*