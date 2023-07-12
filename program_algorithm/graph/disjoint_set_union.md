lc2421 lc547
```
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
```
对于每个节点，都通过find的路径压缩，有唯一的的一个父节点，父节点的父节点为自己
记得通过find找父节点

if(i == fa[i])：快速判断有多少个集合

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
***
lc2076 lc886

886用反向点：互斥就把a和b的反向点结合，后续遇c 、d已经在同一集合了，就false

而2076不能用反向点，是对于每个request，如果相连，本身就是true，是判断request相连两个集合是否会产生限制，而不是886的情况：判断限制数组里是否在同一集合



