Q: how [[uniswap-v4]] math works correctly, even for USDC/ETH, that have different amount of decimals?

- they operate on *raw token amounts*
$$P_{\text{human}} = P_{\text{raw}} \cdot 10^{d_0-d_1}$$
we use this formula only at the end, when interpreting the price into human-readable format

> decimal problem: UI problem, under the hood it all would work correctly