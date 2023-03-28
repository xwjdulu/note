有unordered_map和unordered_set这两个数据结构，其内部实现是哈希表，这就要求作为键值的类型必须是可哈希的，
比如常见的数据类型int、string等
想让pair<int,int>作为unorderd_map的键值，需要编写两个类，每个类中分别包含一个函数，第一个类中的函数叫做哈希函数，将某一个pair<int,int>的对象哈希了，返回其哈希值；第二个叫做相等函数，用于判断两个pair<int,int>对象是否相等，意在解决冲突。
struct Hashfunc {
    size_t operator() (const pair<int,int>& key) const{
        return hash<int>()(key.first) ^ hash<int>()(key.second);
    }
};
struct Equalfunc {
    bool operator() (const pair<int,int>& a, const pair<int,int>& b) const{
        return a.first == b.first && a.second == b.second;
    }
};
最后：
unordered_map<pair<int,int>, int, Hashfunc, Equalfunc> mp;

增强型for循环不能增删，Java原理：在for each中生成迭代器，modcount(操作次数已经确定)
function<void()> precompute = [&](){...}; 对于一般的lambda表达式来说，二者使用差异不大，但是对于存在递归的lambda表达式来说，使用auto precompute =[&](){...};会出现问题

vector<int> a(nums.begin(), nums.end());