```cpp
vector<int> numOfIslands(int n, int m,
    vector<vector<int>> &operators) {
    DisjointSet ds(n * m);
    int vis[n][m];
    memset(vis, 0, sizeof vis);
    int cnt = 0;
    vector<int> ans;
    for (auto it : operators) {
        int row = it[0];
        int col = it[1];
        if (vis[row][col] == 1) {
            ans.push_back(cnt);
            continue;
        }
        vis[row][col] = 1;
        cnt++;
        // row - 1, col
        // row , col + 1
        // row + 1, col
        // row, col - 1;
        int dr[] = { -1, 0, 1, 0};
        int dc[] = {0, 1, 0, -1};
        for (int ind = 0; ind < 4; ind++) {
            int adjr = row + dr[ind];
            int adjc = col + dc[ind];
            if (isValid(adjr, adjc, n, m)) {
                if (vis[adjr][adjc] == 1) {
                    int nodeNo = row * m + col;
                    int adjNodeNo = adjr * m + adjc;
                    if (ds.findUPar(nodeNo) != ds.findUPar(adjNodeNo)) {
                        cnt--;
                        ds.unionBySize(nodeNo, adjNodeNo);
                    }
                }
            }
        }
        ans.push_back(cnt);
    }
    return ans;
}
```