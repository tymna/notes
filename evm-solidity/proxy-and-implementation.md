
- constructor code is not visible for Proxy => initialize()
	- Proxy works only after deployment, but constructor is disappeared after deployment
- Proxy dumb, implementation - all logic
- implementation must be called only by Proxy
    - result: direct calls and prevent calls from else proxies

[[overriding abstract contracts]]