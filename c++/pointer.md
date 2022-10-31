一般情况下，源程序中所有的行都参加编译。但是有时希望对其中一部分内容只在满足一定条件才进行编译，也就是对一部分内容指定编译的条件，这就是“条件编译”。有时，希望当满足某条件时对一组语句进行编译，而当条件不满足时则编译另一组语句。

条件编译命令最常见的形式为：
 #ifdef 标识符
程序1
 #else
程序2
 #endif

它的作用是：当标识符已经被定义过(一般是用#define命令定义)，则对程序段1进行编译，否则编译程序段2。
其中#else部分也可以没有，即：
 #ifdef
程序段1
 #denif

在头文件中使用#ifdef和＃ifndef是非常重要的，可以防止双重定义的错误。如你在头文件aaa.h中定义了一个类aaa如下：
class aaa
{
};
如果两次＃include “aaa.h”（不见得是直接，也有可能两个不同的头文件中都包含了这个头文件）就会出错，因为相同的类不能定义两次。把aaa.h稍做修改：
 #ifndef aaa
 #define aaa
class aaa
{
};
 #endif
就可以避免这样的问题。因为当你已经包含过这个文件，_aaa_就会有了定义，那么#ifndef的条件为假，就不会再执行后面的类定义了。

<标识>在理论上来说可以是自由命名的，但每个头文件的这个“标识”都应该是唯一的。标识的命名规则一般是头文件名全大写，前后加下划线，并把文件名中的“.”也变成下划线

   ![图片名](图片文件路径)

纯虚函数：1,virtual 2,=0 3,没有函数体 
class(){
public:
    virtual void myfun(char * cmdline) = 0;
}
用于接口    类称为抽象类   抽象类不能创建对象
类视为规范，纯虚函数视为接口

枚举可以在定义时具体指定枚举成员对应的整数值
enum EnumName
{
E_Member1 = 3,
E_Member2 = 5
};

if (auto it = seen.find(serial); it != seen.end())

hash<K> 模板定义了可以从 K 类型的对象生成哈希值的函数对象的类型。hash<K> 实例的成员函数  operator()() 接受 K 类型的单个参数，然后返回 size_t 类型的哈希值

智能指针 
unique_ptr 拥有它所指向的对象，在某一时刻，只能有一个unique_ptr指向特定的对象，并在 unique_ptr 离开作用域时释放该对象的智能指针。
多个 shared_ptr 对象可占有同一对象。

右值引用：将亡值

struct listnode{
    int val;
    listnode * next;
    listnode(int x): val(x),next(nullptr){}
    listnode(int x, listnode * y): val(x),next(y){}
};

const vector<int> cv{ 1, 2, 3, 4, 5, 6 };
vector本身是const类型，生成的迭代器就必须是const类型。
数据本身不是const类型，但是从设计的角度来讲有些处理不应该修改该数据。这时也应该要求const类型的迭代器，以避免数据被意外修改。
C++11为此提供了cbegin和cend方法。
vector v{1, 2, 3, 4, 5, 6};
auto it = v.cbegin();

这个函数代码分配一段存储空间，这段存储空间的首地址称为这个函数的地址。
函数指针：返回类型（*p）(参数) = 

在 C 语言中 round 函数用于对浮点数 float 或者 double 或者 longdouble 四舍五入
round函数的返回是double类型，并非int类型

实例化类的两个方法：
栈创建：class c = class();用 . 访问成员
堆创建：class *c = new class() 用->访问成员

upper_bound,lower_bound 原码阅读，自定义cmp函数，没有找到可能返回begin或end
cmp函数：迭代器里第一个false元素