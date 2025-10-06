### leetcode 1046 - GOOGLE
#### Question
- array stones[] given
- choose two stones x and y with heaviest weights and smash them
- if x == y, then two stones are destroyed
- if x != y, (x<=y) then x is destroyed, and y is replaced with (y-x)
- at end of game, at max one stone is left
- return wt of last stone, if no stones left, return 0

#### Max Heap Approach - TC : O(n * logn) SC : O(n)
- choose max heap, because we need to choose two heavy stones
- pop top two stones x and y
- y needs to be heavier stone so maxheap stores heavier stone at top
- if both unequal, push y-x into maxheap
- if equal leave it.
- repeat this game, till maxHeap size is greater than 1
  ```
  PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Collections.reverseOrder())
  for(int stone : stones) maxHeap.add(stone)
  while(maxHeap.size() > 1) {
    int y = maxHeap.poll()
    int x = maxHeap.poll()
    if(x != y) maxHeap.add(y - x)
  }
  if maxHeap.size() == 0, then return 0
  return maxHeap.peek() // one stone left over
  ```
