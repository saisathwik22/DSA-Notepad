### Leetcode 49
### Question : array of strings given, group the anagrams adjacent
 - s = [eat, tea, tan, ate, nat, bat]
 - output = [eat, tea, ate, tan, nat, bat]

#### Approach 1 : Sorting | TC - O(n * k * logk) SC - O(n * k)
- for each word, sort it, map the unsorted version to its sorted version
- word = string[i] | temp = sort(string[i]) | map[temp] = word
- [eat, tea, ate], sort the words, we get "aet"
- map[sorted string[i]] = unsorted string[i]
- now after mapping, it looks like this, [aet]--->[eat, tea, ate]
  ```
  Map<String, List<String>> map = new HashMap<>();
  for(string unsortedWord : s) {
    char[] charArray = unsortedWord.toCharArray();
    Arrays.sort(charArray);
    String sortedWord = new String(charArray);
    if(!map.contains(sortedWord)){
      map.put(sortedWord, new ArrayList<>());
    }
    map.get(sortedWord).add(unsortedWord); // map[sorted word] = unsorted word;
  }
  return new ArrayList<>(map.values());
  ```
