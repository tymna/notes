1) what must be true?
2) where should it be enforced?
3) how to prove it false?

RULE: never derive tests from the implementation
- before function body exists:
	- interface, NatSpec, Requirements:, properties.md
- independent computation

DESIGN: how do i make "X" hold?
TEST: how could "X" fail?

properties (both for building / testing):
1. Invariant (what is true)
2. Delta / postcondition (what changed by exactly how much)
3. Authorization (why may call this, who can't)
4. Input domain (which inputs are legal)
5. Ordering / time (call sequences, reentrancy, time)
6. Conservation / rounding (who pays?)

properties.md
| Prefix | Shape
| INV-n  | 1 invariant               |
| POST-n | 2 delta / postcondition   |
| AUTH-n | 3 authorization           |
| DOM-n  | 4 input domain            |
| ORD-n  | 5 ordering / time         |
| CONS-n | 6 conservation / rounding |

rungs:
1 - impossible to express
2 - impossible by construction
3 - checked at runtime
4 - only tested

unit - this brunch computes what its doc say
fuzz - i know which inputs are possible
invariant - i know which states are reachable
fork - outside world behaves like my mock

CHECKLIST before tests:
1. Purpose (one sentence)
2. Invariants
3. Per function (precond, postcond, reverts)
4. [[branching tree technique]] (one leaf - one test) + modifiers
5. Open the code (what would I write differently?)
6. Negative space (what is not tested)
7. Grade (mutation must kill test suite, not code)

CHECKLIST before function body:
- one-sentence purpose
- properties.md
- every property assigned a rung
- interface + NatSpec + Requirements: / Notes:
- committed

