### Leetcode 1071 - GOOGLE
#### Question
- given two string, return `Greatest Common Divisor` of the strings
- example:
- str1 = "ABABAB" str2 = "ABAB", output : "AB"
- take GCD of str1 length and str2 length
- then extract substring of gcd length from str1
  ```
  int gcd(int a, int b) {
    if b == 0: return a
    return gcd(b, a % b)
  }
  String func(str1, str2) {
    if !(str1 + str2).equals(str2 + str1) then return "";
    gcdLength = gcd(str1.length(), str2.length())
    return str1.substring(0, gcdLength)
  }
  ```
