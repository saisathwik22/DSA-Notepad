### Leetcode 18 - META
- given nums[], find nums[i] + nums[j] + nums[p] + nums[q] == target, where i != j != p != q


#### Brute Force
- TC : O(n power 4) SC : O(2 * quadraplets)
- use hash set to avoid duplicate quadraplets
- when target sum achieved, sort the quadraplets list before adding to hash set
  ```
  Set<Integer> st = new HashSet<>()
  for(i = 0 to n) {
    for(j = i + 1 to n) {
      for(p = j + 1 to n) {
        for(q = p + 1 to n) {
          long sum = (long) (nums[i] + nums[j] + nums[p] + nums[q])
          if(sum == target) {
            List temp = Arrays.asList(nums[i],nums[j],nums[p],nums[q])
            Collections.sort(temp)
            st.add(temp)
          }
        }
      }
    }
  }
  List<List<Integer>> ans = new ArrayList<>(st)
  return ans;
  ```

#### Better Approach
- 3 loops
- TC : O(N*N*N * logM) M = set quantity
- SC : O(2 * quadraplets) + O(N)
- we have a + b + c + d == target
- instead of q loop, use d = target-a-b-c and check whether it exists in hash set
- if exists, store quadraplet in temp list and sort before adding to set
- by default keep adding nums[p] into hash set in k loop

  ```
  Set st;
  for(i = 0 to n) {
    for(j = i + 1 to n) {
      Set<Long> hash = new HashSet<>()
      for(k = j + 1 to n) {
        long sum = nums[i] + nums[j] + nums[k]
        long fourth = target - sum
        if(hash.contains(fourth)) {
          List temp = Arrays.asList(nums[i],nums[j],nums[k],fourth)
          temp.sort(Integer::compareTo)
          st.add(temp)
        }
        hash.add((long)nums[k])
      }
    }
  }
  List<List<Integer>> ans = new ArrayList<>(st)
  return ans;
  ```

#### Optimal Approach
- sort the array
- don't use set to avoid duplicates
- start i loop, if i and i-1 have same elements, then skip it, continue
- start j loop, if j and j-1 have same elements, then skip it, continue
- we got positions of i and j fixed, now process remaining array i.e [j+1......n-1]
- since array is sorted, we can apply `TWO SUM II` approach between j+1 and n-1 to find p and q indices
- since array is sorted, place p on j + 1 and q on n-1
- when sum < tg, then p++ || when sum > tg, then q--
- when sum == tg, after adding quadraplets to list, check for duplicates with p and q
- if p and p - 1 have same elements, then p++
- if q and q + 1 have same elements, then q--

  ```
    Arrays.sort(nums)
    List of List ans = new ArrayList<>()
  for(i = 0 -------> n) {
    if(i > 0 && nums[i] == nums[i-1]) continue
    for(j = i + 1 -------> n) {
      if(j > i+1 && nums[j] == nums[j-1]) continue
      int p = j + 1, q = n - 1
      while(p < q) {
        long sum = (long)(nums[i] + nums[j] + nums[p] + nums[q])
        if(sum == target) {
          ans.add(Arrays.asList(nums[i],nums[j],nums[p],nums[q])
          p++; q--
          while(p < q && nums[p] == nums[p-1]) p++
          while(p < q && nums[q] == nums[q+1]) q--
        }
        else if sum < target, then p++
        else if sum > target, then q--
      }
    }
  }
}
  ```
