#余数问题

lc:1015 

找出k是什么值时，n取k的余数n%k产生了循环，代表return 0；

设n%k == m%k ，则 要使不存在n整除k， (n-m)%k == 0

因为 n-m == 11，，，00式

当k不为2或5的倍数，与10互质，没有公因数，那么11，，，00形式的数对k取余，永远不可能为0，而如果return 0：则有11，，，00形式的数对k取余为0，所以：取余不可能为0，一定有解
***
#埃氏筛法

lc：2584：筛法求质数

cf: 1826c:筛法求因数
```
for(int i = 2;i*i<=n;i++){
    if(flg[i]){
        prime.emplace_back(i);
        for(int j = long(i)*i;j<=n;j+=i)
                flg[j] = false; 
    }
}
```
1、只求到平方根sqrt（n）（对于一个数x，用较小的那个因数进行标记）

2、j从i*i开始标记非质数，因为i（i-1）在之前i-1时已被标记

lc:2709：预处理每个数有哪些质因数

之后怎么判断连接更快？并查集

文件域是用来声明变量和函数的，不能在这里写个for循环
```
#define limit int(1e5+1)
using ll = long long;
vector<int>p[limit];
vector<int>fa;
vector<int>sz;
bool init =  false;
```
***


