$1 << n = 2^n$
powers of 2 can be represented directly with bit shifting

fuzzed:
![[Pasted image 20260916102112.png]]
> -> almost 2x optimization for all operations that we are doing *(1, 255)*
- works when exponent is a *runtime input* (because compiler knows simple optimizations)

not optimized by compiler:
```
2 ** num
!=
1 << num
```
optimized by compiler:
```
2 ** 100
=
1 << 100
```

- `EXP` cost increase when the exponent needs another byte:
```
num = 255  → exponent = 0xff   → 1 byte
num = 256  → exponent = 0x0100 → 2 bytes
```

```
1 << 1    → same gas
1 << 255  → same gas
1 << 256  → same gas
1 << 257  → same gas
```
	  