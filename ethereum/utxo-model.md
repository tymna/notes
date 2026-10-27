- it provide privacy and parallel verification

Bitcoin has no account balances
balance of an account is just summing discrete coins:
UTXO #1: 0.3 BTC  (locked to your key)
UTXO #2: 0.15 BTC (locked to your key)
UTXO #3: 0.05 BTC (locked to your key)
wallet "balance" = 0.5 BTC   ← computed, not stored

it is good for simple transactions, but stateful logic if more convenient for programability (Ethereum) [[blockchains]]

- even because of parallelism Bitcoin is slow because of deliberate consensus choice.
	blocks are tiny and mined slowly
	so UXTOs could be parallelized to enhance throughout, but Bitcoin chooses not to.
	maximize decentralization + security, and the cost is speed.
	so speed lives in the consensus layer, not data model.
