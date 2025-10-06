### Leetcode703 - Amazon
#### Kth Largest element in a stream of elements, return kth largest element after addition of every new element
- TC : O(m * logK) SC : O(k)

```
PriorityQueue<Integer> minHeap;
int k;
kthLargest(int[] arr, int k){
  this.k = k;
  this.minHeap = new PriorityQueue<>()
  for(int num : arr) {
    minHeap.add(num)
    if(minHeap.size() > k) minHeap.poll()
  }
}
int add(int val) {
  minHeap.add(val)
  if minHeap.size() > k then minHeap.poll()
  return minHeap.peek()
}
```
