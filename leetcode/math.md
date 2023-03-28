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

q1734,异或交换律，a^b=c c^a = b
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

q1969:两数相加为常熟，则相乘的最大最小值！要得最小值：则相差尽可能小

q2584：筛法求质数
tmp = *max_element(nums.begin(),nums.end()),m = sqrt(tmp);
for(int i = 2;i<=m;i++){
    if(flg[i]){
        prime.emplace_back(i);
        for(int j = long(i)*i;j<=m;j+=i)
                flg[j] = false; 
    }
}
1、筛法求质数观察数据大小：一般只求到平方根sqrt（x）（最后x只能有一个比平方根大的质因数）
2、从i*i开始标记非质数，因为i（i-1）在之前i-1时已被标记

