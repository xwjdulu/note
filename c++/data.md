decltype与auto关键字一样，用于进行编译时类型推导。
decltype实际上有点像auto的反函数，auto可以让你声明一个变量，而decltype则可以从一个变量或表达式中得到类型，例如：
int x = 3;  
decltype(x) y = x; 
有人会问，decltype的实用之处在哪里呢，假如有一个加工产品的函数模板：

template <typename Creator>  
void processProduct(const Creator& creator) {  
    auto val = creator.makeObject();  
    // do somthing with val  
} 
如果这个函数模板想把加工的产品作为返回值，该怎么办呢？我们可以这样写：
template <typename Creator>  
auto processProduct(const Creator& creator) -> decltype(creator.makeObject()) {  
    auto val = creator.makeObject();  
    // do somthing with val  
    return val;
} 

 vector.insert(arr.begin(), -1);
 位移运算优先于逻辑位运算

 str.resize(k,c);c: 如果k大于字符串的长度，则c是要在新空格中添加的新字符。这是可选参数。

 memset,iota初始化

 static_cast是指显性类型强制转换，如：
int  a = static_cast<int>(120.34);
unique的作用是“去掉”容器中相邻元素的重复元素

在std::array中，提供了2种访问元素的方法：[]和at()
[]不会检查索引值是否越界    arr[5]
at()会检查，一旦越界，将抛出std::out_of_range的异常   arr.at(5)

std::get<n>()是一个辅助函数，它能够获取到容器的第 n 个元素。

set的分析结果也类似，bookSet.insert(SBook("十万个为什么",1)) 这个语句执行了两次构造，一次析构。而 bookSet.emplace("新华字典", 2) 语句只执行了一次构造。

isalpha() / isdigit() / isalnum() / islower() / isupper()参数为字符型变量，分别用于判断字符是否为字母 / 数字(注意是字符型) / 字母或数字 / 小写字母 / 大写字母。如果是，返回非0；如果不是，返回0。

c.rbegin() 返回一个逆序迭代器，它指向容器c的最后一个元素
c.rend() 返回一个逆序迭代器，它指向容器c的第一个元素前面的位置

