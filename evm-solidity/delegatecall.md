With `delegatecall`:
- `msg.sender` stays the same
- `msg.value` stays the same
- storage is the caller’s storage
- code comes from the target

so if we loop msg.value, the contract effectively treated the same 100 ETH as 300 ETH