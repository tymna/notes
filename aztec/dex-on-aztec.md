- simple Uni v2 AMM, where trader and balances are private, but reserves and amounts are public

- swap
- add_liquidity
- remove_liquidity

public:
- token0
- token1
- reserve0
- reserve1
- total_shares
private:
- balances (shares per user)

1. *All actions are private*

 private contract for lp shares

so I wanted in private function to directly get public reserves.
but public runs after private, so i can not get that values to compute swap output before transferring the tokens.
- checks
- *calculate amounts* (public)
- send
- event

private (pxe)
public

!  reserves must be public
- but if they are public, we can deconstruct amounts
- so the only thing that can provide privacy here is *identity privacy* 

logic:
- swap_private that will enuque swap_public


**KEEP IN MIND:** 
> PRIVATE FIRST, PUBLIC AFTER

- all public functions are internal
- 