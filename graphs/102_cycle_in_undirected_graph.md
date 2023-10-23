#Cycle in undirected graph

Link - https://www.interviewbit.com/problems/cycle-in-undirected-graph/

<details>
    <summary>My Solution</summary>

    bool dfs(vector<vector<int> > &graph, int cur, int prev, vector<bool> &visited){

        for(int i=0; i<graph[cur].size(); ++i){
            if(graph[cur][i] == prev){
                continue;
            }
            if(visited[graph[cur][i]]){
                return true;
            }
            visited[graph[cur][i]] = true;
            if(dfs(graph, graph[cur][i],cur, visited)){
                return true;
            }
        }
        return false;
    }

    int Solution::solve(int A, vector<vector<int> > &B) {
        vector<vector<int> > graph(A+1, vector<int>(0));
        for(int i=0; i<B.size(); ++i){
            graph[B[i][0]].push_back(B[i][1]);
            graph[B[i][1]].push_back(B[i][0]);
        }
        for(int i=1; i<=A; ++i){
            vector<bool> visited(A+1, false);
            if (dfs(graph, i, i, visited)){
                return 1;
            }
        }
        return 0;
    }

</details>
<details>
<summary>Hint</summary>

- Convert to adjacency list,
- Check cycle using DFS
- For every adjacent vertex (u for a given vertex v) which is visited and not the parent vertex (not v), there exists a cycle.

</details>

<details>
<summary>Time Space Complexity</summary>

- Time complexity
  - O(V+E)
- Space
  - O(V+E)?

</details>
