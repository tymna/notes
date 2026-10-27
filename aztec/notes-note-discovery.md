###### Note - encrypted piece of data (note hash = commitment)

commitment is stored in Note Merkle Tree (inside PXE)
managed by Nullifier Merkle Tree (inside PXE)

for spending/receiving [[UTXO model]] is used (cash)

privacy needs spending to consume-and-recreate independent notes (proven via unlinkable nullifiers), because editing a fixed account slot would leak who acted through the slot's location, even if the amount is encrypted

Sending Notes:
- on-chain (encrypted logs) -> [[note discovery]] process
- off-chain - directly shared
- self-created notes - stored in local PXE, do not need to share (**change**)

Note Lifecycle:
- NewNote (still not added in Note Tree, pending status)
- ConfirmedNote (proof, that it is added to Tree) [[note discovery]]

spend attempt -> compute nullifier -> prove "nullifier ∉ nullifier tree" ->  insert nullifier into tree (note now marked as used and this unique per note nullifier can't be used twice)

to nullify the note:
- all note fields
- nullifier key
- proof that note exists

after that circuit recomputes the nullifier and checks if it is unique and matches the proven note

same note + my secret => same nullifier.
- each time we compute it from scratch
- to nullify a note one more time, we just can't add same hash twice to Nullifier Tree, cause it was already added
so to include in Nullifier Tree we must have a proof, that this nullifier is not yet in the tree

###### Storage Slots
for private state:
how to know who is the owner of a note in giant shared Tree?
- each note has storage slot hashed into
- this slot is derived by the owning contract (Token) and contract address is also hashed into
- so all my notes are sharing the same slot 
balance = sum of all unspent notes in that slot (but no value stored and the slot itself)

Note Types: