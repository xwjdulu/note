q300 贪心算法，用vector表示第i长的递归子序列的最后一位
（i长的子序列最后一位最小数只有一个可能）
再用二分法不断更新
二分法：如果元素必然存在，使用最后区间化为left == right 方法

q862：
当数组中有负数：滑动窗口就不再适用，因为窗口滑动，窗口值可能大也可能小
对于连续子数组，用前缀数组时，对于不同情况，分析队列的首尾

返回a和b的另外一个数（a+b）减