q 857   wage总>=quality总 * (wage i/quality i)
有quality总，(wage i/quality i)两个未知数，先用最小的(wage i/quality i)
再用可能的quality总 枚举

如果 n 是 4 的幂，那么它可以表示成 4^x 
的形式，我们可以发现它除以3的余数一定为1，即：
4^x = (3+1)^x 
如果n是2的幂却不是4的幂，那么它可以表示成 4^x * 2 
此时它除以 33 的余数一定为2

q264丑数：第n个丑数是之前的最大质因数倍数再乘质因数（记录质因数倍数下标：动态规划）
但是q1201：丑数可以是其它数的倍数
q878
采用二分搜索

get common divisor
int gcd(int x, int y) {
    if (x == 0)
        return y;
    return gcd(y % x, x);
}
最小公倍数：a*b/gcd
三个数的最小公倍数：两个数的最小公倍数与第三数求最小公倍数

q1201:假丑数用除法确定是第几个丑数
区间必然存在的二分法：不断二分使区间长度为1，不要if(mid == n),return mid;
陷阱，可能不止一个数满足条件，区间变化要较大数还是较小数。
真丑数用动态规划

            int h = i >> 6, m = i & 63; // 用位运算取出高 4 位和低 6 位
            if (h < 12 && m < 60 && __builtin_popcount(i) == turnedOn

杨辉三角：组合数
奇数的因数只能是奇数

斐波那契数 F(n)F(n) 是齐次线性递推，根据递推方程 F(n)=F(n-1)+F(n-2)，
可以写出这样的特征方程：
x^2=x+1
y^n = c1*x1^n+c2*x2^n;

m和n的数相乘，长度为m+n(-1),且num1[i]*num2[j]的位置:i+j
求最大值、最小值：经典二分
多次求区间和：前缀和，多次求区间最值：单调队列

pair，vector也可参与比较·
二分法求mid，如果区间内必有答案法，注意应该取较大mid还是较小mid，避免死循环

水塘抽样：
   int getRandom() {
        int i = 1, ans = 0;
        for (auto node = head; node; node = node->next) {
            if (rand() % i == 0) { // 1/i 的概率选中（替换为答案）
                ans = node->val;
            }
            ++i;
        }
        return ans;
    }

q880:倒推，出口反推入口，变化后反推变化前
q2527,q389,对于位运算，可以独立判断每一位，对于异或，本质判断位上1的个数，判断奇数个数的元素：异或

q1363 从集合中选取大部分：选取少部分  map的key与value，value默认有复杂数据类型
找到两个奇数出现次的元素，从异或的结果的某一个‘1’位，分类异或。

裴蜀定理，对于a，b d=gcd(a,b); ax+by = d
证明：令 s= ax+by 是最小非负线性组合 r1 = a%s = a-k*(ax+by),是a，b的线性组合且0=<r1<s 
则r1 = 0,同理，r2 = b%s = 0,s能同时被a，b整除，得证

q470 拒绝采样，一直拒绝，直到采样到想要的

小数部分转化二进制，每次乘二，若有1，则置1，否则置0，再不断乘余下的小数
q1590 取模运算，可以每个数都先取模后再运算

括号里上a下b，是组合数的古典写法，a选b
(A + B) % mod = ((A % mod) + (B % mod)) % mod
(A * B) % mod = ((A % mod) * (B % mod)) % mod
(A - B) % mod =((A % mod) - (B % mod) +mod) % mod
 while(time){
    if(time & 1)
            ans = (res * ans)%mod;
    res = (res * res)%mod;
    time >>= 1;
}



q6329 要使num[i+x*n+y*k] == num[i],则num[i] == num[i + z*gcd(k,n)];裴蜀定理
即数组要满足两个周期，循环数组视为周期为n的周期数组，则要满足gcd(t1,t2)为周期，gcd可以直接调用
注意求变为一个数，贪心变为中位数就行，不同于q2602,变为某个特定的数需要分成更大更小的数们的前缀和特定的数的差距

单调的连续子数组：
q6392,q898,q1521:连续子数组的值去重，求每个连续子数组产生的值，暴力思路是枚举每个起点后枚举终点，o(n^2)
但注意到同一边界的子数组随着长度只会递增或递减，具有单调性，于是我们枚举子数组的值并进行去重：
q1521：对于每个右边界，有一个数组记录每个左边界到某个右边界的数组值，遍历每个右边界并去重
int closestToTarget(vector<int>& arr, int target) {
    vector<int>a;
    int res = 0x3f3f3f3f; 
    for(int &x:arr){
        vector<int>tmp;
        int pre = -1;
        for(int &y:a){
            y &= x;
            if(pre>=0 && tmp[pre] == y)
                continue;
            pre++;
            tmp.emplace_back(y);
            res = min(res,abs(y-target));
        }
        a = move(tmp);
        a.emplace_back(x);
        res =min(res,abs(x-target));
    }
    return res;
}





