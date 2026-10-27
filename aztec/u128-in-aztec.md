- we need u256 usually only for miltiplication
- but 99% of time u128 is enough
Instead they say: the values themselves are u128. Only the brief moment of "multiply two big things before dividing them back down" needs more room. For that, you borrow a Field as a scratchpad for one expression and immediately come back to u128. Cost paid only where needed .