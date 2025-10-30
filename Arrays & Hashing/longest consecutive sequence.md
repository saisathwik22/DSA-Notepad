### Leetcode 128
- arr = [100, 101, 1, 4, 2, 102, 3]
- ans = 4 (1,2,3,4)

#### Brute Foce
- TC : O(n * n) SC : O(1)
  ```
  longest = 1
  for(i = 0 to n) {
    x = arr[i]
    cnt = 1
    while(linearSearch(arr, x + 1) == true) {
      x = x + 1
      cnt = cnt + 1
    }
    longest = max(longest, cnt)
  }
  return longest
  ```
#### Better Approach - Sort
- TC : O(n) SC : O(1)
- sort the array
- iterate over the array
- if curr element is next number of last small, then count++, update the lastSmall
- else if curr element is not equal to last small, or nowhere near its sequence, update last small and cnt
  ```
  sort(arr), longest = 1, cntCurr = 0, lastSmall = INT_MIN
  for(i = 0 to n) {
    if(arr[i] - 1 == lastSmall) {
      cntCurr += 1;
      lastSmall = arr[i]
    }
    else if(arr[i] != lastSmall) {
      cntCurr = 1
      lastSmall = arr[i]
    }
    longest = max(longest, cntCurr)
  }
  return longest
  ```
#### Optimal approach - Set
- TC : O(3n) SC : O(1)
- store elements in set (unique)
- iterate over set, for every element in set it
- if set contains it-1, then cnt = 1, x = it
- now using x, search for its x+1, x+2,... and eventually update the cnt

  ```
  if n == 0 then return 0
  ans = 1
  Set<Integer> s = new HashSet<>()
  for i=0 to n, s.add(arr[i])
  for(int it : s) {
    if !s.contains(it - 1) {
      cnt = 1, x = it
      while(s.contains(x + 1)) {
        x++;
        cnt++;
      }
      ans = max(ans, cnt)
    }
  }
  return ans
  ```
