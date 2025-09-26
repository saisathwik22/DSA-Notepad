### Leetcode 706 - GOOGLE | META | Similar to Leetcode 705 (Hashset)

#### Approach 1 : 
- Use vector of size 10power6 + 1
  ```
  int[] arr;
  int size;
  MyHashMap() {
    size = 1000001;
    arr = new int[size];
    Arrays.fill(arr, -1)
  }
  put(key, value) { // O(1)
    arr[key] = value
  }
  get(key) { return arr[key] } // O(1)
  remove(key) { arr[key] = -1 } // O(1)
  ```
#### Approach 2 : 
```
class MyHashMap {
    private List<Pair>[] bucket;
    private int size = 10000;
    static class Pair {
        int key;
        int value;
        Pair(int key, int value) {
            this.key = key;
            this.value = value;
        }
    }
    public MyHashMap() {
        bucket = new LinkedList[size];
        for(int i = 0; i < size; i++) {
            bucket[i] = new LinkedList<>();
        }
    }
    
    public void put(int key, int value) {
        int bucketNum = key % size;
        List<Pair> chain = bucket[bucketNum];
        for(Pair pair : chain) {
            if(pair.key == key) {
                pair.value = value;
                return;
            }
        }
        chain.add(new Pair(key, value));
    }
    
    public int get(int key) {
        int bucketNum = key % size;
        List<Pair> chain = bucket[bucketNum];
        for(Pair pair : chain) {
            if(pair.key == key) {
                return pair.value;
            }
        }
        return -1;
    }
    
    public void remove(int key) {
        int bucketNum = key%size;
        List<Pair> chain = bucket[bucketNum];
        for(Pair pair : chain) {
            if(pair.key == key) {
                chain.remove(pair);
                return;
            }
        }
    }
}
```
