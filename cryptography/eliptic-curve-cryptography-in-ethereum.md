in ECC curve is a set of points satisfying:
y² = x³ + ax + b
for secp256k1 (used by Ethereum):
y² = x³ + 7
(a = 0, b = 7) - designer's choice, y must != 0

P = (x, y) - random point on a curve

all operations is done modulo p (prime p) (this value is standard for secp256k1).
and curve is over finite field Fp.

1. choose field Fp
2. choose curve y² = x³ + ax + b
3. find points inside that field satisfying the curve

modulo is the arithmetic of field, in other way we will "exit"
y² ≡ x³ + 7 mod p

##### Why we need finite fields?
mod p - all arithmetic stays inside field
because in cryptography we need:
1. easy forwards computation
2. hard reverse computation
we need:
- finite system
- closed arithmetic
- deterministic pubkey generation
- hard reversing

##### Starting point
G
Q = dG (take G and add it to itself for d amount of times) - pubkey
R = kG (new point on a curve) - signatures

##### Signatures
z - hash of the message
d - private key
k - nonce
input (z, d, k) -> output (r, s)

step 1: R = kG
step 2: r = x_R mod n
step 3: s = k^-1(z + rd) mod n

signature = (r, s) - not a point on a curve

To find k, we need to solve problem with 2 unknowns.
But when we have private key, i can easily recompute this s.

attacker can see:
	(r,s)
and know:
	z
but don't know:
	d
	k

##### Discrete logarithm problem
- on eliptic curves we don't have division. We only have additions of points and duplication
- P = kG
  private key = random k added G timeі
  3G = G + G + G
- now computers just can't check that big amount of nubmers
- analogy of logarithm (find discrete k (private key), when knowing public key P = kG) 
>I should try every number (2^256), multiply it by G, and maybe that way I will be able to find that private key

Point is the coordinates itself:
- P = 7G
	~
- P = (x, y)

	Start:
	G = (x₁, y₁)
	↓
	Compute G + G
	↓
	Result:
	(x₂, y₂)
- **Private key** = a single integer (`k`).
- **Public key** = a single point (`P`) (adding the point G to itself k times.
- A **point** is represented by **two numbers** (`x` and `y`).

##### Structure
- private key - sign (32 bytes)
	- k = 32 bytes
- public key - check signature validity
	- K = k * G
	- 2 points on curve (32 || 32 = 64 bytes)
- address - derived from public key (20 bytes)
	- last 20 bytes of keccak256(public key)

