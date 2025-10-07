### Leetcode 1863
- given array of n unique elements
- find sum of xor of each subset of arr
- refer subset generation file for logic

#### Approach 1
- generate all subsets
- calculate sum of XOR of each subsets
- TC : O(n * 2^n)
- SC : O(n * 2^n)
  ```
  List<Integer> temp = new ArrayList<>()
  List<List<Integer>> ans = new ArrayList<>()
  solve(int[] arr, int i, temp, ans) {
    if(i >= arr.length) {
      ans.add(new ArrayList<>(temp))
      return;
    }
    temp.add(arr[i])
    solve(arr, i + 1, temp, ans)
    temp.remove(temp.size() - 1)
    solve(arr, i + 1, temp, ans)
  }
  subsetXORSum(int[] arr) {
    List of List ans, List temp
    solve(arr, 0, temp, ans)
    result = 0;
    for(List subset : ans) {
      xor = 0;
      for(int num : subset) xor = xor ^ num
      result += xor;
    }
    return result
  }
  ```
#### Approach 2 - Backtracking
- instead of storing subsets, calculate XOR while exploring the subsets
  ```
  {1,3} xor = 0 (i at 1)
  choose 1, xor = 0^1 ===> choose 3, xor = 0^1^3 | don't choose 3, xor = 0^1
  return with xor1 = 0^1^3 + 0^1
  don't choose 1, xor = 0 ===> choose 3, xor = 0^3 | don't choose 3, xor = 0
  return with xor2 = 0^3 + 0

  now return with xor = xor1 + xor2 
  ```
- TC : O(2powern) SC : O(n)
  ```
  int solve(int[] arr, int i, int xor) {
    if i == arr.length then return xor;
    int include = solve(arr, i + 1, xor^arr[i])
    int exclude = solve(arr, i + 1, xor)
    return include + exclude
  }
  ```
#### Approach 3 - Observing Patterns
- find OR of all elements of array
- append n-1 zeroes (0s) to right hand side of resultant OR
- TC : O(n) SC : O(1)
  ```
  result = 0;
  for(int num : arr) {
    result = result | num
  }
  return result << (n-1)
  ```
