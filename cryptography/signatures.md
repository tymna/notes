
message -> hash(message) -> sign(hash, privKey) -> ecrecover(hash, splittedSignature)

eliptic curve digital signature algorithm
[[eliptic curve cryptography in Ethereum]]
ECDSA:
- generate key pairs
- create signatures
- verify signatures (need: signature, message, pubkey)
![[Pasted image 20260112094149.png]]

r - x on secp256k1 = kG
s - proof, that signer knows privKey (number computed from the message hash, private key, and nonce)
v - positive or negative y


! 2 signatures would be valid
! invalid sig => returns address(0)