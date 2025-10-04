### Leetcode 225
#### Implement Stack operations pop, top, empty, push using Queue

## Queue operations
- `peek()` : just returns top element without removing it | `front`
- `poll()` : removes the top element and returns it | `pop`
- `.isEmpty()` : checks for empty in queue
- `.offer()` : inserts element at back of queue
- `.size()` : size of queue

#### Approach 1 - Use 2 Queues
- Use 2 Queues
- push 1, push 2
- push 1 | q2 = [1] & q1 = [] | q2 = [] & q1 = [1]
- push 2 | q2 = [2] & q1 = [1] | q2 = [2,1] & q1 = [] | q2 = [] & q1 = [2, 1]
  ```
  Queue<Integer> q1 = new LinkedList<>();
  Queue<Integer> q2 = new LinkedList<>();
  void push(x){
    q2.offer(x)
    while(!q1.isEmpty()){
      q2.offer(q1.poll())
    }
    Queue temp = q1
    q1 = q2
    q2 = temp
  }
  int pop() {
    return q1.poll()
  }
  int top() {
    return q1.peek()
  }
  bool empty() {
    return q1.isEmpty()
  }
  ```
#### Approach 2 - Use only 1 Queue
- Only difference in code is for void push() function, rest all same as above
  ```
  Queue q;
  void push(x){
    q.offer(x);
    n = q.size();
    for(i = 0 ------> n-1) {
      q.offer(q.poll())
    }
  }
  .
  .
  .
  rest all pop(), top(), empty() same as above code
  ```
