 - if cast inside function - truncates
 - if in signature (function inputs) - is checked

f(uint96 x)           reverts — returndata length 0 
g(uint256 x) -> uint96(x)       succeeds, returns 0 ← silent truncation