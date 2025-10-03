### Leetcode 20
#### Question : Given string only contains (){}[], determine if input string valid or not
String valid if:
- open brackets must be closed with same type of brackets
- open brackets must be close in correct order
- every close bracket should have a corresponding open bracket of same type
#### Examples
- "([])" TRUE
- "([)]" FALSE
- "()[]{}" TRUE

### Stack Approach 1:
- iterate over given string, input string s;
- if open bracket found, push it
- if closed bracket found and stack's top is same type of open bracket then pop the top
- if closed bracket found and stack's top is not same type of open bracket, then return false;
  ```
  Deque<Character> stack = new ArrayDeque<>()
  for(char ch : s.toCharArray()) {
    if(stack is empty OR ch is '(' OR '{' OR '[') {
      stack.push(ch)
      continue
    }
    if(ch is ")") {
      if stack.peek() is "(" then pop
      else FALSE
    }
    else if(ch is "}" ){
      if stack.peek() is "{" then pop
      else FALSE
    }
    else if(ch is "]" ) {
      if stack.peek() is "[" then pop
      else FALSE
    }
  }
  return stack.isEmpty()
  ```
#### Stack Approach 2:
- iterate over string
- if open bracket found, push closed bracket of same type to stack
- if closed bracket found, and it equals to top of stack, then pop it
- if closed bracket found, and its not equals to top of stack OR stack is empty then return FALSE
  ```
  Deque<Character> stack = new ArrayDeque<>();
  for(char ch : s) {
    if (ch is "(" OR "{" OR "[" ) then push ")" OR "}" OR "]" into stack
    if stack is empty OR stack.peek() != ch then return FALSE
    if ch == stack.peek() then stack.pop()
  }
  return TRUE
  ```
