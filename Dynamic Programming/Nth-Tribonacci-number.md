### Leetcode 1137 - AMAZON
#### Question
- given n, return T(n)
- T(0) = 0, T(1) = 1, T(2) = 1 | T(n) = T(n-1) + T(n-2) + T(n-3)


#### Brute Force Recursion
- TC : O(3 power N) SC : O(n)
  ```
  solve(n) {
    if n == 0, then return 0
    if n == 1 OR n == 2, then return 1
    a = solve(n-1)
    b = solve(n-2)
    c = solve(n-3)
    return a + b + c
  }
  ```
#### Memoization - Top Down
- TC : O(n) SC : O(n)
  ```
  int[] dp;
  solve(n) {
    if n==0, then return 0
    if n==1 OR n==2, then return 1
    if dp[n] != -1, then return dp[n]
    a = solve(n-1)
    b = solve(n-2)
    c = solve(n-3)
    return dp[n] = a + b + c
  }

  dp = new int[38]
  Arrays.fill(dp, -1)
  return solve(n)
  ```
#### Bottom Up
- TC : O(n) SC : O(n)
  ```
  func(n) {
    int[] dp = new int[n+1]
    if n==0, then return 0
    if n==1 OR n==2, then return 1
    dp[0] = 0; dp[1] = 1; dp[2] = 1;
    for(i = 3; i<=n; i++) dp[i] = dp[i-1] + dp[i-2] + dp[i-3]
    return dp[n]
  }
  ```
#### Space O(1) - Bottom Up

  ```
  solve(n) {
    if n==0, then return 0
    if n==1 OR n==2, then return 1
    a=0; b=1; c=1; d=a+b+c
    for(i=3; i<=n; i++) {
      d=a+b+c
      a=b; b=c; c=d
    }
    return d;
  }
  ```
