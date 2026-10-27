- user identifies and decrypts notes that belong to him

1. Commit - note becomes ConfirmedNote and 
  - the note hash → goes into the Note Tree (on-chain)
1. Deliver the plaintext
 -  the encrypted note data, with the tag attached →
  published as a log (on-chain)
1. Discovery - recipient's PXE has to find that *log*
Note Tagging - default discovery mechanism
- recipient's PXE computes same tag, cause sender and recipient share the same secret
- PXE searches for logs with this tag, if exists it decrypts it and can spend later

Before sending a note sender is registered, so discovery in binded to addresses.  So both recipient and sender must be registered in recipient's PXE.

sender:
- compute the tag
- encrypt the note date
- emit the tagged log
- put the note hash in the tree
recipient:
- compute the same tag
- find the log, decrypt it, track the note

discovery has many places to fail:
  - sender not registered → tags never computed
  - recipient account not in this PXE → wrong half of
  the secret
  - read the balance before sync finished → scan
  hasn't run yet
  - wrong PXE / wrong keys → can't decrypt
  - log never emitted (forgot to actually send the
  encrypted note) → nothing to find
  
  > if my frontend shows a stale/zero balance, is that more likely a contract bug or a discovery/sync issue?
  - if a contract bug, we will see failed tx - note creation either works or reverts

>who computes the tag — sender or recipient — and what do they each need to know?
both parties:
sender:
	 sender's key + recipient's address
	 a · B  =  a · (b·G)  =  *ab·G*
recipient:
	 recipient's key + sender's address
	 b · A  =  b · (a·G)  =  *ab·G*
> same point, the *shared_secret*

  tag_n = hash(*shared_secret*, n)
  after that actual discovery process is PXE-internal
  ▎ Registration is local on each side; my PXE listens
  ▎ only because I registered the sender, not because
  ▎ the sender signaled me.
 
  ▎ Tagging assumes I already know my senders 
  ▎ (contracts I call, myself, known contacts) — I 
  ▎ register those; a note from a truly unknown sender
  ▎ can't be found by tagging, which is a known 
  ▎ design limitation, not a bug.
  
  ▎ I can discover notes from a contract I call 
  ▎ because my PXE already knows that contract (I just
  ▎ interacted with it) — so it can compute the tags;
  ▎ the contract just emits the tagged log, it 
  ▎ doesn't register me.