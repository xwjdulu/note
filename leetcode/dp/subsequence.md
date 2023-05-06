q1671,300求最长单调序列

朴素法o(n^2)：
```
if(num[i]>num[j])
    dp[i] = max(dp[i],dp[j]+1)
```
二分贪心法o(nlgn):
建立一个单调答案数组，将每个序列长度上的值都更新为最小值
```
vector<int>res = {-0x3f3f3f3f};
for(int &x:nums){
    if(x >res.back())
            res.emplace_back(x);
    else{
        int it = lower_bound(res.begin(),res.end(),x) - res.begin();
        res[it] = x;
    }
}
```
