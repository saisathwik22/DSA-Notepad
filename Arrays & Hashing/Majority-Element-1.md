### Leetcode 169
#### Question : given an array, return an arr[i] whose occurence > n/2, n = arr elements
##### Brute Force
- TC : O(n*n) SC : O(n)
  ```
  for(i = 0 ----> n) {
    count = 0
    for(j = 0 -----> n) {
      if(arr[i] == arr[j]) count++;
    }
    if count > n/2 ---> return arr[i];
  }
  return -1;
  ```
#### Better - HashMap
- store each element and its frequency in the hashmap
- re-iterate the map, if any element's occurence > n/2, then return that element
- TC : O(n + nlogn) SC : O(n)
  ```
  HashMap<Integer, Integer> map = new HashMap<>()
  for(i = 0 ---> n) {
    val = map.getOrDefault(arr[i], 0)
    map.put(arr[i], val + 1)
  }
  for(Map.Entry<Integer, Integer> it : map.entrySet()) {
    if it.getValue() > n/2 then return it.getKey()
  }
  return -1
  ```
### Optimal - Boyer Moore Voting Algorithm
- start with count = 1, major = arr[0]
- iterate over the array to obtain our element, then re-iterate to verify it
- TC : O(n + n) SC : O(1)
  ```
  count = 1, major = arr[0]
  for(i = 1 -------> n) {
    if(count == 0) {
      major = arr[i]
      count = 1
    }
    else if(arr[i] == major) count++;
    else count--;
  }
  int verifyCount = 0;
  for(i = 0 -----> n) {
    if(arr[i] == major) verifyCount++;
  }
  if verifyCount > n/2 then return major
  else return -1
  ```
