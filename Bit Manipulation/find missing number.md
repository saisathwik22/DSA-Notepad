### Leetcode 268
- given arr[] contains n distinct integers in range [0,n]
- find missing number from the given arr[]

#### Approach - XOR
- `a^a = 0` and `a^0 = a`
- XOR([0,n]) ^ XOR(arr[] elements) gives us the missing element
- TC : O(n) SC : O(1)
  ```
  xor = 0
  for(i = 0 to <= n) xor ^= i;
  for(num : arr) xor ^= num
  return xor;
  ```
#### Approach - Summation
- TC : O(n) SC : O(1)
- sum([0....n]), sum(arr elements), difference of both
  ```
  rangeSum = 0, arrSum = 0
  for(i = 0 to <= n) rangeSum += i
  for(num : arr) arrSum += num
  return rangeSum - arrSum;
  ```
#### Approach - Binary Search
- TC : O(n log n) SC: O(1)

  ```
  Arrays.sort(arr)
  l = 0, r = n - 1, mid = n
  while(l <= r) {
    mid = l + (r-l)/2;
    if arr[mid] > mid, then result = mid and r = mid - 1
    else l = mid + 1
  }
  return result;
  ```
