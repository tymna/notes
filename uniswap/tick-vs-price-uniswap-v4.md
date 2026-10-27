- **tick** →  where on the logarithmic price grid
- **sqrtPriceX96** → in what part of that range

![[Pasted image 20261012090235.png]]
	$P = 1.0001^{n}$
	that gives the price of that tick, not the **actual current price**

- off-chain - ticks, on-chain - sqrtPriceX96

in contract we store:
- tick 
- sqrtPriceX96
*swap logic* -> continuous space √P (*sqrtPriceX96*)
*liquidity logic* -> discrete space of *ticks*
> we can calculate *tick* from *price*, but store both for convenience (not to use $log$ each time)
> we store the $sqrt$ of the price, which is convenient for calculations
