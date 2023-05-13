auto的限制

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