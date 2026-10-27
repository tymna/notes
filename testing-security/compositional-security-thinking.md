- each component works well in isolation is not enough
	- what gonna happen if it is composed with other components?
	- [[invariant-testing]]
	- not possible to think of every attack, so dev should better have this thinking:
	  > **“I designed the system so that even interactions I didn’t think of are constrained by strong invariants.”**
	  I don't need to predict the exploit, I must identify the property that the exploit violates.
- good test suit + careful impl. of new features
	[[unexpected-control-flow]]
[[writing-secure-protocol]]