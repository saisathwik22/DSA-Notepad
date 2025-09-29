### Leetcode 680
#### Question : Given string, return true if string can be palindrome after deleting at-most 1 character from it | else return false;
- example : [r o t a t x o r]
- by deleting "x", string can be palindrome
- take two pointers left = 0 right = n - 1
- if s[left] == s[right] then left++ right--
- if s[left] != s[right] then either delete s[left] or delete s[right]
- delete s[left] means, check if substring(left+1, right) is palindrome or not
- delete s[right] means, check if sub string (left, right - 1) is palindrome or not
- TC : O(n) SC : O(1)
  ```
  mainFunc(String s) {
    while(left < right) {
      if(s.charAt(left) == s.charAt(right)) left++; right--;
      else {
        return isPalindrome(s, left + 1, right) || isPalindrome(s, left, right - 1)
      }
    }
  }
  isPalindrome(String s, int left, int right) {
    while(left < right) {
      if(s.charAt(left) == s.charAt(right)) left++; right--;
      else return false;
    }
  }
  ```
