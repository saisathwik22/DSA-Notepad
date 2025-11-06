### Leetcode 229 - Amazon, Google

- for n/2 case, max 1 element can be major
- for n/3 case, max 2 element can be major
- for n/4 case, max 3 element can be major
- for n/k case, max k-1 element can be major

## Boyer Moore Voting Algorithm
- find all elements whose frequency > n/3 in array

```
count1 = 0, count2 = 0
major1 = Integer.MIN_VALUE, major2 = Integer.MIN_VALUE
for(i = 0 to n) {
  if count1 == 0 && major2 != arr[i] {
    count1 = 1; major1 = arr[i]
  }
  else if (count2 == 0 && major1 != arr[i]) {
    count2 = 1; major2 = arr[i]
  }
  else if (arr[i] == major1) count1++;
  else if (arr[i] == major2) count2++;
  else if (arr[i] != major1 and major2 && count1 and count2 != 0){
    count1--;
    count2--;
  }
}
// verify
freq1 = 0, freq2 = 0
int leastOcc = (int)(n/3) + 1
for(i = 0 to n) {
  if arr[i] == major1, then freq1++
  else if arr[i] == major2, then freq2++
}
List ans ;
if freq1 >= leastOcc, then ans.add(major1)
if freq2 >= leastOcc, then ans.add(major2)
return ans;
```
