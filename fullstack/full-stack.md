- nodejs to run website
- **synchronous** - line-by-line
	`task1 → task2 → task3`
- **asynchronous** - without it website will freeze (promise based)
	`task1 → start task2 → task3 → finish task2`

website - js (logic), 
		html, css (view)

- wallet in browser: 
	- exposes JS API (injects API into the page (window.ethereum))
	- JS calls to RPC URL
- "use this as a template..."
- write in TS -> compile to JS
              `pnmp tsc index.ts`
- *vite* to run ts

- HTML+JS = React components