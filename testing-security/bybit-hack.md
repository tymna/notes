- why delegatecall tx to a random contract address?
- masked UI, signing was via hardware wallet
SOLUTIONS:
- clear, not blind signing ? 
- decode data from HW wallet

how to verify safe txes?
1. Verify an *uninitialized* tx signature *with* Safe API (signing)
	- Cyfrin CLI tool
2. Verify an *uninitialized* tx signature *without* Safe API (signing)
	- cast calldata "sig" params
	- construct and verify safe tx hash
3. Verify an *initialized* tx *with* Safe API (signing)
	! NEVER SIGN + EXECUTE
	- Cyfrin CLI tool
4. Metamask connection via QR (no key exposure, all signing on wallet)
	- but MM forms the data, could be compromised
5. Verify tx execution (calldata)
	- cast calldata
KEYSTONE WALLET!