### Leetcode 13


#### Approach - Hashmap
- Hash the characters to their numbers
- start with i=0, compare, if map[s[i]] < map[s[i + 1]] then sum - map[i]
- else sum + map[i]
- TC : O(n) Sc : O(7)
  ```
  Map<Character, Integer> mp = new HashMap<>();
  mp.put('I', 1); mp.put('V', 5); mp.put('X', 10); mp.put('L', 10);
  mp.put('C', 100); mp.put('D', 500); mp.put('M', 1000);

  for(i = 0; i < s.length(); i++) {
      if(i+1 < s.length() && mp.get(s.charAt(i)) < mp.get(s.charAt(i+1))) {
          sum -= mp.get(s.charAt(i))
      }
      else sum += mp.get(s.charAt(i))
  }
  return sum;
  ```

```
class Solution {
    public int romanToInt(String s) {
        int n = s.length();
        int sum = 0;
        int i = n - 1;
        while(i > 0) {
            char x = s.charAt(i);
            char y = s.charAt(i - 1);
            // IV or only V
            if(x == 'V') {
                if(y == 'I') {
                    sum += 4;
                    i -= 2;
                }
                else {
                    sum += 5;
                    i--;
                }
            }
            // IX or only X
            if(x == 'X') {
                if(y == 'I') {
                    sum += 9;
                    i -= 2;
                }
                else {
                    sum += 10;
                    i--;
                }
            }
            // XL or only L
            if(x == 'L') {
                if(y == 'X') {
                    sum += 40;
                    i -= 2;
                }
                else {
                    sum += 50;
                    i--;
                }
            }
            // XC or only C
            if(x == 'C') {
                if(y == 'X') {
                    sum += 90;
                    i -= 2;
                }
                else {
                    sum += 100;
                    i--;
                }
            }
            // CD or only D
            if(x == 'D') {
                if(y == 'C') {
                    sum += 400;
                    i -= 2;
                }
                else {
                    sum += 500;
                    i--;
                }
            }
            // CM or only M
            if(x == 'M') {
                if(y == 'C') {
                    sum += 900;
                    i -= 2;
                }
                else {
                    sum += 1000;
                    i--;
                }
            }
            // only I
            if(x == 'I') {
                sum += 1;
                i--;
            }
        }
        char temp = s.charAt(0);
        if(i == 0) {
            if(temp == 'I') sum += 1;
            else if(temp == 'V') sum += 5;
            else if(temp == 'X') sum += 10;
            else if(temp == 'L') sum += 50;
            else if(temp == 'C') sum += 100;
            else if(temp == 'D') sum += 500;
            else if(temp == 'M') sum += 1000;
        }
        return sum;
    }
}
```
