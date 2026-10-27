- `sqrtPriceLimitX96` - price protection
- `amountOutMin` - slippage protection
- `amountInMax` - spending limit

so on the frontend we choose slippage like 1%, 2%, 5%, but under the hood, for SC in is converted into `sqrtPriceLimitX96`
*questions, that it answers:*
- do I receive enough tokenOut
- do I not spend too much tokenIn
[[uniswap-v4]]