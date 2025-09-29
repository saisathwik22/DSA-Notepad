### Leetcode 344
#### Question : Reverse String (in-place)
`TWO POINTERS` :
- char[] s given, n length;
- two pointers l = 0, r = n-1
- TC : O(n) SC : O(1)
  ```
  while(l < r){
    temp = s[l];
    s[l] = s[r];
    s[r] = temp;
    l++; r--;
  }
  ```
##### Additional Approaches
`In-Built JAVA feature`:
- TC : O(n) SC : O(1)
  ```
  List<Character> tempList = new ArrayList<>();
  for char c : s {
    tempList.add(c);
  }
  Collections.reverse(tempList);
  for(i = 0; i < n; i++) s[i] = tempList.get(i);
  ```
`Stack Approach`:
 - Use Stack and store all the characters of s in stack
 - last char of s will be stored on top of stack
 - now pop the top element and re-write into the given input s
 - TC : O(n) SC : O(n)

`Recursion Approach`:
 - TC : O(n) SC : O(n) (recursion call stack)
   ```
   reverseFunc(s, l, r) {
     if(l < r){
        reverse(s, l + 1, r - 1)
         swap s[l], s[r]
     }
   }
   reverseMain(s, n){
      reverseFunc(s, 0, n - 1)
   }
   ```

`Array Approach`:
  - TC : O(n) SC : O(n)
  - Initialise new char[] temp = new char[n]
  - iterate in input s from reverse order
  - while reverse iterating, store the characters in new array
  - then re-iterate the input s from front, and re-write the temp characters into input s
    ```
    for(i = n-1, j=0; i >= 0; i--, j++) {
      temp[j] = s[i]
    }
    for(i = 0 ----> n) {
      s[i] = temp[i];
    }
    ```
