### Leetcode 628
#### Question:
- operations[] = ["5", "2", "C", "D", "+"] given
- `int x` : record new score
- `+` : record new score that is sum of previous two scores
- `D` : record new score that is double of previous score
- `C` : remove previous score
- `output` : return sum of remaining elements in the record
#### Use STACK for record
- Use `Stack<Integer> st = new Stack<>()`; OR
- Use `Deque<Integer> st = new ArrayDeque()`;
- For modern usage, go with Deque, because Stack is old class, and is slow for some operations
  ```
  int func(String[] ops) {
    Use Deque for stack
    int n = ops.length;
    for(i = 0 -----> n) {
      String op = ops[i];
      if(op.equals("C")) {
        stack.pop()
      }
      else if(op.equals("D")) {
        int temp = stack.peek();
        stack.push(temp*2)
      }
      else if(op.equals("+")) {
        int temp = stack.peek()
        stack.pop()
        int newEle = temp + stack.peek()
        stack.push(temp)
        stack.push(newEle)
      }
      else {
        stack.push(Integer.parseInt(op))
      }
    }
    int ans = 0;
    while(!stack.isEmpty()) {
      ans += stack.peek()
      stack.pop()
    }
    return ans;
  }
  ```
