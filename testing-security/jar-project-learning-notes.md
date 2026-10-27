 - make interface (freeze for external, allow changes for internal)
 - don't write all tests for simple contracts
 - first deeply contracts, after that frontend and indexer (not over/under doing)
 - AI makes refinement cheap, so I must use it also
FINISH CONTRACTS FIRST!

- we not always need fuzz tests (mostly for math), but invariant test are all about flow and can be applied to any system
- big input domain and non-trivial handling = fuzz-worthy

- "indexed" if i ll filter by that event param