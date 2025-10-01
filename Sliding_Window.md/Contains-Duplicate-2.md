### Leetcode 219
#### Question : given an array and k, return true, if there exists two distinct index i&j where arr[i]==arr[j] && abs(i-j)<=k

#### Sliding Window Approach - TC : O(n) | SC : O(min(n, k)) for sliding window
- initialize a set `Set<Integer> s = new HashSet<>()`
- declare i=0 and j=0 to outline the sliding window
- if `Math.abs(i-j) > k` means sliding window limits breached, need to SHRINK the window
- to SHRINK the window, remove arr[i] `set.remove(arr[i])` from set and i++
- if set contains arr[j] and abs(i-j) <= k then return true
- if set doesn't contain arr[j] push it into set `set.add(arr[j])` and j++
  ```
  while(j < n) {
    if(Math.abs(i - j) > k) {
      set.remove(arr[i])
      i++
    }
    if(set.contains(arr[j]) and abs(i-j) <= k) return true;
    set.add(arr[j]) because set donot contain arr[j]
    j++
  }
  return false;
  ```

#### Brute Force : TLE - TC : O(n*n)

#### HashMap Approach - TC : O(n) | SC : O(n)
- initialize a `Map<Integer, Integer> map = new HashMap<>()`
- iterate over the array
- check if map contains key arr[i] `map.containsKey(arr[i])`, if yes access that key's value(index) using `map.get(arr[i])`
- Calculate `abs(value of key - i) <= k` ?? if yes return true
- If not, then push the arr[i] and i into map `map.put(arr[i], i)`
  ```
  for(i = 0 ------------> n) {
    if(map.containsKey(arr[i]) && Math.abs(map.get(arr[i]) - i) <= k) return TRUE;
    else map.put(arr[i], i)
  }
  return FALSE;
  ```
