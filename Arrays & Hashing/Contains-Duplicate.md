## Leetcode 217

### Question : Given array, return true if an element occurs more than once
#### Approach 1 : TC - O(n*n) SC - O(1)
```
for(i=0; i<arr.length; i++) {
  for(j=i+1; j<arr.length; i++) {
    if(arr[i] == arr[j]) return true;
  }
}
return false;
```
#### Approach 2 : Sorting | TC - O(nlogn) SC - O(1)
```
Arrays.sort(arr);
for(i = 1; i < n; i++) {
  if(arr[i] == arr[i - 1]) return true;
}
return false;
```
#### Approach 3 : Hash SET | TC - O(n) SC - O(n)
```
Set<Integer> seen = new HashSet<>();
for(int x : arr) {
  if(seen.contains(x)) return true;
}
return false;
```
#### Approach 4 : Hash SET length | TC - O(n) SC - O(n)
```
return Arrays.stream(arr).distinct().count() < arr.length;
```
