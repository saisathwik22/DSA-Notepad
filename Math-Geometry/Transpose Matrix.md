### Leetcode 867 - Amazon, Wipro, InfoEdge, MakeMyTrip
#### Transponse of a matrix

#### Approach - Space : O(m * n) | TC : O(m * n)
  ```
  int[][] arr given
  int m = arr.length;
  int n = arr[0].length;
  int[][] result = new int[n][m]
  for(i = 0 ----> m) {
    for(j = 0 ----> n) {
      result[j][i] = arr[i][j]
    }
  }
  return result;
  ```
#### In place approach is possible only for Square Matrix
