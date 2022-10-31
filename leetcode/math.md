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