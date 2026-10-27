if the system is complex (f. e. with [[hooks - Uniswap V4]]), we can't use `msg.sender`, because it would not represent the actual sender address

**why not to use tx.origin?**
(considered as anti-pattern)
- `tx.origin` shows who signed (initiated) the tx and who pays gas
- so it causes problems with:
	  - multi-sig wallets
	    ```
	  Carol -> Safe.execTransaction -> Router -> PoolManager -> hook
	  tx.origin = Carol
	  but correct msg.sender = Safe
	    ```
	  - [[account abstraction (EIP-4337)]]
	  - relayers

SO:
	it works only with EOAs