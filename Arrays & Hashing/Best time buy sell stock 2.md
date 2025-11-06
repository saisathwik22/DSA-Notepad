### Leetcode 122 - Google
- given prices[], price[i] = price of given stock on ith day.
- can only hold at most 1 stock at any given time.
- return max profit can achieve
  
- example: prices = [7,1,5,3,6,4] profit = 7 (4 + 3)
- buy at price 1 and sell at price 5, profit = 4
- buy at price 3 and sell at price 6, profit = 3

- iterate i from 1 to n
- for every i, check whether prices[i] > prices[i-1] ?
- if yes, then add their difference to the profit
- TC : O(n) SC : O(1)
  ```
  profit = 0
  for(i = 1 to n, i++) {
    if prices[i] > prices[i-1], then profit += (prices[i] - prices[i-1])
  }
  return profit
  ```
