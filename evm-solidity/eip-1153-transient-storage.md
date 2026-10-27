##### MOSTLY FOR: DeFi, callbacks, flash loans and cheap reentrancy

before:
- memory
- storage

now + 
- transient storage (temporary)
	  - cheaper that storage
	  - exists for entire tx
	  - shared across all calls to the contract during tx
	  - erased when the tx finishes
https://www.youtube.com/watch?v=mugTyD70rDk

- how works + when the slot is "WARM" how to use it
- PROJECT: transient storage optimization


TLOAD
TSTORE (price same as warm SSTORE)
	- cold - first call to a slot in current tx (2100)
	- second - was accessed earlier (100)
	- dirty (not 0x00... also cheaper) (100)

assembly {
	tstore(slot, value)
}

for *slot*
bytes32 constant LOCK_SLOT = keccak256("myprotocol.reentrancy.lock");  
bytes32 constant CALLER_SLOT = keccak256("myprotocol.callback.caller");

- *cheaper reentrancy guard*
	- ! use openzeppelin ReentrancyGuardTransient
- *storing context for callbacks*
- approve (if allowance will be spent inside this tx)
