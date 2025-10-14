### Leetcode 168 - Meta, Microsoft
#### Question
- given integer n, return corresponding title as it appears in excel sheet
  ```
  A -> 1
  B -> 2
  C -> 3
  .
  .
  Z -> 26
  AA -> 27
  AB -> 28
  ```

#### Approach - Same as digit extraction of numbers
- In numbers from 1 to 10 are unique in digit wise
- from number 11 repitition of digits occurs like 11, 12, 13.... etc
- to extract digits we modulo and divide the number using `10`
- Similarly alphabets from A to Z are numbered from 1 to 26
- from number 27 repitition occurs like AA -> 27, AB -> 28 etc
- so to extract corresponding character from digit, we use modulo and divide with `26`

  ```
  StringBuilder ans = new SB()
  while(n > 0) {
    n--;
    remain = n % 26;
    char ch = (char)(remain + 'A')
    ans.append(ch)
    n = n / 26
  }
  return ans.reverse().toString()
  ```

##### Dry Run
- example : n = 28, we need output as `AB`
- n--, gives n = 27
- remain = 27 % 26 = 1
- ch = (remain + 'A') = (1 + 'A') = B
- ans.append(ch) | ans = ['B']
- n = n/26 = 27/26 = 1
- n--, gives n = 0
- remain = 0 % 26 = 0
- ch = (remain + 'A') = (0 + 'A') = A
- ans.append(ch) | ans = ['B', 'A']
- n--, gives n < 0, Loop breaks out
- ans = ['B', 'A']
- ans.reverse() gives ['A','B']
- ans.toString() gives ans = "AB"
