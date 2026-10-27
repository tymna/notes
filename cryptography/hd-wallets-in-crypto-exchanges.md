- each user on crypto exchange needs address for deposit
  we don't want to generate private key for each and store million of keys and risk

solution: HD wallet
- only one master seed exists instead of million if keys

	12/24 words -> Master Seed -> **Master Private Key** -> *key tree*
- we can get each key from one seed-phrase

- from **Master Private Key** we can derive:
	- xprv (extended private key)
	- xpub (extended public key)

###### architecture:
*offline* (on secure server priv keys are stored): 
**Master Seed** -> xprv 
				│
			------------	
	Private Key #1            Private Key #2
				│
*online* (creates all, but can't still the money):
				│
	            xpub
				│
			------------	
	Public Key #1            Public Key #2