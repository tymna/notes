- because of [[singleton-design-uniswap-v4]] all transfers happen inside one pool (so we don't need to transfer tokens across different pools)

logic:
- tokens are transferred only after final balance-changes
- but any else balance-changing operations (swap / liquidity) updates internal *delta* (snapshots)