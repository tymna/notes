1. JS engine (library, can't be used directly)
2. Runtime - takes engine and wraps with capabilities code needs. This lets you run JS/TS on a server (environment to execute the code)
   Examples:
	   - browser
	   - Node.js
	   - Deno
	   - Bun (native TS + Node-compatible)
3. npm registry - server hosting packages
4. Package manager - talks to registry, downloads packages, puts into node_modules.
	   Examples:
	   - npm
	   - yarn
	   - pnpm
	   - bun
		`package.json` - project name, dependencies
		`lockfile` - freezes versions to download identical code
5. Framework - on top of a runtime
code -> imports Framework -> runs on runtime -> uses JS engine -> runs on OS