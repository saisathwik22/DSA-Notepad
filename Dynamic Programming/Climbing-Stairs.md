### Leetcode 70 - Amazon, Google, Microsoft, Adobe, OYO, Siemmens, Flipkart
#### Question:
- given n number of steps, distinct number of ways to reach step n
- you can climb 1 stair, or 2 stairs at once.

### Brute Force - Recursion approach
- TC : O(2powerN) because every stair i has two options, either i+1 or i+2
- TLE for n = 44, because 2 power 44 is a huge number
  ```
  solve(n) {
    if n < 0, then return 0;
    if n == 0, then return 1;
    int oneStep = solve(n - 1);
    int twoStep = solve(n - 2);
    return oneStep + twoStep;
  }
  ```
### Memoization - TOP DOWN
- To avoid repeating states, memoize the solutions of a state
- use dp[] array of size 46 because max size of n is 45
- dp[i] = result of ith state
- example n=3
- 2 options : n-1 = 2 | n-2 = 1
- it goes on recursively like this, and n=1 state arrives twice, so store the result in dp[1]
  ```
  int dp[];
  solve(n) {
    if n < 0, then return 0;
    if dp[n] != -1, then return dp[n];
    if n == 0, then return 1;
    int oneStep = solve(n - 1)
    int twoStep = solve(n - 2)
    return dp[n] = oneStep + twoStep;
  }
  main func(int n) {
    dp = new int[46];
    Arrays.fill(dp, -1)
    return solve(n)
  }
  ```
### Bottom Up 
- use dp[] array of size n+1
- dp[i] = number of ways to climb i stairs
- predefine dp[0] = 0 because no. of ways to climb 0 stairs is 0
- predefine dp[1] = 1 because no. of ways to climb 1 stair is 1
- predefine dp[2] = 2 because no. of ways to climb 2 stairs are 2 | one is go 1step + 1step | other is go directly 2steps
  ```
  if n==1 OR n==2 OR n==3 return n;
  predefine dp[0], dp[1], dp[2] to 0,1,2
  for(i=3 ---- <=n) dp[i] = dp[i-1] + dp[i-2]
  return dp[n]
  ```

### Without using dp[] array, same bottom trick
```
a = 1, b = 2, c = 3;
for(i = 3; i<=n; i++) {
  c = b + a
  temp = b;
  b = c;
  a = temp;
}
return c;
```
