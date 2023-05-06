在 C++ STL 中，不同于有序的 std::map 和 std::set 是基于红黑树实现的，std::unordered_map 和 std::unordered_set 是基于哈希实现的

set可以存放pair

对于没有默认的哈希函数的类型，如自定义的 class 类型，pair 类型等，我们就必须自己指定一个哈希函数。这也是为什么直接构建 pair 类型的 unordered_set 如 unordered_set<pair<int, int>> uset 会出现问题 
***
自定义哈希函数
```
struct myhash
{
    std::size_t operator()(pi const& a) const 
    {
        return a.first ^ a.second;
    }
};
int main(){
    unordered_set<pi,myhash>s;
    s.insert({1,2});
    int a;
    return 0;
}
```
***

