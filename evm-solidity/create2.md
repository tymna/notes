new_address = keccak256(
	0xff,
	deployer,
	salt,
	keccak256(bytecode, constructor)
)