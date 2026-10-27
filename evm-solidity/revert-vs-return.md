should the user's action fail?
- yes: `revert`
- no, function just needs to be skipped: `return`


`revert`
- undoes the whole tx
`return`
- only ends *my* function
- after that current function execution ends, and nothing else from it is not executed