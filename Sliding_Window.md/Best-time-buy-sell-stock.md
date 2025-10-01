### Leetcode 121
#### Question:
- array `prices[]` given, `prices[i] = price of given stock on ith day`
- choose a day to buy stock and a day to sell that stock.
- choose such that profits are maximum and return it.
- buy and sell can't belong to same day
#### Brute Force
- TC : O(n*n) SC : O(1)
  ```
  int res = 0;
  for(i = 0 -----> n) {
    int buy = prices[i]
    for(j = i + 1 -------> n) {
      int sell = prices[i]
      res = Math.max(res, sell - buy)
    }
  }
  return res;
  ```
#### 2 Pointer Approach
- TC : O(n) SC : O(1)
  ```
  int l = 0, r = 1, maxProfit = 0;
  while(r < n) {
    if(prices[l] < prices[r]) {
      int profit = prices[r] - prices[l]
      maxProfit = Math.max(maxProfit, profit)
    } else {
      l = r;
    }
    r++;
  }
  return maxProfit
  ```
#### DP approach
- TC : O(n) SC : O(1)
  ```
  int maxProfit = 0;
  int minBuy = prices[0];
  for(int sell : prices) {
    maxProfit = Math.max(maxProfit, sell - minBuy)
    minBuy = Math.min(minBuy, sell);
  }
  return maxProfit
  ```
