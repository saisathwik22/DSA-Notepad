### Leetcode 78 - Microsoft
- given an array of n unique elements, generate all possible unique subsets
- `Total number of subsets possible = 2 power n (2^n)`
- every index i has two options, either pick arr[i] or don't pick
- every subset needs at worst case n length of space
- total subsets 2^n
- So total `Space Complexity : O(n * 2^n)
- Every element has two options, pick or don't pick
- `Time Complexity : O(n * 2^n)`

  ```
  List<List<Integer>> ans = new ArrayList<>() // to store all subsets
  List<List<Integer>> subsets(int[] arr) {
    List<Integer> temp = new ArrayList<>() // to store each subset and push it later into ans
    solve(arr, 0, temp)
    return ans;
  }
  void solve(int[] arr, int i, List<Integer> temp) {
    if (i >= arr.length) {
      ans.add(new ArrayList<>(temp))
      return;
    }
    temp.add(arr[i])
    solve(arr, i + 1, temp)
    temp.remove(temp.size() - 1)
    solve(arr, i+1, temp)
  }
  
  ```
