```
1:
int n;
cin>>n;

2:
void fun(int n)

3:
int n = string.size()

int a[n]
```
只有2，3能成功：Variable Length Array
***
bitset是c++中的一个类库，来管理一系列bit位，及二进制串。类似于数组，但每个元素只能是0或1且仅用1bit的空间

int a = bitset.u_long();to_ulong转化为无符号长整数
***
请注意，c++ 无论是c数组还是vector都是越界出错运行时不会立即报错，最后才抛出异常::operator delete(__p);

C++ 提供了 std::vector 类模板，它允许两者。 operator[] 旨在提高效率。语言标准不要求它执行边界检查(尽管它也不禁止)。 vector 也有 at() 成员函数，保证执行边界检查


