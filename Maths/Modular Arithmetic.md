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
ei `%` niye ja math ase sheita ke amra boli *modular arithmetic*.
### Exercise - 1
**Input:** Three integers `a`, `b`, `k`\
**Output:** Print the reminder when `a+b` is divided by `k`\
**Constraints:** `0<=a,b<=10^9` and `0<k<10^9`\
**Example Input:**
```
10000000000 10000000000 4
```
**Example Output:**
```
1
```
<details>
<summary>Solution (Exercise - 1)</summary>

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

## Properties (Part - 1)
Ektu age jei problem ta korla oitai jodi ektu change kore dei. tahole dekho to problem ta answer thik ashe naki
### Exercise - 1 (*modified*)
**Input:** Three integers `a`, `b`, `k`\
**Output:** Print the reminder when `a+b` is divided by `k`\
~~**Constraints:** `0<=a,b<=10^9` and `0<k<10^9`~~\
**Constraints:** `0<=a,b<=2*10^9` and `0<k<10^9`\
**Example Input:**
```
2000000000 2000000000 5
```
**Example Output:**
```
0
```
Jodi ager problem er solution e example input er value tula input koro tahole output ashbe `-1`. Kintu keno? `4000000000` ki `5` diye bhag korle bhagshesh `-1` hoy? Nah, output `0` ashar kotha. Ar negative number to bhuleo ashar kotha na.\
Tahole keno emon holo?\
Eitar karon bujhar jonne nicher code ta run kore dekho.
```c
#include <stdio.h>
int main() {
  int a = 20000000000, b = 20000000000;
  printf("%d\n", a + b);
  return 0;
}
```
Output:
```
-294967296
```
Areh, jog korlam duita positive number ar jogfol pelam negative number!\
Eitar karon hocche `a` ebong `b` er data type hocche `int`. `int` data type shorbochcho `2147483647` and shorbonimno `-2147483648` store korte pare. ei range er bahire store korte gelei jhamela hoy.\
Ekhon mone hoy bujhte parcho je keno amader ager problem er solution ei problem er jonne kaj korche na. Karon constraints change kore dawar karone, ekhon boro shongkhar number input dile `int` data type er variable ar number ta store korte parche na.\
Tahole solution ki?\
Jara `long long` data type er nam shunecho tara mone hoy ekta solution already ekta solution ber kore felecho. `int` na bebohar kore `long long` bebohar korlei to hoy.\
Hae thik. `long long` bebohar korlei hoye jae. Tobe arekta solution ache jeita amra `int` diyei korte parbo.
<details>
<summary>Solution</summary>

```c
#include <stdio.h>
int main() {
  int a, b, k;
  scanf("%d %d %d", &a, &b, &k);
  printf("%d\n", (a % k + b % k) % k);
  return 0;
}
```
</details>