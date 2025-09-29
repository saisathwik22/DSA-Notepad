### Leetcode 125
#### Question : Check if given strings are palindrome
`TWO Pointer`:
- TC : O(n) SC : O(1)
- Two pointers at start = 0, end = n - 1
- isAlphaNum(char) returns false if ch is space/special character, else return true
- start = 0, end = n - 1, if s[start] != s[end] then return false
  ```
  while(start < end) {
    if(!isAlphaNum(s.charAt(start)) start++; continue;
    if(!isAlphaNum(s.charAt(end)) end--; continue;
    if(Character.toLowerCase(s.charAt(start)) != Character.toLowerCase(s.charAt(end))) return false;
    start++; end--;
  }
  return true;

  boolean isAlphaNum(char ch) {
    if(ch >= '0' && ch <= '9' || Character.toLowerCase(ch) >= 'a' && Character.toLowerCase(ch) <= 'z') return true;
    return false;
  }
  ```
`Other Approach` :
  - reverse the string and check if equal or not
  - TC : O(n) SC : O(n)
