- different for each pool
- price range = multiple of tick spacing
- lover tick spacing (less volatile pools):
	-> tighter ranges
	-> more concentrated liquidity
	=> more gas while swap
	- if we cross more ticks, it takes more gas (more iterations)
	- if tick spacing is higher - we just remain in the same tick
more concentrated liquidity => more fees per dollar deposited (for LP provider)
	- it gives leverage, because every dollar is active within the range

less concentrated:
|----|----|----|

more concentrated:
|-|-|-|