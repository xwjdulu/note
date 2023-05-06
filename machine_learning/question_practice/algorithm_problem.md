来源力扣2448题
$$\sum_{i=0}^{i=n-1} {cost[i]*abs(num[i]-x)}$$
将nums从大到小排序
= $\sum_{i=0}^{i=k} {cost[i]*(x-nums[i])}$+$\sum_{i=k+1}^{i=n-1} {cost[i]*(num[i]-x)}$

求导：

$\sum_{i=0}^{i=k} {cost[i]}$ - $\sum_{i=k+1}^{i=n-1} {cost[i]}$

而随着x增大，导数逐渐增大，这是个凸函数最优问题，用三分法

三分法代码：

```
    while(l<r){
        int delta = (r-l)/3;
        int ml = l+delta,mr = r-delta;
        if(getc(ml)>getc(mr))
            l = ml+1;
        else
        r = mr-1;
    }
```
***
同理力扣1515题

接上题理论，一个点到其它点的带权值距离的和是凸函数

对于二维点，则需要两重三分法

对于double，我们取精度表示近似确定值：eps缩写自epsilon，表示一个小量，但这个小量又要确保远大于浮点运算结果的不确定量。eps最常见的取值是1e-8左右

```
double eps = 1e-8;
    double getMinDistSum(vector<vector<int>>& positions) {
        function<double(double,double)>dis = [&](double x,double y){
            double ans = 0;
            for(auto &&p:positions){
                ans += sqrt((x-p[0])*(x-p[0]) + (y-p[1])*(y-p[1]));
            }
            return ans;
        };
        function<double(double)>besty = [&](double x){
            double yl = 0.0,yr = 100.0;
            while(yr-yl>eps){
                double delta = (yr-yl)/3;
                double ml = yl+delta,mr = yr-delta;
                if(dis(x,ml)>dis(x,mr))
                    yl = ml;
                else
                    yr = mr;
            }
            return dis(x,yl);
        };
        double xl =0.0,xr = 100.0;
        while(xr-xl>eps){
            double delta = (xr-xl)/3;
            double ml = xl+delta,mr = xr-delta;
            if(besty(ml)>besty(mr))
                xl = ml;
            else
                xr = mr;
        }
        return besty(xl);
    }
```

