### Leetcode 66 - Microsoft
#### Question:
- arr[] given which contains digits
- add 1 to the largest digit in the array and return new array after addition.
- example : arr = [1,2,3] num = 123, add +1, num = 124, arr=[1,2,4]
- example : arr = [9,9,9] num = 999, add +1, num = 1000, arr=[1,0,0,0]

  ```
  int[] digits, size n
  int carry = 1
  for(i = n-1 ; i >= 0 ; i--) {
    sum = digits[i] + carry
    digits[i] = sum % 10
    carry = sum % 10
  }
  if carry = 1 {
    int[] newDigits = int new[n + 1]
    newDigits[0] = 1
    return newDigits;
  }
  return digits;
  ```
