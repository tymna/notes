tick gives the price of some token in terms of other token
it always represents the prices based on: token0 relative to token1

```
p(i) = 1.0001 ^ i
i = 0
p = 1
```

```
i = 10
p = 1,0010004501
one unit of token0 = 1,0010004501 units of 
token1
```

```
i = -10
p = 0,9990005498
one unit of token0 = 0,9990005498 units of 
token1
```

why 1.0001?
with each tick the price moves by 0.01% ~ 1 bps
tick spacing - for each pool
- they chose a geometric price progression where each tick is a 0.01% multiplicative step (but any number could be chosen)
- one price movement = one basis point

tick - where on net are you
sqrtPrice - where in the range exactly