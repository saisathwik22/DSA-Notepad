### Leetcode 50 - Linkedin, Bloomberg, Amazon
- given double x, int n, find x power n
- example : 2.00000 power 10 gives 1024.00000
- example : 2.00000 power -2 gives 0.25000
- example : 2.10000 power 3 gives 9.26100

### Binary Exponentiation
- x power n = pow(x, n)
- if n is even, xpowern = pow(x * x, n/2)
- if n is odd, xpowern = x * pow(x * x, (n-1)/2)
- if n is negative, xpowern = pow(1/x, -n)

- `INT_MIN = -(2 power 31) = -(2147483648)`
- `INT_MAX = (2 power 31 - 1) = (2147483647)`
 
- when n is INT_MIN (-2147483648), when (-n) is applied, it gives INT_MAX + 1 (2147483648)
- so use `long` for n, so to avoid overflow issues.
- TC : O(log n)
  ```
  double solve(double x, long n) {
    if n == 0, then return 1
    if n < 0, then return solve(1/x, -n)
    if n is even, then return solve(x * x, n/2)
    if n is odd, then return x * solve(x * x, (n-1)/2)
  }
  return solve(x, (long) n)
  ```
