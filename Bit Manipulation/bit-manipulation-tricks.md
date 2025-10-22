### Bit Manipulation Techniques and Operations

#### AND (&)
- both bits are 1, ans is 1
  ```
  0 & 0 = 0
  1 & 1 = 1
  0 & 1 = 0
  1 & 0 = 0
  ```
#### OR (|)
- any one bit is 1, then ans is 1
  ```
  0 | 0 = 0
  1 | 1 = 1
  1 | 0 = 1
  0 | 1 = 1
  ```
#### XOR (^)
- both bits different, ans is 1
  ```
  0 ^ 0 = 0
  1 ^ 1 = 0
  0 ^ 1 = 1
  1 ^ 0 = 1
  ```
#### NOT (~)
- ~0 = 1 || ~1 = 0

#### Left Shift (<<) | Right Shift (>>)
- 1 left shift, multiply by 2
- 1 rigth shift, divide by 2
- binary(5) : 0101
- binary(10) : 1010
- 5 << 1 : 1010 : binary of 10
- 10 >> 1 : 0101 : binary of 5
  ```
  x >> n => divide x by 2 power n
  x << n => multiply x by 2 power n
  ```

#### Check if number is EVEN/ODD
- `x & 1 = 1` x is ODD
- `x & 1 = 0` x is EVEN
- bitwise operators are faster than multiply and divide

#### Check if number is power of 2
- `x & (x-1) = 0` x is power of 2
- `x & (x-1) > 0` x is not power of 2
- but when x = 0, it still gives 0, but 0 is not power of 2
- so to handle this edge case use below formula
- `x && !(x & (x-1))`

#### Swapping of two number x and y
- x = x ^ y
- y = x ^ y
- x = x ^ y

#### Tricks
- `x & 0 = 0`
- `x & 1 = last bit of x`
- `x ^ x = 0`
- `x ^ 0 = x`

#### Leetcode 136
- in array, all number appear twice, except for one, find it
- `a ^ b ^ c ^ b ^ a = c`
- TC : O(n) SC : O(1)
  ```
  ans = 0;
  for(int x : nums) {
    ans = ans ^ x;
  }
  return ans;
  ```
