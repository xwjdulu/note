线段树： 

lc2589 ：区间问题先贪心排序，对于每个区间，若时间不够，填补右方

线段树懒操作：lazy数组不为空代表它的左右子树需要更新，所以

1：在当前tree节点，当lazy置true的时候，它的tree值就需要改变了

2：每次对左右子树操作时，先判断是否要spreadlazy；

```
void spreadlazy(int idx,int left,int right){
    int mid = left + ((right-left)>>1);
    if(idx*2+1<=8000){
        tree[idx*2] = mid-left+1;
        lazy[idx*2] = true;
        tree[idx*2+1] = right-mid;
        lazy[idx*2+1] = true;
    }
    lazy[idx] = false;
}
```

核心思路：划分树的左右子区间，如果左右子区间有所求区间部分，则进入，当当前idx代表的区间已经是目标区间的子区间了，则return

对于区间问题：int idx,int treeleft, int treeright 区间代表的left，right可以设置小一点

```
update(int treeid,int treel,int treer,int l,int r)

对于线段树可能最大值为n，但实际该次实例最大值为m，可以：
update(1,1,m,left,right)
```

注意，该题的update操作：如果树区间是子区间且树区间需要被填满，则返回，否则，先进入树的右子区间。

把需要增加的工作日参数设为引用

lc732    
线段树离散化：
```
unordered_map<int, pair<int, int>> tree;
void update(int start, int end, int l, int r, int idx) {
    if (r < start || end < l) {
        return;
    } 
    if (start <= l && r <= end) {
        tree[idx].first++;
        tree[idx].second++;
    } 
    else {
        int mid = (l + r) >> 1;
        update(start, end, l, mid, 2 * idx);
        update(start, end, mid + 1, r, 2 * idx + 1);
        tree[idx].first = tree[idx].second + max(tree[2 * idx].first,tree[2 * idx + 1].first);
    }
}
int book(int start, int end) {            
    update(start, end - 1, 0, 1e9, 1);
    return tree[1].first;
}
```
***
二维丶边查询边更新丶离散化丶树状数组求区间最大值：

lc2736：

使用map离散化并让序号表示从1到tot表示从大到小

nums1视为x，nums2视为y

把查询和序号，x，y和sum都放入一个二维数组，进行排序
```
for(int i= 0;i<m;i++){
    auto q = queries[i];
    vc.push_back({mp[q[0]],mp[q[1]],i});
}

for(int i= 0;i<n;i++){
    int s = nums1[i]+nums2[i];
    vc.push_back({mp[nums1[i]],mp[nums2[i]],-s});
}
```

依次进行更新或查询，后面的vc[i]一定是更小的x，前面的点都符合要求，再从树状数组里得到前v[1]大的最大值
***
lc2547
```
const int lmt = 1e3;
int tree[4*lmt], lazy[4*lmt], pre[lmt+1],pp[lmt+1];
class Solution {
public:
    void spread(int id){
        int t = lazy[id];
        lazy[id] = 0;
        if(t){
            tree[id*2] += t;
            lazy[2*id] += t;
            tree[id*2+1] += t;
            lazy[2*id+1] += t;
        }
        return;
    }
    void update(int id,int tl,int tr,int l,int r,int v){
        if(tl>=l && tr<=r){
            tree[id] += v;
            lazy[id] += v;
            return;
        }
        spread(id);
        int m = (tr+tl)/2;
        if(m>=l){
            update(2*id,tl,m,l,r,v);
        }
        if(m<r){
            update(2*id+1,m+1,tr,l,r,v);
        }
        tree[id] = min(tree[id*2],tree[id*2+1]);
        return;
    }
    int query(int id,int tl,int tr,int l,int r){
        if(tl>=l && tr<=r)
            return tree[id];
        spread(id);
        int m = (tr+tl>>1), res = 0x3f3f3f3f;
        /*
        if(m>=r)
            return query(2*id,tl,m,l,r);
        if(m+1<=l)
            return query(2*id+1,m+1,tr,l,r);
        return min(query(2*id,tl,m,l,r),query(2*id+1,m+1,tr,l,r));
        */
        if(m>=l){
            res = min(res,query(id*2,tl,m,l,r));
        }
        if(m<r){
            res = min(res,query(id*2+1,m+1,tr,l,r));
        }
        return res;
    }
    int minCost(vector<int>& nums, int k) {
        memset(tree,0,sizeof(tree));
        memset(lazy,0,sizeof(lazy));
        memset(pre,0,sizeof(pre));
        memset(pp,0,sizeof(pp));
        int n = nums.size(),cur = 0;
        for(int i = 1;i<=n;i++){
            int x = nums[i-1];
            update(1,1,n,i,i,cur);
            update(1,1,n,pre[x]+1,i,-1);
            if(pre[x])
                update(1,1,n,pp[x]+1,pre[x],1);
            pp[x] = pre[x];
            pre[x] = i;
            cur = k+query(1,1,n,1,i);
        }
        return cur+n;    
    }
};
```