# <h1>63. Unique Paths II
####    time:O(m*n)   space:O(n)
####    use dp,cur[j] is the numbers of unique ways to get obstacleGrid[i][j]
####    
```
int uniquePathsWithObstacles(vector<vector<int>>& obstacleGrid) {
        int m = obstacleGrid.size();
        if(m==0) return 0;
        int n = obstacleGrid[0].size();
        vector<int> cur(n,0);
        cur[0] = 1;
        for(int i = 0; i < m ; i++){
            for(int j = 0; j < n ; j++){
                cur[j] = obstacleGrid[i][j]==1 ? 0 : j==0 ? cur[j]:cur[j]+cur[j-1];
            }
        }
        return cur[n-1];
    }
  ```
