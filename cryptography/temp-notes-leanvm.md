- simple [[ZK-VM]] that could be formally verified:
	- [[hash-based-signatures]] aggregation
	- also for exection layer
- [[lean-language]]
- simpler that Cairo

we could have use circuit, but VM is more flexible

4 opcodes:
```
ADD 
	-> arithmetic over fiels
MUL 
DEREF -> access memory
JUMP -> controls exectution
```
2 [[precompiles]]:
```
POSEIDON2
EXTENSION_OP
```

 