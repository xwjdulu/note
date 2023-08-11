模板函数和模板类有的时候可能需要对传入的不同类型进行不同的处理，比如说有的模板传入int或double类型都可以处理，但是传入char型则会出错，这时就需要模板特化的方式

全特化即将模板类型里的所有类型参数全部具体指明之后处理:
```
template<typename T,typename C>
struct A
{
    A(){cout<<"泛化版本构造函数"<<endl;}
    void func()
    {
        cout<<"泛化版本"<<endl;    
    }
};

template<>
struct A<int,int>
{
   A(){cout<<"int,int特化版本构造函数"<<endl;}
   void func()
   {
       cout<<"int,int特化版本"<<endl;    
   } 
};
```

类模板偏特化（局部特化）：顾名思义，只特殊化几个参数或者一定的参数范围:
```
template<typename T,typename C,typename D>
struct A
{
	void func()
	{
		cout << "泛化版本" << endl;
	}
};
 
template<typename C>
struct A<int,C,int>
{
	void func()
	{
		cout << "int,C,int偏特化版本" << endl;
	}
};
```
***
模板的声明和定义为什么不能分开写，要想分开写该怎么做

不能分开写的原因：

编译器在编译模板时需要知道模板的完整定义，才能根据具体的类型参数生成相应的代码

如果要分开写：

1：声明中包含定义文件，但每次修改定义文件都要重新编译

2：在声明时直接实例化
***
