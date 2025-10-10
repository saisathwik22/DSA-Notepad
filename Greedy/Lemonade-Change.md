### Leetcode 860
#### Question:
- one lemonade price = $5
- customer pays in three bills = $5/$10/$20
- return false, if you can't give correct change to every customer, else true
- bills[i] = bill paid by ith customer

#### Approach - Instead of Using map, use 2 variables fiveNote and tenNote
- TC : O(n) SC : O(1)
```
int fiveNote = 0, tenNote = 0
for(int note : bills) {
  if note == 5, then fiveNote++;
  else if note == 10 {
    tenNote++;
    if fiveNote > 0 fiveNote--;
    else return false;
  }
  else if note == 20 {
    if fiveNote > 0 && tenNote > 0, then fiveNote-- and tenNote--;
    else if fiveNote >= 3, then fiveNote -= 3;
    else return false;
  }
}
return true;
```

#### Approach - Use Hashmap
- iterate in bills[] array
- use hashmap to store the bill/note frequency of $5, $10, $20
- for every note increase the freq in the map.
- now, if note $10, you need to give $5 back, check if map contains a $5 to give.
- now, if note $20, you need to give $15 back, so you need either 3 $5 notes OR 1 $10 note and 1 $5 note.
- if for any customer change is not available, return false;
- else return true
  ```
  Map<Integer, Integer> mp = new HashMap<>()
  for(int note : bills) {
    mp.put(note, mp.getOrDefault(note, 0) + 1) // mp[note]++;
    if(note == 10) {
      if(mp.getOrDefault(5, 0) >= 1) { // if mp[5] >= 1
        mp.put(5, mp.get(5) - 1); // mp[5]--;
      }
      else return false;
    }
    if(note == 20) {
      if(mp.getOrDefault(5, 0)>=1 && mp.getOrDefault(10, 0)>=1) { // if mp[5] >= 1 && mp[10] >= 1
        mp.put(5, mp.get(5) - 1); // mp[5]--;
        mp.put(10, mp.get(10) - 1); // mp[10]--;
      }
      else if(mp.getOrDefault(5, 0) >= 3 ){ // if mp[5] >= 3
        mp.put(5, mp.get(5) - 3); // mp[5] -= 3;
      }
      else return false;
    }
  }
  return true;
  ```
