### Floor
- largest number in array <= x
- example : arr = {3,4,4,7,8,10} | x = 5 | floor = 4
  ```
  while(l <= r) {
    mid = l + (r - l)/2
    if(arr[mid] <= x) {
      // search on right for larger number
      ans = arr[mid]
      l = mid + 1
    }
    else high = mid - 1
  }
  return ans
  ```
### Ceil
- smallest number in array >= x
- example : arr = {3,4,4,7,8,10} | x = 5 | ceil = 7
  ```
  --- rest all same -----
  if(arr[mid] >= x) {
    // search on left for smaller number
    ans = arr[mid]
    high = mid - 1
  }
  --- rest all same ---

TC: logN SC : O(1)
  ```
