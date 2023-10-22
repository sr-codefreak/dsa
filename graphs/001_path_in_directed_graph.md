#Path_in_directed_graph

Question:

Link https://www.interviewbit.com/problems/path-in-directed-graph/

my c++ - 1 solution

```
int dfs(int start, int A,vector<vector<int> >  &graph, vector<bool> &visited){
        visited[start] = true;
        if(start == A){
                return 1;
        }
        // if(graph[start].size() == 0){
        //         return 0;
        // }
        int response = 0;
        for(int i = 0; i < graph[start].size(); ++i){
                if(visited[graph[start][i]])
                        continue;
                visited[graph[start][i]] = true;

                response = dfs(graph[start][i], A, graph, visited);
                if(response == 1){
                        return 1;
                }
        }

        return 0;

}

int Solution::solve(int A, vector<vector<int> > &B) {
        vector<vector<int> > myGraph(A+1, vector<int> (0, 0));
        vector<bool> visited(A+1, false);

        for(int i = 0; i < B.size(); ++i){
                myGraph[B[i][0]].push_back(B[i][1]);
        }
        // for(int i= 0; i<myGraph.size(); ++i){
        //     for(int j =0 ; j< myGraph[i].size(); ++j){
        //         cout<<i<<"-> "<<myGraph[i][j]<<" ";
        //     }
        //     cout<<endl;
        // }

        return dfs(1, A, myGraph, visited);
}


```

Time Complexity - O(A+M)

Space Complexity - O(A)
