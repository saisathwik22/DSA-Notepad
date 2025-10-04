### Leetcode 232 - Meta | Google | Amazon | Apple | Microsoft
#### Implement Queue Operations using Stack

#### Using 2 Stacks to implement Queue
- Initialize 2 Stacks `Stack<Integer> input, output`
  ```
  Stack<Integer> input;
  Stack<Integer> output;
  int peekEl;
  MyQueue() {
    input = new Stack<>()
    output = new Stack<>()
    peekEl = -1
  }
  void push(int x) { // O(1)
    if(input.isEmpty()) peekEl = x;
    input.push(x)
  }
  int pop() { // amortized O(1)
    if(output.isEmpty()) {
      while(!input.isEmpty()) output.push(input.pop())
    }
    int val = output.pop()
    return val;
  }
  int peek() { // O(1)
    if(output.isEmpty()) {
      return peekEl
    }
  }
  bool empty() { // O(1)
    return input.isEmpty() && output.isEmpty()
  }
  ```
