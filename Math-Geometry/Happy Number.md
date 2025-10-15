### Leetcode 202
#### Question
- given number n, return true if its happy else false
- a number n is `happy`:
    - when you repeatedly replace it by its sum of squares of its digits
    - if at a point the process leads to 1, then n is happy
    - if it doesnot reach 1 and stays in endless loop, its not happy
- Example
  ```
  n = 19 | Output = true
  1 Square + 9 Square = 81 | n = 82
  8 Square + 2 Square = 68 | n = 68
  6 Square + 8 Square = 100 | n = 100
  1 Square + 0 Square + 0 Square = 1 | return TRUE
  ```

#### Approach - Fast And Slow Pointers - TC : O(logN)
- use getNext() function which gives sum of square of digits of n
- place slow ptr on n, and fast ptr on getNext(n)
- perform slow = getNext(slow) and fast = getNext(getNext(fast)) till slow != fast and fast != 1
  ```
  int mainFunc(int n) {
    int slow = n;
    int fast = getNext(n)

    while(fast != 1 && slow != fast) {
      slow = getNext(slow); // slow++;
      fast = getNext(getNext(fast)); // fast += 2
    }
    return fast == 1;
  }
  int getNext(int n) {
    int total = 0;
    while(n > 0) {
      int digit = n % 10;
      total += (digit*digit)
      n = n / 10;
    }
    return total;
  }
  ```

#### Dry Run for n = 2;
- slow = 2, fast = getNext(2) = 4
- slow = getNext(2) = 4, fast = getNext(getNext(4)) = getNext(16) = 37
- slow = getNext(4) = 16, fast = getNext(getNext(37)) = 89
- slow = getNext(16) = 37, fast = getNext(getNext(89)) = 42
- slow = getNext(37) = 58, fast = getNext(getNext(42)) = 4
- slow = getNext(58) = 89, fast = getNext(getNext(4)) = 37
- slow = getNext(89) = 145, fast = getNext(getNext(37)) = 89
- slow = getNext(145) = 42, fast = getNext(getNext(89)) = 42
- *slow and fast pointer meet at 42*, So output is FALSE
- `NOTE` : for a number to be happy, slow will never be equal to fast, fast hits 1, TRUE

#### Approach - HashSet
- use function getNext(n) to obtain sum of squares of digits
- take a HashSet `Set<Integer> visit = new HashSet<>()` to store the numbers obtained by doing getNext(n)
  ```
  while(!visit.contains(n)) {
    visit.add(n)
    n = getNext(n)
    if n==1, then return true
  }
  return false;
  ```
