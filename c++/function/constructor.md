#对构造函数的理解：

变量的创建：1、内存申请；2、声明；3、初始化

基础变量直接完成3步，自己的变量（比如类）用构造函数完成第三步

拷贝构造函数：使对象和变量一样方便赋值

(如果没有拷贝构造函数：浅拷贝：被赋值对象内存没有释放)
***
c11新特性：移动构造函数

C++11引入移动语义：源对象资源的控制权全部交给目标对象。

移动构造函数的第一个参数必须是自身类型的右值引用（不需要const，为啥？右值使用const没有意义）

不需要进行复制操作。移动操作比复制操作更高效，因为它不需要分配新的内存或复制现有的内存。
***
父类构造函数–>成员类对象构造函数–>自身构造函数

（当一个类的成员是另一个类的对象时，这个对象就叫成员对象.）
***

