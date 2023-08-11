#98老指针auto_ptr

11引入的三个新指针：unique_ptr、share_ptr、weak_ptr

只能指针本身是通过类模板实现的

unique_ptr:只能使用move移交所有权，禁止拷贝提高安全性

share_ptr： a,b互相指向：死锁，强指针

weak_ptr：弱指针：不控制生命周期，只提供访问，share_ptr赋值给它，它通过lock的成员函数变成share_ptr
***
#this指针

隐含于每一个非静态成员函数

不可赋值， this指针的类型：const class * const:指向对象不可修改

this是右值，不可取地址

右值：也是一个表示数据的表达式，如字母常量、表达式的返回值、函数的返回值（不能是左值引用返回）等。

右值不可以取地址

右值不可以直接修改

右值只能放在等号右边

右值往往是没有名称的




