# Modular Arithmetic

## Modular arithmetic ki jinish?
`n % k` mane hocche, n ke k dara bhag korle, jei remainder pabo sheita\
jemon:\
`0 % 4 = 0` &nbsp;&nbsp;&nbsp;&nbsp;  `4 % 4 = 0`\
`1 % 4 = 1` &nbsp;&nbsp;&nbsp;&nbsp;  `5 % 4 = 1`\
`2 % 4 = 2` &nbsp;&nbsp;&nbsp;&nbsp;  `6 % 4 = 2`\
`3 % 4 = 3`\
Another way of thinking about it:\
`n % k` er mane hocche: `n` theke jotobar possible `k` subtract korar por joto thakbe shetai hocche `n % k`\
ei `%` niye ja math ase sheita ke amra boli *modular arithmetic*.\
**Problem**\
Input: two integers `n` and `k`\
Output: print the reminder when `n` is divided by `k`\
Constraints: `0 <= n <= 10^9` and `0 < k < 10^9`
Example:
> Input:
> ```
> 5 4
> ```
> Output:
> ```
> 1
> ```