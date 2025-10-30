### Leetcode 36
- given 9x9 grid is valid if
- if each row has 1-9 digits only without repititon
- if each col has 1-9 digits only without repitition
- if each 3x3 subgrid has 1-9 digits only without repitition

### Approach 1 - Brute Force

  ```
  class Solution {
    public boolean validSub(char[][] board, int sr, int er, int sc, int ec) {
        Set<Character> st = new HashSet<>();
        for(int row = sr; row <= er; row++) {
            for(int col = sc; col <= ec; col++) {
                char ch = board[row][col];
                if(ch == '.') continue;
                if(st.contains(ch))return false;
                st.add(ch);
            }
        }
        return true;
    }
    public boolean isValidSudoku(char[][] board) {
        // Row validation
        for(int row = 0; row < 9; row++) {
            Set<Character> s = new HashSet<>();
            for(int col = 0; col < 9; col++) {
                char ch = board[row][col];
                if(ch == '.') continue;
                if(s.contains(ch)) return false;
                s.add(ch);
            }
        }
        // Column validation
        for(int col = 0; col < 9; col++) {
            Set<Character> s = new HashSet<>();
            for(int row = 0; row < 9; row++) {
                char ch = board[row][col];
                if(ch == '.') continue;
                if(s.contains(ch)) return false;
                s.add(ch);
            }
        }
        // 3x3 subgrid validation
        for(int sr = 0; sr < 9; sr += 3) {
            int er = sr + 2;
            for(int sc = 0; sc < 9; sc += 3) {
                int ec = sc + 2;
                if(!validSub(board, sr, er, sc, ec)) {
                    return false;
                }
            }
        }
        return true;
    }
}
  ```

### Approach 2
- In every 3x3 subgrid, (i/3, j/3) is same for every element in a subgrid
- TC : O(81) SC : O(81)

  ```
  class Solution {
    public boolean isValidSudoku(char[][] board) {
        int n = board.length;
        Set<String> st = new HashSet<>();
        for(int i = 0; i < 9; i++) {
            for(int j = 0; j < 9; j++) {
                if(board[i][j] == '.') continue;
                String num = String.valueOf(board[i][j]);
                String row = num + "_row_" + i;
                String col = num + "_col_" + j;
                String box = num + "_box_" + (i/3) + "_" + (j/3);
                if(st.contains(row) || st.contains(col) || st.contains(box)) {
                    return false;
                }
                st.add(row);
                st.add(col);
                st.add(box);
            }
        }
        return true;

    }
}
  ```
