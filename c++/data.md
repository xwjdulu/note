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