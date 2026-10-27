4 *market mechanisms*: Order Books, AMM, P2P, Parimutuel Pool

core object - *outcome share*
- YES = 1 unit of collateral (if happens, 0 if does not)
- NO = 1 unit of collateral (if doest not happen, 0 if does)
share becomes more expensive and you earn
> the goal: adjust the price of YES/NO shares according to how much people have bought
(if I am right, shares will be redeemed as $1 => bought for $0.60, got $1, profit: $0.40)

$N = \frac{1}{\text{share price}}$

- market must be fully collateralized
> collateral held by the contract ≥ complete *sets outstanding* × 1 unit
- supply(YES) == supply(NO) == *sets outstanding* (not the combined supply) (maximum possible payout)

4 stages:
1) creation (question, outcomes, deadline, who+how decides the truth)
2) trading (*market mechanisms*)
3) resolution (decentralized/optimistic oracles, community verification, no oracle (blockchain state))
4) redemption (1:1 exchange of shares to collateral)

contract guarantees mint/burn/redeem math, but not current prices
so arbitrage:
	YES = $0.55
	NO = $0.52
	sum = $1.07
	
	contract shop: price = $1
	user shop: price = $1.07
	so I can mint in contract for 1, but sell for 1.07

jobs:
- analysts
- market makers
- arbitrageur

types of bets:
1) binary YES/NO
2) index/scalar (with number)
3) spread/threshold (over-under)
informed vs. uninformed traders
- attract both


WE NEED:
*Core market mechanics:*
1. Price Engine
2. Resolution Spec
3. Oracle / settlement mechanism
*Operational layer:*
4. Liquidity model
5. Incentive design
6. Risk / governance