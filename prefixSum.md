# Try to solve this problem
[Prefix Sum Query](https://www.spoj.com/problems/CSUMQ/)

## Brute force approach
```c++
int n;
cin >> n;
int arr[n];
for(int i = 0; i < n; i++) cin >> arr[i];
int q;
cin >> q;
while(q--) {
  int left, right;
  cin >> left >> right;
  int sum = 0;
  for(int i = left; i <= right; i++) sum += arr[i];
  cout << sum << endl;
}
```
### Time complexity
The while loop runs `q` times and the inner for loop runs `left - right + 1` times. The worst case value of `left - right + 1` is `n`. Therefore, the time complexity of the algorithm is `O(q*n)` or `O(n^2)`. Can we do better? For that, let's learn what prefix sum is.

# Prefix Sum
Prefix Sum is also called Cumulative Sum.

## Definition
Let `arr` be an array. The prefix sum of `arr` is an array, `pf` that is defined as -
- For `i = 0`, `pf[i] = 0`
- For `i > 0`, `pf[i] = pf[i - 1] + arr[i - 1]`

Yeah, the definition is quite useless if you are trying to understand prefix sum for the first time. Let's look at an example.

## Example
Lets say, `arr = {a, b, c}` is an array where `a`, `b` and `c` are elements of `arr`. Then prefix sum of `arr` will be `pf = {0, a, a+b, a+b+c}`

## Properties of Prefix Sum
- `pf[i]` is the sum of first `i` elements of `arr[i]`
  - `pf[2]` is equal to `arr[0] + arr[1]`
  - `pf[0]` is `0` (because sum of first 0 elements is 0)
- `pf[j] - pf[i]` is the sum of elements from index `i`(inclusive) to index `j`(exclusive) of `arr`
  - `pf[3] - pf[1]` is equal to `arr[1] + arr[2]`
  - `pf[4] - pf[0]` is equal to `pf[4]`

## Lets try to solve the problem with prefix sum
```c++
int n;
cin >> n;
int arr[n];
for(int i = 0; i < n; i++) cin >> arr[i];
int pf[n+1];
pf[0] = 0;
for(int i = 0; i < n; i++) pf[i+1] = pf[i] + arr[i];
int q;
cin >> q;
while(q--) {
  int left, right;
  cin >> left >> right;
  cout << pf[right+1] - pf[left] << endl;
}
```

### Time complexity
The time complexity for computing the prefix sum array is `O(n)`. The time complexity for calculating the sum of sub-array from `left` to `right` is O(1). Which is much better than the bruteforce approach.

# Fun Fact
Prefix sum of natural numbers are called triangular numbers (i.e. number of objects that can be perfectly shaped into an equilateral triangle). Try to figure out why triangular numbers are related to prefix sum of natural numbers. Details about triangular number is below:
- [Triangular number - Wikipedia](https://en.wikipedia.org/wiki/Triangular_number)
