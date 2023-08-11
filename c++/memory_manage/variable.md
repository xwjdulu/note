# 数据类型：auto，decltype

未初始化数据系统无法推导，并且在编译时报错。
```
auto xx; 
// error: declaration of variable ‘xx’ with deduced type ‘auto’ requires an initializer
```

显示变量有两种类型
```
auto int xx2;
 // error: two or more data types in declaration of ‘xx2’
```

不允许为函数的参数使用
```
void test(auto i){ 
}
// error: ‘auto’ not allowed in function prototype
```

不能用于非静态成员变量
```
struct Stu{
    auto num_ = 95275;       
    // error: 'auto' not allowed in non-static struct member
    static const auto age_ = 10;  
    //OK： age_  -> static const int
};

```

auto无法定义数组
```
int arr[10] = {0,1,2,3,4,5,6,7,8,9};    // OK:
auto aa = arr;                          // OK:
auto rr[10] = arr;              // error: 'rr' declared as array of 'auto'
auto r1[10] = {0,1,2,3,4};      // error: 'r1' declared as array of 'auto'  
```
***
#constexpr
constexpr表示这玩意儿在编译期就可以算出来（前提是为了算出它所依赖的东西也是在编译期可以算出来的）。而const只保证了运行时不直接被修改（但这个东西仍然可能是个动态变量）。

explicit为清晰的;明确的之意.顾名思义,关键字explicit可以阻止隐式转换的发生
implicit

size_t是一些C/C++标准在stddef.h中定义的，size_t类型表示C中任何对象所能达到的最大长度，它是无符号整数。

***
decltype 推导的表达式可简单可复杂，在这一点上 auto 是做不到的，auto 只能推导已初始化的变量类型。
***
块大小：2、4、8、16等字节

为什么内存对齐增加效率：如果数据是从 1 字节开始的，就⾸先要将前 4 个字节读取到寄存器，并再次读取 4-7 个字节数据进⼊寄存器，接着把 0 字节，5，6，7 字节的数据剔除，最后合并 1，2，3，4字节的数据进⼊寄存器，所以说，当内存没有对⻬时，寄存器进⾏了很多额外的操作，⼤⼤降低了 CPU 的性能。
***
#类型转换

1：static_cast 用于执行非多态类型之间的类型转换，例如整型和浮点型之间的转换、基类和派生类之间的指针或引用转换、void 指针和其他指针类型之间的转换等。该转换在编译时完成，通常不会检查运行时错误。

2：dynamic_cast 用于在运行时进行多态类型的转换。它通常用于将基类指针或引用转换为派生类指针或引用，以及在类层次结构中进行下行转换

3：reinterpret_cast 用于在不同的指针类型之间进行转换，例如将一个指针转换为一个整数，或将一个整数转换为一个指针。该转换通常不进行类型检查，因此潜在地不安全，只应在极少数特殊情况下使用。

4：const_cast 用于在去除变量的 const 修饰符或 volatile 修饰符时使用。它可以将指向常量对象的指针或引用转换为指向非常量对象的指针或引用，或者将指向非常量对象的指针或引用转换为指向常量对象的指针或引用。




