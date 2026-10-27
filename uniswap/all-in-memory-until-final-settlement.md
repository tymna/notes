> The fact that all side effects are contained in memory until the very last moment
 improves testability a lot.

why is it also better for architecture?
 |
 v
[[account delta - Uniswap v4]]
[[EIP-1153 (transient storage)]]

- only one function at a time (reduces reentrancy surface)
- clear tx boundary
- cheaper execution because of internal changes (final at the end) (gas)
- separate computation and execution
- improves testability (unit - one property)
- easier invariant protection