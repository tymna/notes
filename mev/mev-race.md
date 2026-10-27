https://www.paradigm.xyz/writing/ethereum-is-a-dark-forest
[[dark-forest-concept]]

- today bots - later miners
- we can try to bypass with obfuscation

if you are a miner:
- they can reorder and submit tx in their mempool
- also they can include tx in block  directly without mempool
- can try to reorg blocks by other miners

time passed, but now it is not *miners*, but searchers+block builders competing for it.
(architecture was splitted)


idea of obfuscation:
- make `burn` happen inside internal all (to not directly expose the profitable call)
	```
	Bot sees:
	get()
	 ↓
	on == false
	 ↓
	revert
	```
	but there also was another scenario:
	```
	set(true)
	→ on = true
		↓
	get()
	→ on == true
	→ pool.burn(...)
	→ $12k
	```
- tx sitting in mempool should not contain enough information for frontrunner to discover the profitable internal call by simulating
