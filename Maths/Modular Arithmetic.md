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
### Exercise
**Input:** Three integers `a`, `b`, `k`\
**Output:** Print the reminder when `a+b` is divided by `k`\
**Constraints:** `0<=a,b<=10^9` and `0<k<10^9`\
**Example Input:**
```
2 3 4
```
**Example Output:**
```
1
```
<details>
<summary>Solution</summary>

```c
#include <stdio.h>
int main() {
  int a, b, k;
  scanf("%d %d %d", &a, &b, &k);
  printf("%d", (a + b) % k);
  return 0;
}
```
</details>