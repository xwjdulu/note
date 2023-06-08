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
