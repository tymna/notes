- before, pool fees were fixed ([[uniswap-v2]], [[uniswap-v3]]):
	- when creating a pool, we set fee tier
	- fees charged for swaps
	- and go to LP providers

[[uniswap-v4]]
- `fee` is still a part of pool identity
- but it can hold the dynamic fee flag
- and now control over fee tier is gone to the hook (that we specified while adding the Pool)


###### hook logic:
- average gas price -> some `fees`
- higher gas price -> lower `fees`
- lower gas price -> higher `fees`

are there any problems in this model?
- gas price manipulation
	set by swapper, so he controls what fee tier he would get
	who benefits?
		- large swappers
- average poisoning
	all gas prices are added to that average
solution:
- use `updateDynamicLPFee` (condition -> update)
- [[block.basefee]], not `tx.gasprice`
	cons:
		only once per block

[[cumulative-average-formula]]
- need to store only 2 values + `constant`
- later just compare `current gas` vs `normal/average gas`

[[dynamic-fees-hook-architeture]]