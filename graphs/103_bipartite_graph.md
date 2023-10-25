#Bipartite graph

Link - https://leetcode.com/problems/is-graph-bipartite

<details>
<summary>Solution</summary>

```
class Solution {
public:
    bool isBipartite(vector<vector<int>>& graph) {
        int n = graph.size();
        vector<int> visited(n,0);
        queue<int> qu;
        visited[0] = 1;
        for(int i=0;i<n;++i){
            qu.push(i);
            while(!qu.empty()){
                int cur = qu.front();
                qu.pop();
                for(int j=0;j<graph[cur].size();++j){
                    if(visited[graph[cur][j]]==0){
                        visited[graph[cur][j]] = visited[cur]%2 +1;
                        qu.push(graph[cur][j]);
                        continue;
                    }
                    if(visited[graph[cur][j]] != visited[cur]%2 + 1){
                        return false;
                    }
                }
            }
        }
        return true;
    }
};
```

</details>

<details>
<summary>Time Space Complexity</summary>

- Time
  - O(V+E)
- Space
  - O(V)?

</details>
