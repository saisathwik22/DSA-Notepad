### Leetcode 238 - LinkedIn, Amazon, Apple, Facebook, Microsoft

- given array[], return ans[] where ans[i] = product of all elements of array except array[i]
- ex : array = [1,2,3,4] ans = [24, 12, 8, 6]
- ex : array = [-1, 1, 0, -3, 3] ans = [0, 0, 9, 0, 0]
- don't use division operator

#### Approach - extra space O(n)
- TC : O(n) SC : O(n)
- use left[] to store product of elements from 0 to n-1
- use right[] to store product of elements from n-1 to 0
- left[0] = 1, right[n-1] = 1
 ```
 for(i = 1; i < n; i++) left[i] = left[i-1] * array[i-1]
 for(i = n-2; i >= 0; i--) right[i] = right[i + 1] * array[i + 1]
 for(i = 0 to n) array[i] = left[i] * right[i]
 ```
#### Approach - Constant Space O(1)
- TC : O(n) SC : O(1)
- use ans[] and store product of elements from 0 to n-1
- use right variable, right = 1
- back iterate from n-1 to 0 in ans[]
- ans[i] = ans[i] * right, then right = right * arr[i]
  ```
  ans[] = new int[n]
  ans[0] = 1;
  for(i = 1 ; i < n; i++) {
    ans[i] = ans[i - 1] * nums[i - 1]
  }
  right = 1;
  for(i = n - 1; i >= 0; i--) {
    ans[i] = ans[i] * right;
    right = right * nums[i]
  }
  return ans;
  ```
