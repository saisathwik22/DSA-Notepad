### Leetcode 26
#### Question : given array, first k elements of array should contain unique elements in order they were present, return k
- example : [0, 0, 1, 1, 1, 2, 2, 3, 3, 4]
- required array : [0, 1, 2, 3, 4, _, _, _, _, _]
- return k = 5

#### Optimal Appraoch - Two Pointer
- TC : O(N) SC : O(1)
- i = 0, j = 1, arr[], n
- if arr[i] == arr[j] then j++
- if arr[i] != arr[j] then first i++, then arr[i] = arr[j], then j++
  ```
  i = 0, j = 1
  while(j < n) {
    if (arr[i] != arr[j]) {
      i++;
      arr[i] = arr[j];
      // arr[i + 1] = arr[j] OR arr[++i] = arr[j]
    }
    j++; // when arr[i] == arr[j]
  }
  return i + 1; // index after last unique element
  ```


#### Using Set 
- TC : O(NlogN) SC : N
  ```
  HashSet temp
  for(i=0---->n) temp.add(arr[i])
  int i = 0
  for(num : temp) {
    arr[i] = num;
    i++;
  }
  return i;
  ```
