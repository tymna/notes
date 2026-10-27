###### new in niswap V4:
3. [[singleton-design-uniswap-v4]] -> [[flash-accounting]] (gas savings)
4. [[hooks]]
5. [[dynamic-fees]]
6. [[ERC-6909]]
	- start: internal accounting + [[all in memory until final settlement]]
	- end: final ERC20 transfer

![[structure - Uniswap V4]]

![[currency abstraction - Uniswap V4]]
[[user defined value types]]
![[PoolManager-uniswap-v4]]
![[account delta - Uniswap v4]]
![[huge storage in Uniswap V4]]

![[swap flow - Uniswap V4]]

![[hooks - Uniswap V4]]

- getters for most important functionality - else low-level reads from storage
	- expose not everything, but what user actually needs
		- so no sense for simple / important value
		- useful for complex internal state, that user will get via library

[[tx.origin-problem]] => [[tx.origin-solution-uniswap-v4]]
[[permit2]]

[[position-management-uniswap-v4]]:

TODO (hooks):
- write simple hook exercise
- check limit order hook