### Decimal to Binary conversion
- example : decimal = 13 | binary = 1101
- 13 % 2 = 1, 13/2 = 6, [1]
- 6 % 2 = 0, 6/2 = 3, [1,0]
- 3 % 2 = 1, 3 / 2 = 1, [1,0,1]
- 1 % 2 = 1, 1/2 = 0, [1,0,1,1]
- TC : O(log N) SC : O(log N)
  ```
  string function(int x) {
    string ans = ""; // empty string
    while(x != 1) {
      if x % 2 == 1, then ans += '1'
      else, then ans += '0'
    }
    reverse(ans)
    return ans;
  }
  ```

### Binary to Decimal Conversion
- example : binary = 1101 | decimal = 13
- backtraverse the binary string
- 1 * (2power0) + 0 * (2power1) + 1 * (2power2) + 1 * (2power3) = 13
- TC : O(n) SC : O(1)
  ```
  int function(string s) {
    int n = s.length, power = 1, num = 0
    for(i = n-1 -----> 0) {
      if s[i] == '1', then num = num + power
      power = power * 2
    }
    return num
  } 
  ```
