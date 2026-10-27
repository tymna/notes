					end-to-end tests
				/                    \
		smart contracts	            Dapp
				|                      |
		    fork tests          full flow simulation
			/        \
	1 - testnet     2 - mainnet



system is defined on different levels, so for [[smart contract testing]] E2E is fork tests (*a full business flow through the contracts, with their real external blockchain dependencie*),
for DApp is full flow simulation with all system components (UI, wallet, etc)