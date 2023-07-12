#ios::sync_with_stdio(false)

在调用 ios::sync_with_stdio(false) 后，cout 与 stdout 不再共享同一块缓冲区，它们分别管理自己的缓冲区

因为这种同步，所以 cin、cout 比 scanf、printf 速度要慢，如果我们在使用 cin、cout 输入输出前加一句 ios::sync_with_stdio(false)，即取消缓冲区同步，可节省时间
***
#cin.tie(nullptr)

cin 默认是与 cout 绑定，所以每次 cin 操作的时候都在联系流（即输出流）调用 flush()，这样增加了 IO 负担，通过 cin.tie(nullptr) 来解除 cin 和 cout 之间的绑定，进一步加快执行效率。同时，解除绑定带来的效果，详述如下：
```
cin 默认绑定了 cout 来同步在控制台输出。“绑定”的效果，每当被“绑定”的对象有出入或输出操作，就会即时刷新（本质，在一定刷新频率下刷新）“绑定”的对象的缓冲区，以达到即时回显的效果。cout 没有默认绑定其他输出，所以 cout.tie() 获取到空指针。
```
#c++cout不输出

这是因为 cout 并不是直接输出到黑色窗口里的，而是先把输出的内容存在“缓冲区”，

这个缓冲区满了，才会把它里面的内容显示在黑色窗口。

但是，我们也可以手动让“缓冲区”显示内容——实际上 endl 做的就是先换行，再告诉缓冲区，输出内容。如果你不想换行的话，就写 cout<<"hehe"<<flush, 这也可以告诉缓冲区输出，但和 endl 不同，它不会给你换行。
***
默认情况下，cout默认输出6位有效数字,

数太大：科学计数法

小数精度：

 控制器写法：
 cout << fixed << setprecision(5);

 方法写法：
 cout.precision(5);
 cout.setf(ios::fixed);