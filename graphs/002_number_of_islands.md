#Number_of_islands

Link - https://leetcode.com/problems/number-of-islands/

<details>
    <summary>my c++ solution</summary>

    Solution

    ```cpp
        class Solution {
        public:
            int numIslands(vector<vector<char>>& grid) {
                int m = grid.size();
                int n = grid[0].size();

                vector<vector<bool> > visited(m, vector<bool>(n, false));

                int islands = 0;

                for(int i = 0; i < m; ++i){
                    for(int j = 0; j < n; ++j){
                        if(grid[i][j]!= '1'){
                            continue;
                        }
                        if(visited[i][j]){
                            continue;
                        }
                        islands++;
                        queue<pair<int,int>> q;
                        visited[i][j] = true;
                        q.push({i, j});
                        while(!q.empty()){
                            pair<int,int> cur = q.front();
                            int x = cur.first;
                            int y = cur.second;
                            q.pop();
                            if(x+1 < m){
                                if(grid[x+1][y]=='1' && !visited[x+1][y]){
                                    visited[x+1][y] = true;
                                    q.push({x+1, y});
                                }
                            }
                            if(y+1 < n){
                                if(grid[x][y+1]=='1' && !visited[x][y+1]){
                                    visited[x][y+1] = true;
                                    q.push({x, y+1});
                                }
                            }
                            if(x-1 >= 0){
                                if(grid[x-1][y]=='1' && !visited[x-1][y]){
                                    visited[x-1][y] = true;
                                    q.push({x-1, y});
                                }
                            }
                            if(y-1 >= 0){
                                if(grid[x][y-1] == '1' && !visited[x][y-1]){
                                    visited[x][y-1] = true;
                                    q.push({x, y-1});
                                }
                            }
                        }
                        // cout<<i<<" "<<j<<endl;
                        // for(int ii = 0; ii<m; ++ii){
                        //     for(int jj = 0; jj<n; ++jj){
                        //         cout<<visited[ii][jj]<<" ";
                        //     }
                        //     cout<<endl;
                        // }

                    }
                }

                return islands;
            }

        };

    ```

</details>

<details>
    <summary>Found a better solution</summary>

    ####Solution

    ```cpp

    class Solution {
        public:
            void dfs(int r, int c, vector<vector<char>>& grid) {
                if (r < 0 || c < 0 || r >=grid.size() || c >= grid[0].size() || grid[r][c] == '0')
                return ;
                grid[r][c] = '0';
                dfs(r+1, c, grid);
                dfs(r-1, c, grid);
                dfs(r, c+1, grid);
                dfs(r, c-1, grid);
            }

        int numIslands(vector<vector<char>>& grid) {
            int n = grid.size();
            int m = grid[0].size();
            int ans = 0;
            for (int i = 0; i < n; ++i) {
                for (int j = 0; j < m; ++j) {
                    if (grid[i][j] == '1') {
                        ans++;
                        dfs(i , j, grid);
                    }
                }
            }
            return ans;
        }

    };

    ```

</details>

<details>
    <summary>Time Space Complexity</summary>

    #### Time Complexity
    O(V+E)
    V=mn, E=4mn
    O(mn)
    #### Space Complexity
    O(mn), where mn is the number of cells in the input matrix

</details>
