### Leetcode 48 - Rotate Image
```Amazon | Microsft | Morgan Stanley | Infosys | Google | Salesforce | Samsung | Zoho | Paytm | DE Shaw | Flipkart | Qualcomm | Snapdeal```
#### Inplace rotation
#### Rotate given nxn matrix by 90 degrees in clockwise direction 
- `Clockwise 90 degree` : 1. transpose of given matrix | 2. reverse each row (left to right)
- TC : O(n * n) SC : O(1)
  ```
  // transpose
  for(i = 0 ---> n) {
    for(j = i ----> n) {
      temp = arr[i][j]
      arr[i][j] = arr[j][i]
      arr[j][i] = temp
    }
  }
  // reverse each row
  for(i = 0 -----> n) {
    left = 0, right = n - 1
    while(left < right){
      swap arr[i][left] and arr[i][right]
      left++; right--;
    }
  }
  ```
#### AntiClockwise rotation by 90 degree
- TC : O(n * n) SC : O(1)
- 1. transpose of matrix | 2. reverse each coloumn (top to bottom)
  ```
  // tranpose
  for(i = 0 to n) {
    for(j = i to n) {
      swap arr[i][j] and arr[j][i]
    }
  }
  // reverse each coloumn top to bottom
  for(j = 0 to n) {
    top = 0, bottom = n - 1
    while(top < bottom) {
      swap arr[top][j] and arr[bottom][j]
      top++; bottom--;
    }
  }
  ```
