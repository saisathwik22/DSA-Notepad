### Leetcode 953 - FB, Uber, Linkedin, Apple, Amazon, Walmart, DE Shaw, Bloomberg
#### Question:
- order:[....] given which depicts order of alphabets according to alien dictionary
- words:[_,_,...] given which contains different words
- check whether words follow the alien dictionary order or not, if not false, if yes true

#### String Approach:
- Take `Map<Character, Integer> mp = new HashMap<>()` to hash the alphabets in `order` with their indices.
- iterate through words[ word1, word2, word3, .....]
- start with word1 and word2, compare alphabets, if equal, move to next alphabets
- if not equal, compare their indices from hashmap, if they dont follow alien dictionary order, false
- TC : O(n), SC: O(n)
  ```
  for (i=0 ----> words.length-1) {
    for(j=0 -----> words[i].length()) {
      if j >= words[i+1].length(), then return FALSE
      if(words[i].charAt(j) != words[i+1].charAt(j)) {
        currLetter = mp.get(words[i].charAt(j))
        nextLetter = mp.get(words[i+1].charAt(j))
        if nextLetter < currLetter, then return FALSE
        else break;
      }
    }
  }
  return TRUE
  ``` 
