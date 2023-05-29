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
