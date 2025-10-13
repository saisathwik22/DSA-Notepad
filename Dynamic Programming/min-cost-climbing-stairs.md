### Leetcode 746 - GOOGLE
#### Question:
- cost[] given, where cost[i] = cost of ith step
- you can start from step at index 0 or index 1
- once you pay the cost, you can either climb one step or two steps
- return min cost to reach top of the floor

#### Approach - Recursive brute force
- TC : O(2 power N)
- solve(int i) function
- if i >= n, then return 0
- a = cost[i] + solve(i + 1) | b = cost[i] + solve(i + 2)
- return min(a, b)

#### Approach - Top Down
- store result of ith state in dp[i]
- TC : O(n)
  ```
  int[] dp;
  solve(i, cost) {
    if i>=cost.length, then return 0;
    if dp[i] != -1, then return dp[i]
    int a = cost[i] + solve(i + 1)
    int b = cost[i] + solve(i + 2)
    return dp[i] = Math.min(a, b)
  }
  main funct(int[] cost) {
    dp[] = new int[1001]
    Arrays.fill(dp, -1)
    return Math.min(solve(0, cost), solve(1, cost))
  }
  ```
