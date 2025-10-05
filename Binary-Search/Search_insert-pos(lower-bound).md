### Lower Bound - SEARCH Insert Position | Leetcode35 - Google | Facebook
- smallest index `i` such that `arr[i] >= x`
- TC : O(logN) SC : O(1)
  ```
  arr[], n, x
  low = 0, high = n-1, ans = n
  while(low <= high) {
    mid = low + (high-low)/2
    if(arr[mid] >= x) {
      // mid may be answer, look for smaller index on left
      ans = mid
      high = mid - 1
    } else low = mid + 1
  }
  return ans;
  ```
### Upper Bound
- smallest index `i` such that `arr[i] > x`
- same TC and SC
  ```
  ------ rest all same -------
  // mid may be answer, look for smaller index on left
  if(arr[mid] > x) {
    ans = mid
    high = mid - 1
  }
  ------ rest all same -------
  ```
