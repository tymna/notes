###### 1. MVC - Model View Controller (server to mix html with data)
- poor scalability

###### 2. SPA - Single Page Application (with API, a lot of logic is moved to frontend) (if page is an app)
- we can request data and make changes without reloading
- scalable, interactive
- too much JS, poor loading timeline

Thin -> *Thick* client

###### 3. BFF - Backend For Frontend
- frontend | BFF ([[API]] aggregation) | backend
- for web and mobile apps, we get data in different ways
	- web app -> BFF1 -> backend
	- mobile app -> BFF2 -> backend
- faster integration
- scalability limits

SPA's problem - performance (to much JS)
###### 4. SSG / ISG / SSR (part of rendering back to the server)
> I choose what page what framework will use
- SSG - Static Site Generation (fast, if content is almost not changing)
- ISG - Incremental Static Generation (if data changes, but rarely)
- SSR - Server Side Rendering (if need fresh data and SEO)

RSC - React Server Components
- splits work between server and client - where code runs (server/browser)
###### 5. Modular Frontend Monolith
- different domains, system is divided
- adds complexity
###### 6. Microfrontends
- deploy independent frontend applications, put together in runtime
