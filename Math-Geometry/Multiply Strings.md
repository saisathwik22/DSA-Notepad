### Leetcode 43
- string a and string b given with numbers, multiply and return result in form of string
- example : a = "12" b = "13" output = "156"
- TC : O(m * n) SC : O(m + n)

  ```
  String a, String b given
  int m = a.length(), n = b.length()
  if a.equals("0") || b.equals("0"), then return "0"
  int[] ans = new int[m + n]
  for(i = m-1 to 0) {
    for(j = n-1 to 0) {
      digit1 = a.charAt(i) - '0'
      digit2 = b.charAt(j) - '0'
      temp = digit1 * digit2
      posLow = i + j + 1, posHigh = i + j
      sum = temp + ans[posLow]
      ans[posLow] = sum % 10
      ans[posHigh] += sum/10
    }
  }
  StringBuilder result = new SB()
  for(int x : ans) {
    if(!(result.length() == 0 && x == 0)) result.append(x)
  }
  return result.length() == 0 ? "0" : result.toString()
  ```
