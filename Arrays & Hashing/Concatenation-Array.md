### Leetcode 1929
#### Question : given array nums of length n, build array ans of length 2n, where array nums is concatenated twice.
- input: nums = [1,2,1] n = 3
- output: ans = [1,2,1,1,2,1] 2*n = 6
- add array nums into ans once, then add it again
  ```
  int n = nums.length;
  ans[] of length 2*n
  // add nums from 0 to n-1 in ans
  for(i = 0; i < n; i++) {
    ans[i] = nums[i];
  }
  // add nums again from n to 2n-1 in ans
  for(i = 0; i < n; i++){
    ans[i + n] = nums[i];
  }
  ```
  `TC : O(n + n) SC : O(1)`
- why ans[i + n] ?
- nums = [1,2,1] n=3, indexes are 0,1,2
- ans = [1,2,1,1,2,1] n=6, indexes are 0,1,2,3,4,5
- i=0,1,2 are filled using (i=0--->n) ans[i]=nums[i];
- i=3,4,5 are filled using ans[i+n]=nums[i]
- because i=0 -> ans[0+3]=nums[0] | ans[3] = nuns[0]
- i=1 -> ans[1+3]=nums[1] | ans[4] = nums[1]
- i=2 -> ans[2+3]=nums[2] | ans[5] = nums[2]
