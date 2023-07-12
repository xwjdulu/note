内存分配不释放，就不能再使用了

linux下valgrind工具分析内存泄漏

heap leak:

malloc,realloc,new分配的内存：free或delete掉

resource leak：

系统分配给程序的资源没有被函数释放：handle、socket：比如分配的句柄没有释放
***
析构函数设置为虚函数：利用虚函数的多态功能：

防止内存泄漏，当父类指针指向子类对象时，释放父类指针，只会调用父类的析构函数，不会调用子类析构函数，造成内存泄漏
***
#所以：
不要像使用C语言那样自己过程式分配/释放内存而应该将分配释放交给类来负责
***

#free 和delete

delete是c++关键字，可以重载，编译器计算内存

free是c的库函数，不能重载，人为计算内存




