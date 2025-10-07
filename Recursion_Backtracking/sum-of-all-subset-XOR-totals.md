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
