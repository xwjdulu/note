q300 贪心算法，用vector表示第i长的递归子序列的最后一位
（i长的子序列最后一位最小数只有一个可能）
再用二分法不断更新
二分法：如果元素必然存在，使用最后区间化为left == right 方法

q862：
当数组中有负数：滑动窗口就不再适用，因为窗口滑动，窗口值可能大也可能小
对于连续子数组，用前缀数组时，对于不同情况，分析队列的首尾

返回a和b的另外一个数（a+b）减

kmp算法中，求前缀数组，求i+1的prefix时，在prefix[i]基础上判断：j代表公共前缀长度
如果s[i+1] == s[j],则找到了公共前缀
如果不等，找位置i上第二公共长j，而这个j=prefix[prefix[i]];
    for (int i = 1; i < n; i++) {
        int j = pi[i - 1];
        while (j > 0 && s[i] != s[j]) 
            j = pi[j - 1];
        if (s[i] == s[j]) 
            j++;
        pi[i] = j;
    }
q1668
class Solution {
public:
    int maxRepeating(string sequence, string word) {
        int n = sequence.size(),m = word.size();
        vector<int>prefix(m);
        for(int i = 1;i<m;i++){
            int j = prefix[i-1];
            while(j>0 && word[j] != word[i]){
                j = prefix[j-1];
            }
            if(word[j] == word[i])
                j++;
            prefix[i] = j;
        }
//对前缀数组进行偏移，这样j = prefix[j] j代表长度才能转化为代表下标，但同时，
j代表j+1的下标的字符在进行比较
        for(int &x:prefix)
            x--;
        vector<int>dp(n+1);
        int j = -1;
        for(int i = 0;i<n;i++){
//如果匹配失败，从小字符串选下一个
            while(j != -1 && sequence[i] != word[j+1]){
                j = prefix[j];
            }
//匹配成功
            if(sequence[i] == word[j+1]){
                j++;
                if(j == m-1){
                    dp[i] = (i == m-1)?1:(dp[i-m]+1);
                    j = prefix[j];
                }
            }
        }
        return *max_element(dp.begin(),dp.end());
    }
};

m斤水果，最多搬n斤，搬(m+n-1)/n次
n转化为m进制，不断对m取余，然后对于幂可以m*m，也可以n/m
得到字符串中出现次数最少的字符只能暴力法

q1130 贪心：单调栈  每个数都要被左右的比它大的数消去，代价最小，则选更小的数消去中间数
https://leetcode.com/problems/minimum-cost-tree-from-leaf-values/solutions/339959/One-Pass-O(N)-Time-and-Space/

q659,双哈希模拟构建每一个子序列  q846，记录每一个牌的数量，构建牌
q955,遍历每一个字母位置下前后单词比较，看看是否是字典序，如果已经是字典序则不用比较，如果不是，则删除
注意，两个相同的单词也是字典序

q714 贪心
q406 核心思路，矮的对高的没有影响

区间问题，常常贪心排序，（记得用引用优化加速）
