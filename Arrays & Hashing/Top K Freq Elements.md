### Leetcode 347 - Amazon, Accolite
- given arr[] and int k, find k most frequent elements
- arr[] = [1,1,1,2,3,3] k = 2
- output is [1,3]


### Bucket Sort - TC : O(n)
- initialize bucket[][] array of size n+1
- i represents the frequency
- bucket[i] = {_,_,...} represent elements which have frequency i
- store elements and their frequency in map as usual
- then iterate over bucket array and store the elements in their corresponding frequency index
- initialize new result[] array of size k
- back-iterate over bucket array and add elements to result array
- make sure size of result array is == k
  ```
  Map<Integer, Integer> mp = new HashMap<>()
  for(int x : nums) {
    mp.put(x, mp.getOrDefault(x, 0) + 1)
  }
  List<Integer>[] bucket = new List[n + 1]
  for(Map.Entry<Integer, Integer> entry : mp.entrySet()) {
    int element = entry.getKey()
    int freq = entry.getValue()
    bucket[freq].add(element)
  }
  int[] ans = new int[k]
  int idx = 0;
  for(i = n ; i >= 0 && idx < k ; i-- ) {
    if(!bucket[i].isEmpty()) {
      for(int val : bucket[i]) {
        ans[idx] = val;
        idx++;
        if idx == k, break;
      }
    }
  }
  return ans;
  ```

## Min Heap Declaration in JAVA to store pair of elements
```PriorityQueue<int[]> minheap = new PriorityQueue<>((a,b) -> a[0] - b[0])```

### Min Heap Approach
- use map to store <frequency of num, num>
- make sure heap stores only k elements
- delete min frequency element when heap size > k
- for faster deletion, we need the smallest freq pair to be on top
- so we can delete it in log(size)
- so, `MIN HEAP` sorts pairs in ascending order of frequency
- TC : O(n * log(n-k))
  ```
  Map<Integer, Integer> mp = new HashMap<>()
  for(int x : arr) {
    mp.put(x, mp.getOrDefault(x, 0) + 1) // mp[x]++
  }
  Declare min heap
  for(Map.Entry<Integer, Integer> entry : mp.entrySet()) {
    int num = entry.getKey(), freq = entry.getValue()
    minHeap.offer(new int[]{freq, num})
    if (minHeap.size() > k) minHeap.poll()
  }
  int[] ans = new int[k]
  int i = 0;
  while(!minHeap.isEmpty()) {
    ans[i] = pq.poll()[1]
    i++
  }
  return ans;
  ``` 
