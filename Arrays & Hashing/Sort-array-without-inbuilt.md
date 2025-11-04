### Leetcode 912 - Goldman Sachs, Cisco, Microsoft
- given array, sort the array in ascending order without using inbuilt sort functions


### Counting Sort Approach
- given arr, n, find out max and min elements of arr
- use a map and store the frequency of elements of arr
- now using range [min ele, max ele] rewrite the array into sorted one.
- TC : O(n + range) SC : O(range)
  ```
  nums[], n
  minEle = Integer.MAX_VALUE
  maxEle = Integer.MIN_VALUE
  for(int x : nums) {
    minEle = Math.min(minEle, x)
    maxEle = Math.max(maxEle, x)
  }
  Map<Integer, Integer> mp = new HashMap<>()
  for(int x : nums) {
    mp.put(x, mp.getOrDefault(x, 0) + 1);
  }
  int i = 0
  for(int num = minEle ; num <= maxEle; num++ ) {
    int count = mp.getOrDefault(num, 0)
    while(count > 0) {
      nums[i] = num
      i++
      count--
    }  
  }
  return nums;
  ```
