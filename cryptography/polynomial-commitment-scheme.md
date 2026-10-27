$p(x) = p₀ + p₁x + p₂x² + ... + pₙxⁿ$
$p(x) = Σ pᵢxⁱ$ (for $i = 0$ to $n$)
> $n$ is the degree of the polynomial and $pi$ are all its coeﬃcients


### 1. Create commitment
##### 1) Trusted Setup
- someone generates a random  $s$
- they compute: $s$, $sG$,  $s^2G$, ...
- this points are published
- secret is destroyed
to compress an entire polynomial into one small object, we just represent the whole polynomial by it's value at that one point
we need a secret, because it provides that i can't cheat while computation and output will be truthful
> it is a hidden constant that makes the commitment scheme secure
##### 2) Take the data from the blob and convert in to polynomial
any data can be converted into polynomial (data = array in a blob)
- [12, 45, 7, 91]
- each value can be interpret as a point
	  Index      Value
		0    →      12
		1    →      45
		2    →      7
		3    →      91
- n points with x values, there is one polynomial of degree n - 1

- we can use [[merkle-trees]], but there is a better solution:
##### 3) KZG Commitment
- my blob became a polynomial, so I can calculate elliptic curve point
- $P(x)=7+5x+3x^2$
- $C = 7G + 5(sG) + 3(s^2G)$
### 2. Generate(KZG Proof)

### 3. Verify