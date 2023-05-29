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
#decltype 推导的表达式可简单可复杂，在这一点上 auto 是做不到的，auto 只能推导已初始化的变量类型。

