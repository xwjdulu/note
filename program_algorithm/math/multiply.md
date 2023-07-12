#st表

st表离线查询区间最大值：
```
for(int i = 0;i<n;i++)
    st[i][0] = a[i];
for(int j = 1;j<l;j++){
    int d = (1<<j-1);
    for(int i = 0;i+d<n;i++){
        st[i][j] = max(st[i][j-1],st[i+d][j-1]);
    }
} 
for(int i = 0;i<m;i++){
    int l, r;
    cin>>l>>r;
    l--,r--;
    int q = ceil(log2(r-l+1))-1;
    cout<<max(st[l][q],st[r-(1<<q)+1][q])<<endl;
}
```
***

lc1483：离线查询节点的第k个节点
```
for(int i = 0;i<n;i++)
        st[i][1] = parent[i];
for(int j = 2;j<l;j++){
    for(int i = 0;i<n;i++){
        if(st[i][j-1] == -1)
            continue;
        st[i][j] = st[st[i][j-1]][j-1];
        }
}

//第k个：不断访问父亲节点，k不要和st[i][j]划等号2
```
for (int j = 0; j < 20; j++) {
    if ((k >> j) & 1) {
        node = st[node][j+1];
        if (node == -1) 
            return -1;
    }
}
```
***

