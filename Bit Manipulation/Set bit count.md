### Leetcode 191
- Count number of set bits(1 bits) in binary representation of integer n
- example : n = 13 (1101) | output : 3

#### Method 1 : Brian Kernighan's Algorithm
- each time you do `n = n & (n-1)` , it removes rightmost set bit of n
- so number of times you can do this before n, is number of set bits
- TC : O(number of set bits) SC : O(1)
  ```
  int count = 0;
  while(n != 0) {
    n = n & (n - 1)
    count++;
  }
  return count;
  ```
##### Dry run for n = 13 (1101)
- n = 1101 & 1100 is 1100 | count = 1
- n = 1100 & 1011 is 1000 | count = 2
- n = 1000 & 0111 is 0000 | count = 3

#### Method 2 : Bit by Bit check
- TC : O(log N)
- loop through all bits, and count how many are set
  ```
  count = 0;
  while(n != 0) {
    count += (n&1)
    n >>= 1; // right shift // n = n/2
  }
  return count;
  ```

#### Method 3 : Built In JAVA
`count = Integer.bitCount(n)`

#### Unsigned Integer
- when n is large or negative
  ```
  count = 0
  while(n!=0){
    count += (n & 1)
    n >>>= 1
  }
  return count
  ```

### Leetcode 338 - AMAZON
- given n, return ans[] where ans[i] = number of set bits of i (0 <= i <= n)
- use solve(i) which returns number of set bits of i
- for solve() function use Brian Kernighan's algo or bit by bit check or java in built function
- loop from i=0 to i=n, ans[i] = solve(i)

#### Other Approach
```
ans[n + 1]
if n == 0, return ans;
ans[0] = 0
for i=1 to i=n {
  if i%2 == 0, ans[i] = ans[i/2] + 1
  else ans[i] = ans[i/2]
}
return ans
```
