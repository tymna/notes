```
        // sqrtPriceX96 * sqrtPriceX96 might overflow
        // So use FullMath.mulDiv to do uint256 * uint256 / uint256 without overflow

        // 1 / P = X / Y - USDC / WETH
        // 1 / P has 1e6 / 1e18 = 1e-12 decimals

        // sqrtPriceX96 == sqrt(p) * Q96
        // Q96 = 2^96
        // sqrtPriceX96 * sqrtPriceX96 = p * Q96 * Q96
        //                                   192 bits
        //                  256 - 192 = 64 bits
        //                  2**64 / 1e18 = 18
        // P = (sqrtPrice96 / Q96) * (sqrtPrice96 / Q96)
        price = FullMath.mulDiv(slot0.sqrtPriceX96, slot0.sqrtPriceX96, Q96);
        // price = sqrt(P) * Q96 * sqrt(P) * Q96
        //       = P * Q96
        // 1 / price = 1 / (P * Q96)
        price = 1e18 * 1e12 * Q96 / price;
```
![[Pasted image 20260902084333.png]]