大数组定义在main函数中不能执行，将其定义为全局变量可以执行

数组定义在函数中时，占用的内存来自栈空间，栈空间是在进程创建时初始化的，有固定的大小，一般很小，所以太大的数组会耗光栈空间。全局变量一般分配在数据段，可以比较大。
***
#为什么数据范围小时用vector存储会比unordered_map高效

缓存友好性：计算机读取缓存比读取内存高效

在读取数据时，会把地址周围的也进行缓存

vector是连续地址，更容易被缓存命中，而unordered_map是在内存中分散的
***
堆：G左右、有碎片     栈：M左右。无碎片(新使用，旧内存已经弹出)


