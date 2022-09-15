# Modular Arithmetic

## Modular arithmetic ki jinish?
`n % k` mane hocche, `n` ke `k` dara bhag korle, jei remainder pabo sheita\
jemon:\
`0 % 4 = 0` &nbsp;&nbsp;&nbsp;&nbsp;  `4 % 4 = 0`\
`1 % 4 = 1` &nbsp;&nbsp;&nbsp;&nbsp;  `5 % 4 = 1`\
`2 % 4 = 2` &nbsp;&nbsp;&nbsp;&nbsp;  `6 % 4 = 2`\
`3 % 4 = 3` &nbsp;&nbsp;&nbsp;&nbsp;  `7 % 4 = 3`

Another way of thinking about it:\
`n % k` er mane hocche: `n` theke jotobar possible `k` subtract korar por joto thakbe shetai hocche `n % k`

ei `%` niye ja math ase sheita ke bola hoy *modular arithmetic*.

### Exercise-1
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
<summary>Click here to view solution of Exercise-1</summary>

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
Ektu age jei problem ta korlen oitai jodi ektu change kore dei. tahole dekhen to answer thik ashe naki
### Exercise-2
**Input:** Three integers `a`, `b`, `k`\
**Output:** Print the reminder when `a+b` is divided by `k`\
**Constraints:** ~~`0<=a,b<=10^9`~~ `0<=a,b<=2*10^9` and `0<k<10^9`\
**Example Input:**
```
2000000000 2000000000 5
```
**Example Output:**
```
0
```
Jodi Example-1 er solution e Example-2 'Example input' er value gula input koren tahole output ashbe `-1`. Kintu keno? `4000000000` ki `5` diye bhag korle bhagshesh `-1` hoy? Nah, output `0` ashar kotha. Ar negative number to bhuleo ashar kotha na.\
Tahole keno emon holo?\
Eitar karon bujhar jonne nicher code ta run kore dekhen.
```c
#include <stdio.h>
int main() {
  int a = 20'000'000'000, b = 20'000'000'000;
  printf("%d\n", a + b);
  return 0;
}
```
Output:
```
-294967296
```
Areh! jog korlam duita positive number ar jogfol pelam negative number!\
Eitar karon hocche `a` ebong `b` er data type hocche `int`. `int` data type shorbochcho `2147483647` and shorbonimno `-2147483648` store korte pare. ei range er bahire store korte gelei jhamela hoy.\
Ekhon mone hoy bujhte perechen je keno amader ager problem er solution, ei problem er jonne kaj korchilo na. Karon constraints change kore dawar karone, ekhon boro shongkhar number input dile `int` data type er variable ar number ta store korte parche na.\
Tahole solution ki?

Jara `long long` data type er nam shunechen tara nishchoi bhabchen je, `int` na bebohar kore `long long` bebohar korlei to hoy.

Hae, thik. `long long` bebohar korlei hoye jae. Tobe arekta solution ache jeita amra `int` diyei korte parbo.\
Ei solution ta dekhar age ekta modulo operator er ekta property jante hobe.\

### Property-1: `(a + b) % k = (a % k + b % k) % k`
**Proof:**
> Proof ta porar age ekbar nije nije cheshta kore dekhen. ekta hint dei: uttor dekhar por mone hobe, "Ayhay, eto shohoj chilo!"

Asha kori cheshta korechen. Ekhon tahole milie nin.\
Dhorun, `a` ke jodi `k` dara bhag kori tahole bhagfol `p` ebong bhangshesh `q`\
Ekibhabe dhorun, `b` ke jodi `k` dara bhag kori tahole bhagfol `r` ebong bhangshesh `s`\
Tahole amra bolte pari je,\
`a % k = q -----------(i)`\
`b % k = s -----------(ii)`\
`a = pk + q ----------(iii)`\
`b = rk + s ----------(iv)`
> Jodi apni cheshta koreo proman na korte paren tahole baki ongsho porar age arekbar cheshta kore dekhen

Ekhon, LHS e jodi `a` ar `b` ke boshiye dei tahole amra pabo:\
`(a + b) % k`\
`= (pk + q + rk + s) % k` [From `(iii)` and `(iv)`]\
`= ((p + r) * k + (q + s)) % k`\
`= (q + s) % k`\
`= (a % k + b % k) % k` [From `(i)` and `(ii)`]

Exercise-2 solve korar jonne ja shikha lagbe shob shikha hoye giyeche. Ekhon cheshta kore dekhte paren je Property-1 er shahajje solve korte paren naki.
<details>
<summary>Solution of Exercise-2</summary>

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