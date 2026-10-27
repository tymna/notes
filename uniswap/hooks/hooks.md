why? 
- customize behavior of liquidity pools
  before/after each key operation inside the pool

what?
- external smart contracts
```
contract -> 1 hook

	 -> contract A
hook -> contract B
	 -> contract C
```


interesting decisions:
- not allow a few hooks per 1 contract
- less flexibility because of [[singleton-design-uniswap-v4]] -> hooks fixed that (compensate each other)

