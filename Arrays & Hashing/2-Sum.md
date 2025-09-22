### Leetcode 1
### Question : Given array & int target, return {i, j} where arr[i] + arr[j] == target
#### Approach 1: TC - O(n*n) SC - O(1)
- arr[i] + arr[j] = target | target - arr[i] = arr[j]
- iterate over array, with two loops i and j.
- search for (target-arr[i]) in the array.
- if (target-arr[i]) is not found in range j to n-1, then i is not part of answer, i++;
  ```
  for(i = 0; i < n; i++) {
    for(int j = i + 1; j < n; j++) {
      if(arr[j] == target - arr[i]) return {i, j};
    }
  }
  ```
#### Approach 2 : Hash Map (One-Pass) | TC - O(n) SC - O(n)
- declare a map<int, int>
- iterate over arr, search for (target-arr[i]) in map
- if not found, put {arr[i], i} into the map, then i++
  ```
  HashMap<Integer, Integer> map = new HashMap<>();
  for(i = 0; i < n; i++) {
    int diff = target - arr[i];
    if(map.contains(diff)) {
      return new int[] {map.get(diff), i};
    }
    map.put(arr[i], i);
  }
  return new int[] {};
  ```

#### Other Approach : Hash Map (Two-Pass)
- Use Map and store the elements with its indices (arr[i], i)
- now iterate over array again
  ```
  for(i=0; i < n; i++){
    int diff = target - arr[i];
    if(map.contains(diff) && map.get(diff) != i) return {map.get(diff), i};
  }
  return {};
  ```
