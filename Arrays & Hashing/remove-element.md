### Leetcode 27
### Same as Move Zeroes to end question - Leetcode283
#### Question : array and int val given, move elements 'val' to end 
- input : [0,1,2,2,3,0,4,2] | Val = 2
- output : [0,1,3,0,4,_,_,_] | return number of elements which are not equal to val

##### Approach 1:
- store elements != val in a temp List
- then iterate the nums array, replace the elements with elements of temp List(!= val)
- return temp.size();
- make sure the starting elements are not equal to val in the input array
  ```
  array nums;
  List temp;
  for(i=0---->n){
    if(nums[i] != val) temp.add(nums[i]);
  }
  for(i=0----->temp.size()){
    nums[i] = temp.get(i);
  }
  return temp.size();
  ```
- TC : O(n) SC : O(n)

##### Approach 2 : 2Pointer
- iterate over the array and place j pointer on first occurence of 'val'
- re-iterate over the array and make the changes
  ```
  for(i = j+1---->n){
    if(nums[i] != val){
      swap nums[i], nums[j];
      j += 1;
    }
  }
  ```
- return the count of elements which are not equal to val.
- TC : O(n) SC : O(1)
