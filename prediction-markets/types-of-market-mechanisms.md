[[prediction market base]]

1. Parimutuel (pool betting)
	- deposit in a YES/NO pools, lock
	- $x$ staked, $Y$ - total YES
	  $payout=x+x / Y*N$ - stake back+bonus
2. [[CPMM]] (constant-product AMM)
	+ + easy Solidity implementation
	+ + familiar DeFi pattern
	- - LPs can be exploited
3. LMSR (Hanson's Logarithmic Market Scoring Rule)
	+ + beautiful economic properties
	+ + no LP problem
	- - hard Solidity implementation
4. CLOB (order book)
	+ + no AMM risk
	+ + simple concept
	- - needs liquidity and matching


