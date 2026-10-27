
- cloud provider
- has MCP

can deploy from:
- GitHub
- CLI
- [[Docker]]


what I need to deploy:
- frontend
- server
- api
- indexer (but i use a binary file for docker, maybe I can reuse it here, not to build cargo there?)
- postgreSQL

1. Node.js (js runtime environment) entry point is "index.ts"
	- dev - locally, hot reload
	- build - compile (what [[railway]] runs first)
	- start - run the compiled code
fix deps
fix build
should i make a fronend as a separate workspace