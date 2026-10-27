```solidity
// Parent
function foo() public virtual { /* base */ }

// Child  
function foo() public override {
    super.foo();     // parent logic
    // extra logic   // extend
}
```

## Abstract contracts
- Non-abstract parent: can be inherited AND deployed standalone
- Abstract parent: can ONLY be used through inheritance