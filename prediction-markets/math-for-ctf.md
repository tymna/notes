gets: 1 total share = 0.5 YES + 0.5 NO
redeems: 1 total share + 0.5 of the winning side

problem: no integers in solidity (but we need to store 0.5)

`n` - numerator
`den` - denominator
*value of 1 share* = `n[i] / den`
*den* = `n[0] + n[1]`
*payout* = `(balYes * n[0] + balNo * n[1]) / (n[0] + n[1]))`
