### Leetcode 463 - GOOGLE
#### Question: given 2d array of 0s and 1s
- find perimeter of island in the grid
- there is only 1 island in the grid

- below test case, yellow stripes are perimeter, answer is 16
  <img width="221" height="213" alt="image" src="https://github.com/user-attachments/assets/8364cb36-a042-4453-9f24-9fb0ae442d63" />

#### Approach 1 - DFS
- step on to cell (grid[i][j] = 1) and apply DFS
- if i or j go out of bound then perimeter++ because it means that the cell is at the border of the grid
- for a cell with value 1, if there is any 0 adjacent to that cell (only UP/DOWN/LEFT/RIGHT), perimeter++
- for marking a cell visited, make it -1 after you visit that cell
- TC : O(m * n) SC : O(1)
  ```
  at cell (i, j), value = 1
  UP : (i + 1, j) if out of bound OR value 0, then perimeter++
  DOWN : (i - 1, j) if out of bound OR value 0, then perimeter++
  LEFT : (i, j - 1) if out of bound OR value 0, then perimeter++
  RIGHT : (i, j + 1) if out of bound OR value 0, then perimeter++
  ```
  ```
  int m, n, perimeter
  DFS(grid[][], i, j) {
    if i<0 || i>=m || j<0 || j>=n || grid[i][j]==0, then perimeter++ and return;
    if grid[i][j] == -1, then return;
    grid[i][j] = -1;
    DFS(grid, i+1, j)
    DFS(grid, i-1, j)
    DFS(grid, i, j+1)
    DFS(grid, i, j-1)
  }
  main function(grid[][]) {
    m = ____, n = _____, perimeter = 0
    for(i = 0 -----> m) {
      for(j = 0 -----> n) {
        if grid[i][j] == 1 {
          DFS(grid, i, j)
          return perimeter
        }
      }
    }
    return -1
  }
  ```
