# Algorithm: Detect Squares (Leetcode 2013)

---

## Data Structure
Let `pointsByX` be a map of maps:
    pointsByX[x][y] → count of how many times point (x, y) was added

---

## Procedure ADD(point)
Input: (x, y)
Output: None

1. if x not in pointsByX:
       create empty map for pointsByX[x]

2. pointsByX[x][y] += 1

---

## Procedure COUNT(point)
Input: (x, y)
Output: total number of axis-aligned squares using (x, y)

1. totalSquares ← 0

2. for each x2 in pointsByX:
       if x2 = x:
           continue

       side ← |x2 - x|

       for each y2 in { y + side, y - side }:
           
           count1 ← pointsByX[x2][y2]   if exists else 0
           count2 ← pointsByX[x2][y]    if exists else 0
           count3 ← pointsByX[x][y2]    if exists else 0

           totalSquares ← totalSquares + (count1 × count2 × count3)

3. return totalSquares

---

## End of Algorithm
