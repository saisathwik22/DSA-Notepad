### Leetcode 167 - Amazon
- given array sorted in ascending order, find two i and j where arr[i] + arr[j] == target
- once you find those indices, return {i+1,j+1}
- TC : O(n) SC : O(1)
  ```
  arr[], n
  int i = 0, j = n - 1
  while(i <= j) {
    if arr[i] + arr[j] == target {
      return new int[]{i + 1, j + 1}
    }
    else if arr[i] + arr[j] > target, then j--
    else if arr[i] + arr[j] < target, then i++
  }
  return new int[]{}
  ```
