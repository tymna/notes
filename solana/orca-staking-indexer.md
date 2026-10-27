- orca positions (**`usePositions`**)
- txs data ✅ (transaction_crawler)
- accounts data ✅ (program_subscribe)

I fetch data from Orca SDK only in usePositions.ts. 
It is used to know what positions i can stake (when i click "Stake")
We do an RPC call `fetchPositionsForOwner`, so basically, my database must contain this data. Our indexer will fetch positions for owner and write the data into the database so we can display what positions we have. 
So this is the place where I should index not only my program but also workup program / or leave just RPC call.

agenda:
1. So if we have some full range position on orca, we will show them on the website via `usePositions`
2. If no, We can index everything instead of unstaked-positions, so option: - **API does one RPC call** (`getTokenAccountsByOwner`) at query time — minimal, scoped
   орки є сдк
	[12:15 PM]наче
	[12:16 PM]там фільтруєш по пулу
	[12:16 PM]кожен наш пул дозволяє позиції лише з конкретного пула орки
	[12:16 PM]індексером не варто цього робити

- TODO: delete "backfill"
- so now i backfilled it. In the future, when new positions will be opened, it will be filled automatically (TODO: test - open a new pool)
1. When indexer will give all needed data, i can move to [[API]]
so, 1st:
- do we need some custom data for it? or because it generated from idl, it already provides it in a convenient way for frontend (like if we need pool state, we just go to init pool database and get it from it. or we create custom database?)
1) does in needs txes in a proper order
- how it actually work?
   this is one of the problems: `Але, треба продумати як зберігати транзакції, Щоб спочатку всі витягнути, бо воно від нових до старих качає. А потім у вірному порядку обробити, бо інакше це просто піпець`
	- ONLY FOR TX HISTORY AND FOR NOTHING ELSE (BUT that is where i ll need custom table)
3) write all getters for frontend
4) integrate into frontend
