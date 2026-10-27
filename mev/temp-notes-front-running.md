1. I submit tx
2. Bot see profitable opportunity
3. Bot takes data from tx I sent
4. Bot sends his tx
5. Bot's tx executed before mine
6. My tx is reverted

Txs are included into blocks not as they were sent. So if bot set higher priority fee -> his tx is gonna be executed first

- higher priority fee
- direct communication with block builders

front-runner (BotA) can be front-ran (BotB), but BotB can use [[private-mempool]]