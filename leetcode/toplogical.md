q 221 q 1277

q2421 q547
class Solution {
public:
    int numberOfGoodPaths(vector<int>& vals, vector<vector<int>>& edges) {
        int n = vals.size(),res = n;
        vector<vector<int>>nxt(n);
        for(auto &v:edges){
            nxt[v[0]].emplace_back(v[1]);
            nxt[v[1]].emplace_back(v[0]);
        }
        vector<int>father(n),id(n),sz(n,1);
        iota(father.begin(),father.end(),0);
        iota(id.begin(),id.end(),0);
        function<int(int)> find = [&](int i){
            if(i == father[i])
                return i;
            return father[i] = find(father[i]);
        };
        sort(id.begin(),id.end(),[&](int i, int j){
            return vals[i] < vals[j];
        });
        for(int &i:id){
            int fi = find(i),vi = vals[i];
            for(int &j:nxt[i]){
                j = find(j);
                if(j == fi || vals[j] > vi)
                    continue;
                if(vals[j] == vi){
                    res += sz[fi] *  sz[j];
                    sz[fi] += sz[j];  
                }
                father[j] = fi;
            }
        }
        return res;
    }
};
对于每个节点，都通过find的路径压缩，有唯一的的一个父节点，父节点的父节点为自己
记得通过find找父节点

对于互斥的并查集，a和b可以a和b+n(反向点)结合，b和a+n结合，表示互斥
在bfs中，如果要给搜索的每个点打标记，应该在它入队时就打标记，
而不是从队列中取出来再打标记，因为标记后的点无法再入队，从队列
取出来再打标记，会造成重复入队

在树中没有环，如果要求一个点a到一点b的路径，则从b出发，构建father[nxt] = b;
然后对a点dfs，while(node){a = father[a]},就可以得到一条从a到b的路径 

可以利用以下算法找到图中距离最远的两个节点与它们之间的路径：
以任意节点 p出现，利用广度优先搜索或者深度优先搜索找到以 p 为起点的最长路径的终点 x；
以节点 x 出发，找到以 x 为起点的最长路径的终点 y；
x 到 y 之间的路径即为图中的最长路径，找到路径的中间节点即为根节点。
思路：图都有一个交汇点，而离交汇点最远的那个点就是x，x一定是最长路径的端点，然后找离交汇点第二远的点

q1584 最小生成树：克鲁斯卡尔算法，普利姆算法 最小生成树
q2471  数组排序的最小交换次数错误思路：记录每个人的正确位置，然后遍历，若不在正确位置上，则放入正确位置
错误理由：当n个数都形成一个环，应该交换n-1次，但是遇到不是正确位置得数把它放入后方正确的位置，后续遍历
到该数时，计数变少
正确做法：长度减环数
见q765：for(int i = 0;i<n/2;i++){
            if(i == find(i))
                c++;
        }
c代表计算有几个环：本来i对情侣的father就是i，经过并集操作后，father改变了，由此得环数

q684  图连接问题：并查集 q839:判断是否同一集合：看父节点是否相同 判断是否已连接：cnc函数（如果没链接，则会连接）

q329:不能用单纯的动态规划，因为一个点的值可能来自左上点，而前点的值又可能来自右下
没有确定方向，只能dfs 或者；转化为拓扑结构（一定无环）：相连的且有比它大的则有出度，枚举所有出度为0的点的最长路径bfs

q127，根据数据量，不能用dfs，求拓扑结构的最短路径，应该用bfs
dijstra算法：求带权值的拓扑结构的最小路径：不断从当前点访问邻接点，更新路径值，并更新father数组

floyd算法：求图的最短路径：f[k][i][j]代表i号点与j号点可以通过前k个点相连
for (k = 1; k <= n; k++) {
  for (x = 1; x <= n; x++) {
    for (y = 1; y <= n; y++) {
      f[k][x][y] = min(f[k - 1][x][y], f[k - 1][x][k] + f[k - 1][k][y]);
    }
  }
}
dp[0][i][j]初始化：
f[0][x][y]：x 与 y 的边权，或者 0，或者无穷大（f[0][x][y] 什么时候应该是无穷大？当 x 与 y 间有直接相连的边的时候，为它们的边权；当 x = y 的时候为零，因为到本身的距离为零；当 x 与 y 没有直接相连的边的时候，为 无穷大）
怎么利用Floyd求最小环，每进行到最大点为k时，如果i，j已经可以通过前k-1个点相连了，又可以通过k相连，则成环
for(int k = 1;k<=n;k++){
    for(int i  = 1;i<=n;i++){
        for(int j = 1;j<=n;j++){
            if(k > i && k>j && i!= j && nxt[k-1].count(i-1)  && nxt[k-1].count(j-1) )
                    res = min(res,dp[k-1][i][j]+2);
            dp[k][i][j] = min(dp[k-1][i][j],dp[i-1][k][i]+dp[i-1][k][j]);           
        }
    }
}

q6330：数据量不能用floyd法，也不能像2360用dfs时间戳法：因为从一个点到目标点会有多个路径，产生多个时间戳
用bfs法求得从一个点x到邻接两点的路长，但x可能前面有其它点，比如：[0,1],[1,2],[1,3],[2,3]，但根据n<=1000
可以o(n^2),即遍历每个点为起点，心急吃不了热豆腐啊！！！注意先处理再入队，bfs前先初始化

q269：判断拓扑结构是否有环
1，相邻单词第一个不同代表拓扑顺序
2，要把所有出现的单词都放入答案，不用vector<vector<int>>nxt,
用unordered_map<char,vector,int>>nxt表示出现了哪些单词
3用dfs时，在return前添加char进res，越早return，越是最低级
4用bfs，不断更新入度表，入度为0则加入res，是高优先级

q2617,2612:把几何问题转化成拓扑问题，从出发点(2612:p)(2617:0,0)bfs到其余点的最短距离
去重：一个点有很多相邻点，而我们只想要访问一个点一次，采用set，不断插入bfs的queue和从set删除
unordered_set<int>ban = {banned.begin(),banned.end()};
q.push({0,0});
auto &s = st[l%2];
for(auto it = s.lower_bound(l);it != s.end() && *it<=r;it = s.erase(it))

q2646:正确思路：先遍历每次trip，进行price更新，再dfs树，判断一个节点是否减半：注意不能贪心认为隔一个节点减半就ok，类似冷却的股票买卖和打家劫舍：100，1，1，100，中间两个都不减半
在dfs求价格和时，如果在参数上加上一个是否可以打折，则会在函数体内进行2次dfs，o(2^n)复杂度过高，可以记忆化或者其实dfs内只一次dfs，返回值为打折或者不打折
注意dfs返回值利用和(int pre)不要原路死循环
tarjan算法求公共祖先！！！！
function<void(int, int)> tarjan = [&](int pos, int pre) {
    father[pos] = pre;        //father：父亲数组(直接相连)
    for (int  x: nxt[pos]){         //遍历邻接点
        if (x != pre) {
            tarjan(x, pos);
            pa[x] = pos        //pa:并查集父亲：x和pos同一集合
        }
    }
    for (int x: qry[pos]) {           //qry[pos]:pos要到的所有节点
        if(x == pos || vis[x]){
            diff[x]++;
            diff[y]++;
            int y = find(x);
            diff(y)--;
            if(father[y]>=0)
                diff[father[y]]--;
        }
    }
    vis[pos] = true;
};

q815:bfs求最短路径，m:公交数量，n:站点数量
bfs每个站点和相邻站点：o(n^2^*m)错
bfs每个公交车：o(m * n/m * m)对，注意这样有多个起点终点

q2462:dijstra
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

或者floyd算法：注意：三维优化二维，路径更新只需要  (是有向图，注意下标位置)
for(int i = 0;i<n;i++){
    for(int j = 0;j <n;j++){
        dp[i][j] = min(dp[i][j],dp[i][x]+z+dp[y][j]);
    }
}

q2101:首先注意读题和例子：是圆心在爆炸范围内！第二：不能用并查集，别急啊：i能传j，j不一定能i，这是有向，不是并查集
第三：注意需要每个点都跑一次dfs/bfs(也是因为有向)



