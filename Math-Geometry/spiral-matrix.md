### Leetcode 54
- ```Paytm | Zoho | Morgan Stanley | Accolite | Amazon | Microsoft | Snapdeal | DE Shaw | Oracle

#### Question: given an mxn matrix, return list[] which contains spiral iteration
- example:
  ```
  1 2 3
  4 5 6
  7 8 9

  output : list = [1,2,3,6,9,8,7,4,5]
  ```

#### Approach:
- initialize top = 0, down = m-1, left = 0, right = n-1
- dir = 0 means printing row left to row
- dir = 1 means printing col top to down
- dir = 2 means printing rown right to left
- dir = 3 means printing col down to top
- first print m[top][left to right] then top++
- then print m[top to down][right] then right--
- then print m[down][right to left] then down--
- then print m[down to top][left] then left++
- do this until top <= down and left <= right

  ```
  m = rows, n = cols
  top = 0, down = m - 1, right = n - 1, left = 0, dir = 0
  List<Integer> ans = new ArrayList<>();

  while(left <= right && top <= down) {
    if (dir == 0) {
      for(i = left; i <= right; i++) ans.add(m[top][i])
      top++
    }
    if(dir == 1) {
      for(i = top; i <= down; i++) ans.add(m[i][right])
      right--;
    }
    if(dir == 2) {
      for(i = right; i >= left; i--) ans.add(m[down][i])
      down--;
    }
    if(dir == 3) {
      for(i = down; i >= top; i--) ans.add(m[i][left])
      left++;
    }
    dir++;
    if(dir == 4) dir = 0;
  }
  return ans;
  ```
