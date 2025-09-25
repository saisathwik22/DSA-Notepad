### Leetcode 705 | *GOOGLE*
#### Question : design a hashset | add(key) | remove(key) | contains(key) functions
##### Boolean array approach
- 0 <= key <= 10 power 6
- use boolean array "data[]" of size (10power6 + 1), predefined to false
- data = new boolean[1000001] for every time MyHashSet() function is called
- when `.add(key) is called data[key] = true` | `.remove(key) is called data[key] = false` | `.contains(key) is called data[key] returned`
- TC : O(1) for each function call | SC : O(10power6 + 1)
##### Brute force approach - Array List
- initialise List<Integer> data;
- every time MyHashSet() is called, data = new ArrayList<>()
- when .add(key) is called, then `data.add(key)` when `!data.contains(key)`
- when .remove(key) is called, then `data.remove(Integer.valueOf(key))`
- when .contains(key) is called, `return data.contains(key)`
- TC : O(n) for each function call | SC : O(n)

##### Optimal approach  - Hashing

```
class MyHashSet {
    int M; // number of buckets 
    List<LinkedList<Integer>> buckets;
    public int getIndex(int key) {
        return (key % M);
    }
    public MyHashSet() {
        M = 15000;
        buckets = new ArrayList<>(M);
        for(int i = 0; i < M; i++) {
            buckets.add(new LinkedList<>());
        }
    }
    
    public void add(int key) {
        int index = getIndex(key);
        LinkedList<Integer> bucket = buckets.get(index);
        if(!bucket.contains(key)) {
            bucket.add(key);
        }
    }
    
    public void remove(int key) {
        int index = getIndex(key);
        LinkedList<Integer> bucket = buckets.get(index);
        bucket.removeFirstOccurrence(key);
    }
    
    public boolean contains(int key) {
        int index = getIndex(key);
        LinkedList<Integer> bucket = buckets.get(index);
        return bucket.contains(key);
    }
}
```


### Hashing : 
- hash array of size N, key given to be hashed
- hash[key % N] = key
- say, two keys key1 and key2 are to be hashed
- if (key1 % N == key2 % N) this is called `COLLISION` : Two keys into same bucket
- How to solve ? Seperate Chaining | Open Addressing (Linear Probing | Quadratic Probing)

#### Seperate Chaining:
- take hash array of format array<List<int>>
- two keys key1 and key2 are to be hashed
- if (key1 % N == key2 % N == index) then it's a Collision
- now hash[index].add(key1) | hash[index].add(key2)

#### Open Addressing | LinearProbing
- two keys key1, key2 to be hashed, hash array size N
- if hash[key % N] already occupied then hash[(key % N) + 1] = key
- slow for searching | TC is very high
#### Load Factor : Interview Specific
- `LOAD FACTOR (LR)` : N/M (N = elements that are put in array already | M = size of hash array)
- if LR > 0.75 ----> `ReHashing`
- if LR <= 0.75 ----> Fine
- when LR > 0.75, first create other hash array of size 2*M, then rehash
