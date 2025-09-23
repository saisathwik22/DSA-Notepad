### Leetcode 14
#### Question : array of strings given, find LCP
- input : s=["flower", "flow", "flight"]
- output : ans = "fl"
`BETTER APPROACH`
  ```
  String prefix = strs[0];
  for (int i = 1; i < strs.length; i++) {
    int j = 0;
    while (j < Math.min(prefix.length(), strs[i].length())) {
        if (prefix.charAt(j) != strs[i].charAt(j)) break;
        j++;
    }
    prefix = prefix.substring(0, j);
  }
  return prefix;
  ```
- start with prefix = FLOWER
- iterate and compare each character of FLOWER and FLOW
- after iterations new prefix = FLOW
- now iterate and compare each character of FLOW and FLIGHT
- comparison fails at character O and I i.e., index 2
- now update prefix with substring(0, 1)
- TC : O(mn) SC : O(1)
- `substring(0, j)` : creates new string with characters from index 0 to j-1


  ```
  given String[] s
  StringBuilder ans = new StringBuilder()
  Arrays.sort(s)
  String first = s[0], last = s[s.length-1]
  for(i=0; i < min(first.length(), last.length()); i++) {
    if(first.charAt(i) != last.charAt(i)) return ans.toString();
    ans.append(first.charAt(i));
  }
  return ans.toString();
  ```
- TC : O(n * logmn) SC : O(n + m)
- s=[flower, flow, flight]
- sort the s --> [flight, flow, flower]
- now check the common prefix for flight and flower
