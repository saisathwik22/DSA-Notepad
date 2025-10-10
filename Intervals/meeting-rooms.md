### Leetcode 252 - Amazon, Facebook, Google, Microsoft, Karat, Oracle, Adobe, VMware, eBay, Bloomberg
#### Question:
- int[][] intervals given = [ (0,30), (5,10), (15,20) ]
- (start time of meeting, end time of meeting)
- return true if a person can attend all meetings within given time intervals
- if any meeting's start time overlaps with any meeting's end time, return false;
- TC : O(nlogn) SC: O(1) | SORTING
  ```
  Arrays.sort(arr, (a,b)->Integer.compare(a[0],b[0]))
  for(i = 0 ------> arr.length() - 1) {
    if arr[i][1] > arr[i+1][0], then return false;
  }
  return true;
  ```
