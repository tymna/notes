[[EVM]]


- <font color="#4f81bd">Storage write (cold): 20,000 gas</font>
- <font color="#4f81bd">Storage read (cold): 2,100 gas</font>

- <font color="#f79646">Storage write (warm): 2,900 gas</font>
- <font color="#f79646">Storage read (warm): 100 gas</font>

- Memory expansion: quadratic cost
	- f(n) = n²
- Stack ops: 3 gas
- Calldata read: 3 gas per word

require(amount > 0, "zero"); // stack op
require(msg.sender == owner, "auth"); // CALLER op (2 gas)
require(balances[msg.sender] >= amount, "bal"); // SLOAD

packing for:
	rarely-written
	frequently-read
optimise both reading and writing


why [[L2 1]] is cheaper and why ETH is cheap now?