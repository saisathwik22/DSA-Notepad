### Leetcode 560
- given arr[], return number of subarrays whose sum is k

#### Brute Force :
- find all subarrays possible
- find sum and check == target ?
- every start point can have different end points
  ```
  ans = 0;
  for(s = 0 to n) {
    for(e = s to n) {
      sum = 0
      for(i = s to e) {
        sum += arr[i]
      }
      if sum == target, ans++
    }
  }
  return ans;
  ```

#### Optimal Approach
- iterate over array, for every i, find cumulative sum till index i
- check whether (cumulativeSum-k) exists in map or not
- if exists, then ans += mp[cumulativeSum - k]
- then update the count of cumulative sum in map
```
when (cumulative sum - k) is found in map,
it means k was added to some value to reach cumulative sum
this means subarray with sum k exists, so update result with mp[cumulativeSum-k], update mp[cumulativeSum]
```
- TC : O(n) Sc : O(n)

  ```
  ans = 0, sum = 0
  Map<Integer, Integer> mp = new HashMap<>()
  mp.put(0, 1)
  for(i = 0 to n) {
    sum += arr[i]
    if(mp.containsKey(sum - k)) ans += mp.get(sum - k)
    mp.put(sum, mp.getOrDefault(sum, 0) + 1)
  }
  return ans;
  ```
