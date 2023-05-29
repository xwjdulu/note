q1986:状态子集，注意：for(int subset = mask;subset>0;subset = (subset-1)&mask)

是大于0，否则死循环，所以用subset表示当前步骤新增状态，

那么之前状态：mask^subset

先预处理subset是否满足条件

第二方法：返回值为pair：<任务数,还能做任务的时间>，然后根据当前状态找一个任务做
***
q1494 错误思路：贪心完成同一拓扑层(有的分支可以先行完成，以免有一层有太多课程)

状态压缩常用：

遍历子集：
```
for (int subMask = state; subMask; subMask = (subMask - 1) & state) {
    operate subMask...
}
```
判断子集：
x & y == x
逻辑式转0，1

思路，枚举每个状态，再看每个状态下减去一次能学的状态。
***




