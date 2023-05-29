#floyd dijstra

lc2262 , lc2462  

dijstra也是bfs思想，不断地找下一层的最短路
```
struct edge {
  int v, w;      //v代表权值，w代表相邻点
};
vector<edge> e[maxn];       //存储边权
int dis[maxn], vis[maxn];  
void dijkstra(int n, int s) {
  memset(dis, 63, sizeof(dis));
  dis[s] = 0;
  for (int i = 1; i <= n; i++) {
    int u = 0, mind = 0x3f3f3f3f;   //u为s出发未访问的最近点，mind表示距离
    for (int j = 1; j <= n; j++)
      if (!vis[j] && dis[j] < mind) u = j, mind = dis[j];
    vis[u] = true;         
    for (auto ed : e[u]) {     //对于u的邻接点，更新路径
      int v = ed.v, w = ed.w;
      if (dis[v] > dis[u] + w) dis[v] = dis[u] + w;
    }
  }
}
```
或者floyd算法：注意：路径更新是二维运算  (是有向图，注意下标位置)

x到y新增路径
```
for(int i = 0;i<n;i++){
    for(int j = 0;j <n;j++){
        dp[i][j] = min(dp[i][j],dp[i][x]+z+dp[y][j]);
    }
}
```
***
#bfs

lc815:bfs求最短路径，m:公交数量，n:站点数量

bfs每个站点和相邻站点：o(n^2^*m)错

bfs每个公交车：o(m * n/m * m)对，注意这样有多个起点终点
***
