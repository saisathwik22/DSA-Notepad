### Leetcode 190 - Amazon
- given 32 bit signed integer, reverse the bits
- for example (8 bits) : 00000101 (5)
- output : reversed -> 10100000 (160)

  ```
  result = 0;
  for(i = 0 to 32) {
    result <<= 1;
    result |= (n & 1)
    n >>>= 1
  }
  return result;
  ```
