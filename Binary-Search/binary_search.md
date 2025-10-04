### Leetcode 704 - Google | Microsoft | eBay | Cisco | OLA .... many more

## Binary Search - O(logn)
### Iterative 
```
func(arr, target) {
  n = arr.length;
  l = 0, r = n - 1, mid = 0;
  while(l <= r) {
    mid = l + (r-l)/2;
    if(arr[mid] == target) return mid;
    else if(arr[mid] < target) l = mid + 1;
    else if(arr[mid] > target) r = mid - 1;
  }
  return -1
}
```
### Recursive
```
func(arr, l, r, target) {
  if(l > r) return -1
  mid = l + (r-l)/2
  if(arr[mid] == target) return mid
  else if(arr[mid] < target) {
    return func(arr, mid + 1, r, target)
  }
  else if(arr[mid] > target) {
    return func(arr, l, mid - 1, target)
  }
}


return func(arr, 0, n-1, target)
```
