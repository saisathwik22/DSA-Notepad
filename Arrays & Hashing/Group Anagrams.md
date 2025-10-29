### Leetcode 49 - Group Anagrams

``` Amazon, Google, Uber, Facebook, Bloomberg, Yahoo, Goldman Sachs, Microsoft, Apple, Walmart, Twilio, Affirm```

- given String[], group the anagrams together, return answer in any order
- input : String strs = ["eat", "tea", "tan", "ate", "nat", "bat"]
- output : [ ["bat"], ["nat", "tan"], ["ate", "eat", "tea"] ]

#### TC : O(n * klogk) SC : O(n * k) - Use MAP - Sorting
- use map `Map<String, List<String>> mp = new HashMap<>()`
- for every word in String[] strs, map stores <sorted word, {unsorted original words...}>
  ```
  Map storage
  word = "eat", sort it "aet", store it
  mp[sortedWord].add(word)

  final map after storing all words

  "aet" -> ["eat", "tea", "ate"]
  "abt" -> ["bat"]
  "ant" -> ["nat", "tan"]
  ```
- return map values at the end in form of ArrayList<>
  
  ```
  for(String word : strs) {
    char[] temp = word.toCharArray()
    Arrays.sort(temp);
    String sortedWord = new String(temp)

    mp.computeIfAbsent(sortedWord, k -> new ArrayList<>()).add(word)
  }
  return new ArrayList<>(mp.values())
  ```

#### Without Sorting - TC and SC : O(n * k)
- use array of size [26] to store frequency of alphabets
- for every word in strs, store the frequency in arr[]
- now iterate the array, and store the non zero freq letters in a string builder
- that string builder is your sorted version of your word, we did it without using sort function
- rest, store every word against its sorted version generated through array[26]

  ```
  String generate(String s){
    int[] count = new int[26]
    for ch in s.toCharArray() {
      count[ch - 'a']++
    }
    SB newS = new SB()
    for (i=0 to 26) {
      if count[i] > 0 {
        newS.append(String.valueOf((char)(i + 'a')).repeat(count[i]));
      }
    }
    return newS.toString()
  }
  main func(String[] strs) {
    Map<String, List<String>> mp = new HashMap<>()
    for String s : strs {
      String newS = generate(s)
      if(!mp.containsKey(newS)) {
        mp.put(newS, new ArrayList<>())
      }
      mp.get(newS).add(s)
    }
    return new ArrayList<>(mp.values())
  }
  ```
