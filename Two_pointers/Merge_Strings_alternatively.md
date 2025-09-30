### Leetcode 1768
#### Question : Given two string word1 and word2, merge them by adding letters alternatively, starting with word1. if any string length is longer than the other, add the remaining elements at last.
- example : word1 = "abc" word2 = "pqrst"
- ans = [a, p, b, q, c, r, s, t]
- TC : O(n + m) SC : O(n + m)
- int i = 0, j = 0;
  ```
  StringBuilder ans = new StringBuilder();
  while(i < n && j < m) {
    ans.append(word1.charAt(i))
    ans.append(word2.charAt(j))
    i++; j++;
  }
  while(i < n) {
    ans.append(word1.charAt(i))
    i++;
  }
  while(j < m) {
    ans.append(word2.charAt(j))
    j++;
  }
  return ans.toString();
  ```
              
