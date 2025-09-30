### Leetcode 88
#### Question: two arrays nums1 (length = m + n) nums2 (length = n) | First "m" elements in nums1 denote to be merged, rest n elements are 0s
#### Merge both arrays in non-decreasing order and no extra space, final ans should be in nums1, thats why its length is given m+n
- TC : O((m + n)log(m + n)) SC : O(log(m + n))
- Arrays.sort(nums1) is used to sort in non-decreasing order
- This feature's time complexity is O((m + n)log(m + n))
- Arrays.sort uses Dual-Pivot Quick Sort which internally uses recursion stack of space complexity log(m+n)
  ```
  int i = m, j = 0
  while(i < (m + n) && j < n) {
    nums1[i] = nums2[j]
    i++; j++;
  }
  Arrays.sort(nums1)
  ```
#### No Extra Space - 3 Pointers
- TC : O(m + n) SC: O(1)
- i = m - 1; j = n - 1; last = m + n - 1;
  ```
  while(j >= 0) {
    if(i >= 0 && nums1[i] > nums2[j]) {
      nums1[last] = nums2[i]
      last--; i--;
    } else {
      nums1[last] = nums2[j]
      last--; j--;
    }
  }
  ```
