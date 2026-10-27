
- EVM operates on 256-bit words, so smaller data (f. e. address)  must be normalized
- free memory pointer![[Pasted image 20260116103531.png]]
- event (2 indexed params - log3: not indexed data offset, length of data, signature, param, param)

- Bitwise operations
  - not(value) - Bitwise NOT (flips all bits)
  - and(a, b) - Keep only bits that are 1 in BOTH (for getters)
  - or(a, b) - Combine values
- **Mostly no sense for packing specifically** — solc with `--via-ir --optimize` handles it well enough
- ![[Pasted image 20260122101902.png]]
	![[Pasted image 20260122101917.png]]
- calls
	- **staticcall**(g, a, in, insize, out, outsize) - for pure/view functions (read-only, no state changes)
	- **call**(g, a, v, in, insize, out, outsize) - for state-changing functions or sending ether
	- **delegatecall**(g, a, in, insize, out, outsize) - executes in caller's context (preserves msg.sender, storage)
- nums:
  Positions/offsets/selectors → hex
  Counts/amounts/shifts → decimal   
- use when I need to prepare memory
- call() useful for getters (for external contract) with multiple/complex params
	- Dynamic returns (bytes/string): 27.5% savings - biggest win
    - Multi-parameter reads: 14% savings                                                                                       
    - Simple getters: 13.6% savings  
- 2 vals - in memory (0x00, 0x20)
  more - use ptr
- dynamic array: `[ptr]    [ptr+0x20] [ptr+0x20]`
			   `[length] [el1]      [el2]`  
- mapping slot = keccak256(key, slot of mapping)
- nested mapping slot
  key1 => key2 => val
 keccak256(key2, keccak256(key1, slot of mapping))
 - first indexed, after non-indexed
 - if **calldata** - read from it directly, DON'T copy to stack
 - little assembly functions inside solidity code
 - [[inheritance]] puts base contracts first
 - bit flags: use powers of 2 as constants so or/and/not toggle individual
  bits without collision