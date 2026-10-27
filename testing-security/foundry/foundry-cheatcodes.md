- `vm.label` to put a label on contracts in Traces
- `vm.mockCall` control output value

- funds
  `deal(address, uint)` - ETH
  `deal(address token , address to, uint256)` - ERC20
  `hoax(address, uint)` - deal + prank

- `forge inspect src/Stablecoin.sol:Stablecoin storage ` state vars
- `forge inspect src/Stablecoin.sol:Stablecoin methods` funcs
- `forge inspect src/Stablecoin.sol:Stablecoin abi` interfaces
