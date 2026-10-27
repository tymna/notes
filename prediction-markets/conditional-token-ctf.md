
Conditional Token - token, which value depends on the outcome of some future event.

Polymarket uses Gnosis framework
	https://github.com/gnosis/conditional-tokens-contracts
	https://github.com/Polymarket/poly-ct-scripts
	Gnosis implementation:
	- complexity to handle:
	  - any number of outcomes (bitmask)
		  - combine bitmasks, create new token for nested outcome (Bob or Alice)
	  - nested conditions (parentCollectionId)
	  - arbitrary combination of outcomes (combinatorial markets)
> we can take all combination of outcomes and turn into tradable asset

[[Polymarket study]] just deploys Gnosis' bytecode of CTF

>we could use ERC20, to deploy YES and NO tokens
>but ERC1155 allows us to:
>hold 2 token ids inside one contract



