![[Unit-Testing-Principles-Practices-and-Patterns_RuLit_Me_644505.pdf]]


##### The goal of unit testing
> If the code is hard to unit test - it needs improvement.

GOAL: *sustainable* growth of a software project (no tests -> no *scaling*):
1) protect immutable logic (*sustainability*)
2) safely integrate new features/refactor (*scalability*)
- less entropy -> easier to grow

- tests must "help the project"

	test
	-> value
	-> cost

> Code is a liability, not an asset.
> Test is the code that solves problem (ensuring app correctness).

[[coverage]] = good negative indicator, bad positive

Good Test Suite:
- integrated in dev cycle (automatically / regularly triggered on every code changes)
- targets only most important parts of code (skip getters (already tested assertions) / already tested libs => [[branching tree technique]])
	- *business logic* (domain model) - priority
	----
	- infrastructure code
	- external deps and services
	- glue-code (routers, outer exec. wrappers)
- provides max val with min maintenance costs
	- smart structure

NEED TO KNOW:
1. What a 'good test' is? (what a bad one is)
2. Write / refactor valuable tests.


##### What is a unit test?

Unit Test - 
	- verifies single unit of behavior
	- quickly
	- in isolation from other tests

*London*: isolation from system's collaborators
- isolation means to double all classes specifically for unit tests ('test double', one kind of dep. 'mock')
- lighter version
- no need to mock immutables (they called "values")

*Classical*: test isolation from each other

- test one class (contract) at a time
- isolated from each other

DEPENDENCIES:
- shared (database, state variable) => can be mocked
	- slower exec. => better use for integration tests
- private (inside single test)
	- faster exec.
	- mutable / immutable
- out-of-process (some testnet Mock for fork tests)
![[Pasted image 20260909102639.png]]

shared dependency is usually out-of-process (any deployed thing shared across my tests)
- state is maintained externally
- multiple contracts/tests interact with that exact state
![[Pasted image 20260909103530.png|342]]

> tests are not for verifying units of code, they must verify *units of behavior*


end-to-end test - subset of integration tests

- [[integration tests]]/end-to-end after unit


##### The anatomy of a unit test

1. Structure
	- AAA - arrange, act, assert ()
	  there is a sense in TDD (first test, later code) / not to write tests looking at the code, but think about actual behavior
	- if multi-staged - better be split to a couple of tests (for [[integration tests]] can be multi-staged for efficiency)
	- comments or just lines between sections
	  
	- Arrange - the largest section (reusable)
		- constructors / internal functions
		- test coupling: a modification of one brakes others (BAD practice) => *a modification of one test should not affect other tests*
		- test must be *readable*
		- inherit
			- unit: common mocks, users, constants, helpers, setup
			- integration: not foundry case, but useful for databases
	- Act - single line of code
	
	Encapsulation = protect an object’s internal state from being changed in invalid or unexpected ways.
	No invariant[[ ]]violation.
	- Assert
		- one test = one behavior (not one assertion)
		- too much assertions - bad => meaningful abstractions:
		```
			struct PositionData {
		    uint256 amount;
		    uint256 fees;
		    int24 tick;
		}
		
		function getPosition() external view returns (PositionData memory);
		```
	- expressive names 
	  method_scenerio_expectedResult - not really useful + increases maintenance cost (mental),
	  better in simple human words
		  - no strict naming policy
		  - as describing to a non-programmer
		  - word_word_word
		**test contract (for function/feature = unit + 'Test') → behavior**
		! don’t include the name of the SUT’s method in the test’s name (I DON'T TEST THE CODE, I TEST APPLICATION BEHAVIOR)
		- but for utility testing - SUT's method names are okay
	- tests can be grouped / *fuzzed*
		Delivery_for_today_is_invalid()
		Delivery_for_tomorrow_is_invalid()
		The_soonest_delivery_date_is_two_days_from_now()

---

### Making your tests work for you

##### The four pillars of a good unit test MOVE TO EXCALIDRAW

`1.Protection against regressions
	- it ensures that the feature will work as intended (bugs protection)
`2.Resistance to refactoring`
	- must not cause *false positives* (the fewer - the better)
		- if ignore - quality of code will deteriorate (become fragile)
		- re-evaluate the suit and reduce brittleness
	- what causes the false positives?
		- test structure (to much detail of the SUT) => decouple from implementation details => verify expected result (not code)
			- if the test if failing it must mean that the behavior of SUT is uncorrect
			- test must answer: what went wrong?
			- why to even tests the SUT algorithm, but no outcome that I expect?
priority - (1), (2) - can be developed over time

working functionality and passing test = true negative
broken functionality and failing test = true positive
(2) helps to catch:
broken functionality and passing test (does't catch an error) = false negative
working functionality and failing test = false positive

*accuracy*:
- protection against regressions (false negatives)
- resistance to refactoring (false positives)
![[Pasted image 20260915101336.png|395]]

`3. Fast feedback`
`4. Maintainability`

- test scores 0 if one of categories is 0
  $valueEstimate = [0..1]*[0..1]*[0..1]*[0..1]$
! use for [[smart contract testing]]
![[Pasted image 20260915103321.png|283]]
max out: *resistance to refactoring*, maintainability
choose: *protection against regressions* / fast feedback
	the more win on one - more loss on another

![[test pyramid]]
![[test properties <-> test types]]

- it is okay, if some project will have less unit tests that integration
- sometimes integrations tests = e2e test / unit = integration

writing tests - *black-box* (no impl. details)
while analyzing tests / utility code - *white-box* (based on impl. code)


#### Mocks and test fragility
Test Double:
- mock (outgoing interaction) - ERC20Mock (commands / commands+queries)
- stub (incoming interactions) - oracle calls (queries)
	- not verify part results, only final result of my Suite

good interfaces:
![[Pasted image 20260917104301.png|358]]
- no leak of implementation details for user interactions (must be done internally)
- *tell-don’t-ask*
- expose as less as you can (only code that directly help clients)
	
[[The Periphery vs. Core Pattern]]
	- periphery makes a friendly, high quality interface for clients
[[hexagonal architecture]] (proper connection between systems)
	Business Core
	     ↓
	   Port (interface)
	     ↓
	   Adapter (logic)
	     ↓
	External system

good API design - tests have fractal structure, but each verify the behavior on a specific level
so tests does not need to verify that details directly, it must verify the final result, that client will have

- mocks needed for inter-system communications (not intra-system)
- if out-of-process dep. is inside app, and not a part of observable behavior - no need to mock

#### Styles of unit testing
1. *Output-based* - pure functions, calculations ([[functional programming]])
2. State-based - state verification
3. Communication-based - mocks

idea:
	separation between business logic and side effects:
		code for business logic (code that makes a decision = immutable (functional) core)	`computeSwap()`
		code that incurs side effects (code that acts upon that decision = mutable shell, dumb)
		`swap()`
		so now our unit test can verify one unit of behavior just on different layers

but *output-based* architecture is not always a win, not every test must be like that
question to ask:
> **Can I separate the business decision/calculation from the state mutation without making the architecture worse?**

If yes → worth doing.
If no → keep it together.
([[hexagonal architecture]] is better for my usecases)

#### Refactoring toward valuable unit test

Four types of code:
1. Domain model and algorithms (HIGH VALUABLE UNIT TESTS)
2. Trivial code (NO NEED TO TEST)
3. Controllers (coordinates) (BRIEFLY TESTED IN INTEGRATION TESTS)
4. Overcomplicated code
	- refactoring: split to algorithms and controllers
	- need to test the logic

- sometime for test it is useful to divide code and logic into different part, after - mock it
[[all in memory until final settlement]]

- test valuable pre-conditions
bad:
```
function swap(...) external {
    // validate everything
    // calculate price
    // calculate fee
    // update liquidity
    // update ticks
    // update oracle
    // calculate deltas
    // transfer tokens
    // emit events
}
```
better:
```
swap()
   │
   ├── validate
   │
   ├── swapMath(...)
   │
   ├── updatePosition(...)
   │
   ├── updateTick(...)
   │
   ├── updateAccounting(...)
   │
   └── settle(...)
```

- we have different layers of behavior (🧅), and each of them could be unit tested
- complex code must not have a bunch of collaborators
	either
	*deep* (complex or important)
	or 
	*wide* (work with many collaborators)


#### Integration testing
- one *happy path*
		- successful execution of a business scenario
- *edge cases* (that can't be covered with unit tests)
		 - error in results of happy path execution
		 - integration error (uncorrect result)

simple project test pyramid:
`-------------`
`|           |
`|integration|
`|           |
`|-----------|
`|           |
`|   unit    |
`|           |`
`-------------`


the longest happy path: with all out-of-process dependencies
goal - capture interactions with *every* external system (even if a few tests are needed)

![[fail fast principle]]

- real instances of managed dependencies, unmanaged - mocks
  my contracts - deploy
  not mine - use mock
- fork tests for actual real instances ~ [[end-to-end tests]]

- if edge case was unit-tested - no need to repeat in integration

[[end-to-end tests]] does not substitute unmanaged dependencies with mocks
- can be used as sanity checks before deployment

- YAGNI stands for “You aren’t gonna need it”


to make good integration test:
1. Explicit domain model boundaries
2. Reducing number of layers
	```
	Business/domain logic (domain model) (core)
        ↓
	Application/use-case contracts (application services layer) (periphery)
        ↓
	External protocols / blockchain infrastructure (infrustructure layer) (UI, indexer, etc)
	```

- integration test can contain multiple AAA, AAA

##### Mocking best practices
- only for unit tests
- for very-edges (not everything)

for external interactions (because dependencie is unmanaged):
- only expected calls
- no unexpected calls
##### Unit testing anti-patterns
- test private methods indirectly (as part of observable behavior)
	- if needed to be tested - make it independent
- widening the public API surface for tests is a bad practice
- don't put in Arrange algorithms from codebase -> better hardcode the expected result
- no adding production code for testing