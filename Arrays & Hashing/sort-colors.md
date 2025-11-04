### Leetcode 75
``` Adobe, Amazon, Hike, Makemytrip, MAQ Software, Microsoft, Morgan Stanley, Ola Cabs, OYO Rooms,
    Paytm, Snapdeal, Qualcomm, Samsung, Walmart, Yatra.com, Flipkart
```
- given array of integers 0(red) 1(white) 2(blue) sort them

### Approach 1 - N*logN
- `Arrays.sort(nums)`


### Approach 2 - Count sort
- TC : O(n + n) SC : O(1)
  ```
  nums[], n
  count0 = 0, count1 = 0, count2 = 0
  for(int x : nums) {
    if x is 0, count0++
    if x is 1, count1++
    if x is 2, count2++
  }
  for(i = 0 to n) {
    if count0 > 0 {
      nums[i] = 0
      count0--;
    }
    else if count1 > 0 {
      nums[i] = 1
      count1--;
    }
    else if count2 > 0 {
      nums[i] = 2
      count2--;
    }
  }
  ```

### Approach 3 - i, j, k
- TC : O(n) SC : O(1)
- i denotes 0, j denotes 1, k denotes 2
- since 2 should be at the end of array, k = n - 1
- i and j start from 0
  ```
  i = 0, j = 0, k = n-1
  while(j <= k) {
    if nums[j] == 1, j++
    else if nums[j] == 2 {
      swap nums[j], nums[k]
    }
    else if nums[j] == 0 {
      swap nums[j], nums[i]
    }
  }
  ```
