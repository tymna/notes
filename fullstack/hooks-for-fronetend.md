###### wagmi tx-state, 2 patterns:
- 1 tx -> reactive hooks
	- useWriteContract + useWaitForTransactionReceipt({ hash })
- multi-step (approve + write) -> imperative
	- async fn: writeContractAsync → await waitForTransactionReceipt
	- manual useState
[[hook structure diagram]]
it gives return, and that must be checked inside component that i use