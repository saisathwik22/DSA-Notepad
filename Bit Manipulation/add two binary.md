### Leetcode 67 - AMAZON
- given two binary strings a and b, add them and return resultant binary string
- a = "1010" b = "1011", ans = 10101
- TC : O(max(len a, len b)) SC : same
  ```
  StringBuilder ans = new SB()
  i = a.length() - 1, j = b.length() - 1, carry = 0
  while(i >= 0 || j >= 0 || carry == 1) {
    int sum = carry
    if i>=0, then sum += a.charAt(i--) - '0'
    if j>=0, then sum += b.charAt(j--) - '0'
    ans.append(sum % 2)
    carry = sum / 2
  }
  return ans.reverse().toString()
  ```
