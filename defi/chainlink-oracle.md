Oracle Problem - we need a *reliable* way to connect with external real-world data!

network of nodes aggregate data -> deliver on-chain -> receive LINK as payment for service

- ###### Data and Price Feeds
`AggregatorV3Interface = priceFeed(0x0..`int price = priceFeed.latestRoundData()`
- ###### Automation (upkeep)
	- smart contract can not execute its functions automatically
`is AutomationCompatibleInterface
`checkUpkeep()
`performUpkeep() { if {... doStuff() } }
- ###### CCIP (bridge)
- ###### Chainlink Functions (custom code in trusted environment, if too expensive for blockchain)
- ###### VRF
- ###### Data Streams (smooth perp DEX)
- ###### Proof of Reserve

#### Automation:
- Time Based
- Custom Logic (`AutomationCompatibleInterface`)
- Log Trigger (after event)

#### CCIP:

cross-chain messaging protocols = 2 pools+verification, execution system
mechanisms:
- lock -> mint
- burn -> mint
- lock -> unlock
- burn -> unlock

capabilities:
- transfer data
- transfer token
- programmable token transfers (data+tokens)

architecture:
- Sender -> Router -> Receiver
- Token Pool
- DON - commit and execute on the destination
- ARM (risk managment) - verification layer

##### CCT (token standard):
= make your token multichain from day one
[[ERC-7802 and xERC-20]]
- more easy to use some ready protocol (LayerZero, Wormole, Hyperlane, Chainlink) standart and launch a token on top of that
ho
- need to pay fees in LINK (disadvantage compared to else)

#### Chainlink Functions (code+results -> public, executed in trusted environment)
- acces to off-chain data
- cheaper compute

#### VRF 
problem: blockchains are deterministic systems (same input = same output)
- word = func(nodePrivKey, seed) + node gives a proof
usage:
- via subscription (regular)
- direct (in contract itself)

`requestRandomWords` in our function
`fullfillRandomWords` callback for Coordinator

#### Data Streams

both Data Streams and Price Feeds use DON, but:
- Data Streams - sign, but stores data off-chain, only if needed (pull-based)
- Price Feeds - push data on-chain (push-based)

#### Proof Of Reserve (transparency of digital assets)

confirm that digital asset is collateralized with RWA

- stablecoins
- wrapper assets
- tokenized comodities
- c-c apps
- defi


