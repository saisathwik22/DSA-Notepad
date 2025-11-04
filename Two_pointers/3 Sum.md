### Leetcode 15 - Amazon, Google, Facebook
- arr[] given of length n
- find arr[i] + arr[j] + arr[k] == 0, such i != j != k != i
- return {arr[i], arr[j], arr[k]}

#### Revisit 2 Sum
- given array, find i and j such that arr[i] + arr[j] == target
- when index are asked as answers, no sorting, as it will misplace the positions
- when elements are asked as answers, sorting can be done.
- [-1, 0, 0, 1, 2, 2, 7] target = 1
- ans = [ {-1, 2}, {-1, 2}, {0, 1}, {0, 1} ]
##### How to handle duplicate set of elements ?
- [-1, 0, 0, 1, 2, 2, 7] target = 1

- if arr[i] + arr[j] == target, check for duplicate
- condition 1 : if arr[i] == arr[i + 1], then i++ // 0 at 1 and 0 at 2
- condition 2 : if arr[j] == arr[j - 1], then j-- // 2 at 5 and 2 at 4
- if both conditions are false, then push the i and j pair to answer[]

#### 3 SUM
- n1 + n2 + n3 == 0
- n2 + n3 = -(n1)
- (-n1) is the target
- apply two sum on target = (-n1)
- find two indices n2 and n3 such that n2 + n3 = -(n1)
- fix an n1 in the array at i, apply two sum(arr, n1) from i+1 to end of array
  ```
  arr[], n
  if n < 3, then return new ArrayList<>()
  List<List<Integer>> ans = new ArrayList<>()
  Arrays.sort(arr)
  for(i = 0 to n - 2) {
    if i!=0 && arr[i] == arr[i+1], then continue
    int n1 = arr[i]
    int target = -n1
    twoSum(arr, i + 1, ans, target)
  }
  return ans;

  twoSum(arr[], int k, ans[], target) {
    i = k, j = n - 1;
    while(i < j) {
      if arr[i] + arr[j] > target, then j--
      else if arr[i] + arr[j] < target, then i++
      else {
        ans.add(Arrays.asList(-target. arr[i], arr[j]))
        while(i < j && arr[i] == arr[i + 1]) then i++
        while(i < j && arr[j] == arr[j - 1]) then j--
        i++, j--;
      }
    }
  }
  ```
