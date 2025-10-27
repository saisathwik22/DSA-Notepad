### Add two integers a and b
- example : a = 5 (0101) b = 3 (0011)
- sum = a ^ b and carry = (a & b) << 1
- a = sum and b = carry
- TC : SC : O(1)
  ```
  while(b != 0) {
    carry = (a & b) << 1
    a = a ^ b
    b = carry
  }
  return a
  ```
### Subtract two integers a and b
- TC : SC : O(1)
- borrow = (~a) & b
  ```
  while(b != 0) {
    borrow = (~a) & b
    a = a ^ b
    b = borrow << 1
  }
  return a
  ```
### Reverse integer x
- example : x = 123 output = 321
- before updation to reverse integer, check for overflows
- TC : O(log base10 x) SC : O(1)
  ```
  ans = 0
  while(x != 0) {
    digit = x % 10
    x /= 10
    if(ans > Integer.MAX_VALUE/10 || (ans == Integer.MAX_VALUE/10 && digit > 7)) return 0
    if(ans < Integer.MIN_VALUE/10 || (ans == Integer.MIN_VALUE/10 && digit < -8)) return 0
    ans = ans * 10 + digit
  }
  return ans
  ```
