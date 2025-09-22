### Leetcode 242
#### Question : Given two strings s and t, return true if t is an anagram of s, else false;
`Anagram`: word/phrase formed by rearranging letters of another word/phrase using all original letters exactly once.
#### Approach 1 : Sorting | TC - O(nlogn) SC - O(1)
- sort both the strings s & t, check for their equality
- if(sort(s) == sort(t)) return true;

#### Approach 2 : Map | TC - O(n) SC - O(26)~O(1)
- int[] hash = new int[26]
- hash the string s | hash[s[i]] += 1;
- verify the occurences of hash with string t
  ```
  for(i = 0; i < n; i++) {
    if(hash[t[i]] > 0) {
      hash[t[i]] -= 1;
    }
  }
  ```
- now, re iterate over hash array
  ```
  for(i = 0; i < 26; i++){
    if(hash[i] != 0) return false;
  }
  return true;
  ```
- because if t is anagram of s, occurences of characters will be same for both strings
- while verifying with t, decrease the frequency of occurence of each character which is found in both s and t.
- so, if t is anagram of s, frequencies stored in hash will become 0, because we are decreasing them by 1
- so, after verification, even if any hash[i] != 0, that means that character's occurence was not equal in both strings s & t, hence not an anagram.

#### Follow Up:
- If string would contain Unicode (under ASCII 128) characters
- Space complexity would be O(128)
- declare hash array of size 128 / map<char, int>
  ```
  int[] count = new int[26]
  for(char ch : s.toCharArray()) count[ch - 'a'] += 1;
  for(char ch : t.toCharArray()) count[ch - 'a'] -= 1;
  // check if all element in array count are 0
  boolean allZeroes = Arrays.stream(count).allMath(element -> element == 0)
  return allZeroes;
  ```
