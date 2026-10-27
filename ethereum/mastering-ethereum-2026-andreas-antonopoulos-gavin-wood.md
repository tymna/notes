##### [What Is Ethereum?](https://masteringethereum.xyz/chapter_1.html#chapter-1-what-is-ethereum)


Ethereum - open source, decentralized computing infrastructure that executes programs called smart contracts.
- not intended to use as a digital currency network (it could, but the point of Ether is a utility currency)
- designed to be a programmable blockchain that runs a virtual machine capable of executing code
- Turing complete - can run any kind of code (gas is the limit)
- after the move to PoS, it is split into:
	1. EL (execution layer) -> runs contracts, transactions
	2. CL (consensus) -> secure the network, selects and finalizes blocks

>early idea: programmable money → smart contracts for assets and transfers
>shift: general-purpose computing platform → “world computer”
>result: Ethereum = decentralized computation layer (not just finance, any program logic)

Development was divided into 4 stages:
- Frontier (Ether, first DApps, "difficulty bomb" to later transition to PoS)
- Homestead (for devs)
- Metropolis (end of Ethereum 1.0)
- Serenity (parallel 5 sub-stages)

Ethereum is many machines + one shared memory.

- gas is the mechanism that allows Turing-complete computation while limiting the resources that any program can consume

DApp - smart contract + UI
Web3 - apps on decentralized protocols

Bitcoin updates are more stable, Ethereum "move fast and break things"
- as dev I must be ready to migrate, update, etc; so I must have some control over smart contracts, before protocol is not stable
> You’d better keep up because no one will slow down for you.

##### [Chapter 2. Ethereum Basics](https://masteringethereum.xyz/chapter_2.html#chapter-2-ethereum-basics)

1 Ether = `1 * 10^18` wei

Wallet - application to manage Ethereum account

- small tx before big (accounts can be created in a wrong way)
- 2 papers with seed phrase, store in secure place as it was cash

- each node stores local copy of a blockhain to validate contract execution

- EOA - account with priv key
- contract account (if to smart contract, we need to use the tx and tx data as input)

code:
- contract = class
- transfer has a gas limit, so with contracts exec can be reverted

##### [Chapter 3. Ethereum Nodes](https://masteringethereum.xyz/chapter_3.html#chapter-3-ethereum-nodes)

after PoS, node must run 2 pieces:
- consensus client - nodes agreement on history of the blockchain
	- in code it checks:
	  - BLS signatures
	  - attestations
	  - double / surround vote
	  - slashinng proofs
	  - fork choice
	  - all consensus PoS logic
- execution client - execution+verification (what happens inside the block?)

- rules of how nodes behave are fixed

to set up a node, we need to use a client.
- each node downloads full blockchain



we can also run *remote client* - wallet functionality

adv:
- direct interactions and deployment
- privat information querying
disadv:
- maintenance

ethereum-node
├── consensus
└── execution 

- running a node (Infura, Alchemy) ≠ validator
	- validator (need to stake 32 eth)
- there are solutions: one-command / Dappnode if i want to run a node simpler

hard fork - new version, that is not compatible with old one
	old nodes on old version, updated on new
	usually old version dies fast

every client has a JSON-RPC API
accessed from:
- HTTP request
- libraries:
	- Viem (frontend)
	- web3.py (bots, scripting, automation, deployment+testing)
	- alloy (Rust) (indexer, security)
*remote client*:
doesn't store full blockchain
- mobile wallets
- browser wallets
- hardware wallets

less hardware, more scalability (if state will grow up, it is more expensive to run a node, so the chain will be less decentralized):
- history pruning (history, state) -> keep what is needed, drop ancient data
- Verkle tree ->  smaller proofs
- zk-EVM
  
for users:
- cheaper txs
- better RPC
- more noderunners

##### [Chapter 4. Cryptography](https://masteringethereum.xyz/chapter_4.html#chapter-4-cryptography)
[[cryptography]]
for now everything is NOT encrypted 
- encrypted = can be decrypted ≠ hashed
 and can be read. In the future, with ZKps it could be changed (but still remaining consensus).

PK => EOA
- private key
- public key

PKC-based system ([[eliptic curve cryptography in Ethereum]] = asymmetric cryptography) for authentication and authorization
- trapdoor functions - invertable if you know some piece of information to reverse the function
- eliptic curve cryptography
*digital signature* - code that can be produced only with the knowledge of private key
- to generate a private key, we just generate a random number ([[CSPRNG]]). Chance of duplicate is 1/300 mil
	- entropy (mouse moves, noise) -> OS -> CSPRNG -> 256 random bits -> k
! there are almost enough private keys to give every atom in the universe an Ethereum account

**public key** - point on a curve (x, y), that satisfies eliptic curve equation
	- we can multiply, but can't divide
	- Ethereum uses uncompressed pubkeys, so relevant prefix is 0x04 (65 bytes)
> 04 + x-coordinate (32 bytes) + y-coordinate (32 bytes)

**hash function** - map data of arbitrary size to data of a fixed size
- for keccak256 hash collisions are effectively impossible

- determinism
- verifiability (eﬃcient (linear complexity))
- noncorrelation
- irreversibility
- collision protection

hash 64 bytes (with no prefix) -> get 32 bytes hash -> take 20 last bytes = Ethereum address

EIP-55 checksum addresses - regular addresses but with uppercase + lowercase
- letteres = checksum
- is it a correctly formatted address? no symbol is misplaced?

**Validators [[cryptography]]**
*slashing* - punishing validator by subtracting some ETH
- every validator must sign all their consensus messages
- every signature is stored in block
[[BLS-signatures]]:
- we can't use ECC signatures because of a lot of validators
	- chain can handle now 2600 mes/sec, but target was 900 validators until [[BLS-signatures]] idea arrive
	- more validators, more decentralization (not TPS)
	- signature aggregation -> only one stored in a block
	- enable detection of malicious validators (each node can check if signature valid, if not repeating; all written in clients code)

*blob transactions* - move big data from layer 2 cheaper
- all data from L2s must be posted in Ethereum, so it is downloaded and verified by all the nodes
Solution: post not all data, but only commitment to it
- to verify:
  1. Download temporarily
  2. Create commitment + generate small proof + simple verification (achieve DAS)
    - solution: [[polynomial-commitment-scheme]] (data can be represented as polynomial)


##### [Chapter 5. Wallets](https://masteringethereum.xyz/chapter_5.html#chapter-5-wallets)
container for private key and systems for managing these keys
2 types:
- nondeterministic (all independent)
- deterministic (from seed)
	![[Pasted image 20260708120024.png]]
	- mnemonic + salt = seed (from it priv keys are derived)
	- generate master private key
	- derive child keys
	
	- branches and subbranches can be used for different departments (organization)
	- seed - best way to store wallets


hot wallet - keys online
	- automatic signing
	- but: needs single process handling / setup with multiple wallets
cold wallet - keys NOT online

[[HD wallets in crypto exchanges]]
	m
	 ├── m/44'
	 ├── m/44'/60'
	 ├── m/44'/60'/0'
	 ├── m/44'/60'/0'/0
	 ├── m/44'/60'/0'/0/0
	 ├── m/44'/60'/0'/0/1
	 └── ...
	 
Security:
- most secure seed - that no one can recover (all copies are destroyed)
- harder to recover <=> more secure
simpler = better => seed phrase recovery:
	a) withstand natural disasters
	b) geographically separate from hardware wallet
	c) be in a secure place
	d) have tamper-evident packaging
	- false security: divide seed into pieces of paper

option:
- seed and passphrase
- passphrase can be stored digitally (useless without seed)

safe setup:
1. Hardware wallet
2. Safe backup (not stored digitally)
3. Plan of inheritance
+ backup once a year

EIP/RIP - protocol level
ERC - app-related changes

- separate mempool for EOA txs and UserOperations

RIP-7560 - handling AA for L2 (clean)
- moving towards validation in contracts, not on protocol level
- can't be used directly on Ethereum Mainnet, because nodes would be able to process txs (requires all client's upgrades)
EIP-5806 - run custom code by EOA through a "delegate call"
*EIP-3074* - AUTH, AUTHCALL - but now, we are not trying to modify EOAs, but move towards AA
**focused now:**
*EIP-4337*
*EIP-7702* - temporarily delegate to smart contract (upgrade of 3074)

Social Recovery:
- key is lost
- guardians sign a tx to update wallet's signing key

ENS - like DNS (ip -> google.com)

##### [Chapter 6. Transactions](https://masteringethereum.xyz/chapter_6.html#chapter-6-transactions)

5 tx types:
- 0x00 - legacy
- 0x01 - EIP-2930 ( + access list field)
- 0x02 - EIP-1559 ( + base fee + priority fee)
- 0x03 - EIP-4844 ( + blob gas)
- 0x04 - EIP-7702 ( + delegation designator)
	- set the code in EOA

Nonce:
- not stored, counted while tx
- replay protection
- + execution in correct order

! important: keep track in apps
- tx will stuck, if previous not included in block (prev. nonce)
- if same nonces, diff data - 1/2 will be confirmed

> not used gas is refunded

tx with value - payment
tx with data - invocation
tx with both
tx with none

data:
- 4-byte selector
- function args

tx: 
- first byte - tx type
- tx type payload

- chain id in signature

contract creation tx - empty "to" field with data payload (optional: eth)

offline signing:
- create the tx
- transfer unsigned tx to offline device (via QR / flash drive)
- transmit signed tx back to an online device
tx -> node -> validator in block -> network

**MEV (Maximal Extractable Value)** is the extra profit someone can make **by controlling or influencing the ordering of transactions in a block**.
- sandwich attack - bot profits from another users large trade
	Bot buys
	↓
	Big buy (raises the price)
	↓
	Bot sells
- proposer/builder separation
- private mempools - tx directly to builders and validators
now:
tx -> builder (through private mempool) -> include in block -> send the whole block to validator

##### [Chapter 7. Smart Contracts and Solidity](https://masteringethereum.xyz/chapter_7.html#chapter-7-smart-contracts-and-solidity)

deprecated: selfdestruct() - remove code from storage, refund gas 
tx is atomic: one reverted - all reverted

###### Languages
1. Imperative - state of program is constantly changing
2. Declarative - explain what result I want to get, not how to get it step by step

library - deployed once, but reused
```
this.externalFunction();
```

- C3 linearization for multiple inheritance
	- rightmost inheritance order
		- but constructor runs from left to right

errors:
- assert for invariants (`Panic(uint256)`)
- require (`Error(string)`)

- try/catch - catch an error and decide what to do with it (not fully revert execution, BUT only for external calls) = act first, then react
- if/else = check first, then act


for catching events - WebSocket (wss)
for single calls (function/data) - RPC

library call - always a delegatecall (so origin = EOA)

gas is not refunded if "out of gas"
- evaluate gas costs during development

##### [Chapter 8. Smart Contracts and Vyper](https://masteringethereum.xyz/chapter_8.html#chapter-8-smart-contracts-and-vyper)
- built-in security+easier auditing:
	- no modifiers
	- no inheritance
	- single file / module system
	- no same-name functions
	- type conversion with built-in function (safe upcast)
	- overflow protection at the compiler level
- decorators (nonreentrant, deploy)
- C99 scoping rules (easier auditing)


##### [Chapter 9. Smart Contract Security](https://masteringethereum.xyz/chapter_9.html#chapter-9-smart-contract-security)
Defensive programming:
- minimalism/simplicity
- code reuse (libraries)
- code quality (like aerospace engineer)
- readability/auditability
- test coverage

Exploits:
- reentrancy (cross-function, cross-contract, read-only)
! PROTECT VIEW FUNCS ALSO
> **don't let another contract observe or interact with your contract while it is in an inconsistent state** => 
	*all state must be written before any external call*

- reentrancy guard for [[EIP-1153 (transient storage)]] stores the lock in a temporarily storage (cheaper)
use:
- Stateless libs

- prevrandao with future block or vrf
- careful with callbacks
- check call and send return
- prevent front running: commit+reveal, minTokenAmountOut
- prevent floating points and precision:
	- use large numbers (gives more precise result)
	- multiplication first
- decentralized oracle solutions / TWAP
- external input validation
- signatures: must contain nonces, avoid abi.encodePacked, chainId (use [[EIP-712]] + ECDSA lib)
- CONFIGURATION!!!
	- test deploy/upgrade scripts
##### [Chapter 10. Tokens](https://masteringethereum.xyz/chapter_10.html#chapter-10-tokens)
fungible tokens
NFT ≠ another NFT

intrinsic - blockchain
extrinsic - connected to Real World

- would the protocol work the same without the token?
- "utility token" - fundraising tool for startups (not regulated)

IERC20
'

'

- permit with sig, no on-chain approve, relayer does the job for you
- ERC-223 to check if contract support token that is transferred (tokenFallback)
- ERC-777 helps with adoption, more intuitive, but harder, so less used
	- tokensReceive -> no need to transfer from and approves (directly push tokens to the contract)


NFTs:
- each token has unique identifier (id)
- ERC1155 - each token has id, and can be fungible/nonfungible
	```
	Alice:
	  Gold   (ID 1): 1000
	  Silver (ID 2): 500
	  Sword  (ID 3): 1
	```

EIP-165
- verify, if contract supports interface (built-in into 1155)

[Chapter 11. Oracles](https://masteringethereum.xyz/chapter_11.html#chapter-11-oracles)
oracle - person who communicated with gods (Greece)
- human, software, hardware
> smart contracts for funds distribution after death

oracle:
- collect data
- transfer data on chain with signature
- make the data available

types:
- immediate-read
- publish-subscribe
- request-response

data must be verified: proofs & [[TEE]]

cross-chain messaging:
- relay - execution first, settlement later

##### [Chapter 12. Decentralized Applications](https://masteringethereum.xyz/chapter_10.html#chapter-12-decentralized-applications)
![[Pasted image 20260818102606.png]]

![[Pasted image 20260818102625.png]]

NO SINGLE POINT OF FAILURE
(can have off-chain components, but for convenience, not mandatory)
- we must be able to fully rely on an on-chain data

![[Pasted image 20260819110711.png]]

1. Smart Contracts
	[[tornado cash]] was blocked "officially", but still can be used now
	essential data and application logic on chain, anything else - off-chain
2. Data Storage
	smart contract itself
	indexer+database
	[[IPFS]] - each files is hashed (identifier) (HTTP replacement)
	[[merkle-trees]]
3. Frontend (UI)
- develop on local chain first

- Scaﬀold-ETH: npx create-eth@latest (simple ui to interact with contracts and a burner wallet (yarn))

hosting:
- centralized - Vercel
- decentralized - [[IPFS]] (only static)
	eth.limo - gateway layer
	- in IPFS we store hash, with is not user-friendly
	- limo - reverse proxy (hash -> §§§.eth.limo)
	flow:
	https://mydapp.eth.limo
	        ↓
	eth.limo receives the HTTPS request
	        ↓
	resolves mydapp.eth through ENS
	        ↓
	reads the ENS contenthash
	        ↓
	gets something like ipfs://bafy...
	        ↓
	retrieves the files from IPFS
	        ↓
	returns them to your browser over HTTPS
- people 100% know that it is website related to my domain (PERSONAL BLOG)
##### [Chapter 13. Decentralized Finance](https://masteringethereum.xyz/chapter_10.html#chapter-13-decentralized-finance)
- AMM: linear curves allow complete pool drainage
- Lending Markets: overcollateralized - in case of volatility - collateral is liquidated
	- concept of incentivization is fundamental (game theory principles to ensure that participants act in ways that maintain and improve the network's functionality and security)
	- borrowing is not "taxable"
- Oracles
- Stablecoins
	- algorithmic always failed
- Liquid Staking + Restaking
- RWA
- Bridges
	- models:
	  - lock and mint
	  - mint and burn (own token)
> regulators cannot attack the blockchain itself, they can target its users and developers
- code should remain free (same as developers)

##### [Chapter 14. EVM](https://masteringethereum.xyz/chapter_10.html#chapter-14-evm)
- everything state-changing computed by EVM (only simple ETH transfers not)
- just a computation engine
- if tx run successfully on a sandbox - real-world state is updated

future:
- publish blocks and verify blocks - separate tasks (statelessness) (searchers and builders)
- verkle trees for small proofs
- you don't store the full EVM, only state root

classic Merkle tree = hashed membership tree;
*Merkle Patricia tree* = hashed, prefix-compressed key–value database structure.

- changing non-empty storage slot to zero refunds gas
- deprecating / adding opcodes is complicated
- EOF is a bytecode wrapper, but it's development was stopped

##### [Chapter 15. Consensus](https://masteringethereum.xyz/chapter_15.html#chapter-15-consensus)
- safety (nothing bad)
- finality
- liveness (something good)

- forks keep Ethereum alive during network delays (tree, not chain)
- real purpose of mining - supporting the chain
- PoW needed CPUs, which where limited
- Beacon -> Ethereum validators

nodes - validation
validators - attached to nodes
	1. Block proposing
	2. Creating attestations
each validator is a node, but not each node is a validator


slot - 12 seconds
epoch - 32 slots

validator can propose only one block at a time
- not punished in PoW (requires some work, but at the end - only one excepted)
- punished (requires no work)
only one attestation (much less fees)

bad behaviour - slashing (takes part of staked ETH)

- accountable safety (more that 1/3 of validators must be dishonest)
- plausible liveness

we need 2 stages (local  + global)

Validator A runs LMD-GHOST on their local view to get the head of the chain. Here is
validator A's view of the network:
Validator A attestation: head block: block 3
Validator B attestation: head block: block 3
Validator C attestation: head block: block 3
The result is block 3, so validator A publishes block 4 on top of it.
Inside block 4, validator A saves the three attestations voting for block 3 because they were
not included in previous blocks.

- diversify clients

##### [Chapter 16. Scaling Ethereum](https://masteringethereum.xyz/chapter_16.html#chapter-16-scaling-ethereum)
- we anyway need scaling solutions like L2
The Scalability Trilemma:
- decentralization
- security
- scalability

- main challenge: increase scalability without centralization and less security 
- currently centralized sequencers reduce MEV because they process transactions in the exact order they are received
  future - decentralized sequencing mechanisms
-  Ethereum plans to achieve partial parallel execution 

Archive Node (more expensive to run) can provide state, historical blocks and state at any block (indexer is more easy to build)

- rent a storage?

- solution for MEV: Proposer-Builder separation (just makes it more transparent)

Rollups (L2s):
- smart contract on L1 (stores L2 state) (settlement)
- off-chain (L2 execution)

3 stages of roll-up development:
0 - centralized governance
1 - proper proof system
	- users can safely exit
	- some centralized components remain
2 - truly decentralized
	- fraud system open to everyone (permissionless)

Optimistic: need to wait for challenge period to withdraw to L1

Based: L2 sequencer = Ethereum validators (no centralized sequencer)


weak statelessness:
[[verkle trees]] (key, value)
- *witnesses* - compact collection of state data necessary to execute a block's tx
reason: [[merkle-trees]] produce large *witnesses* (can't be verified by stateless validator)

strong statelessness:
- wallet knows current state and generates witness to each tx

ETHEREUM SCALLING APPROACH:
- improve, but don't sacrifice decentralization and security
	- rollups, danksharding (cheaper rollups <- cheap temporary data space (blobs) on L1)
	- statelessness
	- final settlement on L1

##### [Chapter 17. Zero-Knowledge Proofs](https://masteringethereum.xyz/chapter_17.html#chapter-17-zero-knowledge-proofs)
[[zk]]
- tnx to crypto space
- ZKPs for EVM:
	- some nodes that execute txs + create a [[ZK proof]]
	- other light nodes just verify the proof
	- bigger throughput and high decentralization
- Fiat-Shamir heuristic - a noninteractive zero-knowledge proof system
- zk-VM: universal circuit - general purpose zk computer (not to create different circuits each time)
- zk-EVM: proves execution for EVM of EVM