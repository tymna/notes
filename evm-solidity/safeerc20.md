first it wraps the low-level call and after manually inspects the result

proper ERC20:
- revert on failure
- return true on success
bool ok = token.transfer(to, amount);
require(ok, "ERC20: transfer failed");


we use it to handle different ERC20s:
- don't return any value
- return false
- return weird messages or custom errors
so we need to handle tis revert properly, cause that token influences our contract balance


in Jars i need it because of USDT just emits event, it does not return bytes value, that is expected by regular IERC20, it gets back 0, so decode reverts.
