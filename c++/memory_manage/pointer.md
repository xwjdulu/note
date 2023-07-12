98老指针auto_ptr

11引入的三个新指针：unique_ptr、share_ptr、weak_ptr

只能指针本身是通过类模板实现的

unique_ptr:只能使用move移交所有权，禁止拷贝提高安全性

share_ptr： a,b互相指向：死锁，强指针

weak_ptr：弱指针：不控制生命周期，只提供访问，share_ptr赋值给它，它通过lock的成员函数变成share_ptr
***




