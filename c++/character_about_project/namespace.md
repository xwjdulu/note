命名空间： 解决名称冲突
namespace name1
{
	int a = 0;
	int Add(int left, int right)
	{
		return left + right;
	}
    namespace sonname1{        //命名空间嵌套
        int b;
    }
}
同一个工程中允许存在多个同名命名空间，比如上面代码在file1.cpp中，我在file2.cpp还可以
namespace name1{
    int d;
}

命名空间的3种使用方式 1,加命名空间名称及作用域限定符   N::a
2,用using将命名空间成员或函数引入 using namespca N::a       3,using namespace N; 命名空间名称引入


