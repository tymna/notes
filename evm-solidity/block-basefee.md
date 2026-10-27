- every block has a gas limit
- $target = \frac{gasLimit}{2}$
  $gasLimit$ - set by validator in their client config
![[Pasted image 20261021091848.png]]

- `basefee` - minimum price per gas unit every tx must pay

- if prev. block:
   used more that target - base fee rises
   less - base fee falls

- base fee is burned and not paid to validators

