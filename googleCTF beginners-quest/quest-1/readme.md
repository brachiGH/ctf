![](VSCodium_yPTqNYp1bt.png)

```JavaScript
const o = [52037, 52077, 52077, 52066, 52046, 52063, 52081, 52081, 52085, 52077, 52080, 52066].map(a => String.fromCharCode(a - 0xCafe)).join('')
console.log(o)
```