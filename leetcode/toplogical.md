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

