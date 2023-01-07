q223 850
两个矩形的重叠面积：在xy轴的映射：(x1,x2),(y1,y2)   (x3,x4),(y3,y4)
只有 overlapx =  min(x2,x4) - max(x1,x3)
     overlapy = min(y2,y4) - max(y1,y3)
只有两者都存在，才有重叠
q391 扫描线
q827  求满足条件的块，再遍历，假使其翻转

二维数组旋转：1，划分为块  2，翻转：swap
二维数组的四个方向：vector<vector<int>>(4,vector<int>(2));
bfs与queue

q895:
频率栈：按频率从大到小出栈：
为每个频率都建栈，同时维护最大频率maxfq，从vc[maxfq]出栈
除了map，set，c++自带容器嵌套

