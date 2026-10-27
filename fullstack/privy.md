old: seed phrase
new: email

PROBLEM IT FIXES: onboarding
- It allows the user to connect a wallet to some social account and later it would be recoverable even if the user has lost the private key or seed phrase. 

Privy - user onboarding and embedded wallet infrastructure
log in: email, phone, passkey, wallet
embedded wallets: created automatically or manually
gas sponsorship: built in

>it is not a smart contract, it is off chain infrastructure

- embedded wallets
- TEE + key-splitting
	Distributed Key Sharding - splitting key into encrypted shares, stored across separate security boundaries
	Flow:
	1. Generate key
	2. Shard key (immediately split into encrypted shares)
	3. Distribute shares
	4. Full key never persists
	
	1 part - user's share
	2 part - Privy's share
	3 part - recovery share
	the come together only inside TEE, just to produce the signature
- performance at scale
- modular APIs + SDKs

-  MetaMask stores our key in the browser but Privy is not purely browser-side.  So it needs to be split to be securely stored.

Privy is OAuth client (middleman):
- Privy can claim: "Google confirms this is user X (this Google account / email), and they authenticated just now."
- after login, key is binded to specific accounts


- I don't manage seed phrase, but trust that it is stored securely