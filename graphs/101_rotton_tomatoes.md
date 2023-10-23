#Rotting Oranges

Link - https://leetcode.com/problems/rotting-oranges/

<details>
<summary>Solution (Click to expand)</summary>
    ```cpp
        class Solution {
        public:
            int m;
            int n;
            bool isValidCoordinates(int i, int j){
                if(i>=0 && j>=0 && i<m && j<n){
                    return true;
                }
                return false;
            }
            bool allZeroOr2(vector<vector<int>>& grid){
                for(int i=0; i<m; ++i){
                    for(int j=0; j<n; ++j){
                        if(grid[i][j]==1){
                            return false;
                        }
                    }
                }
                return true;
            }
            void mydfs(int i, int j, vector<vector<int>>& grid, int depth){
                grid[i][j]=depth;
                depth+=1;
                if(isValidCoordinates(i-1,j))
                    if(grid[i-1][j] > depth || grid[i-1][j] == 1){
                        mydfs(i-1,j,grid,depth);
                    }
                if(isValidCoordinates(i+1,j)){

                    if(grid[i+1][j] > depth || grid[i+1][j] == 1 ){
                        mydfs(i+1,j,grid,depth);
                    }
                }
                if(isValidCoordinates(i,j-1))if(grid[i][j-1] > depth || grid[i][j-1] == 1)mydfs(i,j-1,grid,depth);
                if(isValidCoordinates(i,j+1))if(grid[i][j+1] > depth || grid[i][j+1] == 1)mydfs(i,j+1,grid,depth);
            }
            int orangesRotting(vector<vector<int>>& grid) {
                m = grid.size();
                n = grid[0].size();

                // check if all are 0 or 2
                if(allZeroOr2(grid)) return 0;

                //do dp based for every initial 2
                // 3 = 1 min, 4 means 2 min and so on...
                for(int i=0; i<m; ++i){
                    for(int j=0; j<n; ++j){
                        if(grid[i][j]==2)mydfs(i,j,grid,2);
                    }
                }

                for(int i=0; i<m; ++i){
                    for(int j=0; j<n; ++j){
                        if(grid[i][j]==1){
                            return -1;
                        }
                    }
                }

                int max = 0;
                for(int i=0; i<m; ++i){
                    for(int j=0; j<n; ++j){
                        if(max<grid[i][j]){
                            max=grid[i][j];
                        }
                    }
                }

                return max-2;
            }

        };
    ```

</details>
