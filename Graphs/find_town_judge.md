### Leetcode 997 - AMAZON
#### Question:
- find a node who is trusted by every other node(except itself), but trusts no other node.

### Approach:
- use `int[] indegree` and `int[] outdegree` to record the trust
- finally, return the node i whose `indegree[i] == n-1` and `outdegree[i] == 0`
- TC : O(n) SC : O(n)
  ```
  for(int[] edge : trust) {
    u = edge[0]; v = edge[1]
    indegree[v]++;
    outdegree[u]++;
  }
  for(int i = 1; i<=n; i++) {
    if(indegree[i] == n-1 && outdegree[i] == 0) return i;
  }
  return -1;
  ```
