```
auto cmp = [&](const pi &a,const pi &b){
    return nums1[a.first] + nums2[a.second] > nums1[b.first] + nums2[b.second];
};
priority_queue<pi,vector<pi>,decltype(cmp)>pq(cmp);
```
1:decltype:因为这里需要的参数是类型，而非实例对象，lambdaCompare 很明显是一个实例对象，就像auto x = 1;，x是一个实例对象，int 才是类型

2: pq内部排序比较的时候要使用的是一个实例化的lambda对象，只能通过lambda的 copy构造进行实例化，从哪里copy呢，就需要pq构造函数的时候传入这个lambda对象。pq的自定义比较也可以使用struct或者class，因为struct和class都有默认构造函数，此时就不需要pq(Type) 而是直接pq即可。同理，自定义比较也可以使用函数，同样此时也需要提供函数对象进行实例化pq(CmpFunc)，假设比较函数为bool CmpFunc(int x, int y) {return x < y;} 

3：就好比你写一个类： class A { public: int a ; A() { a = 0; } A(int x) { a = x; } } 在实例化类A的时候，你传了参数就调用第二个构造函数，否则就是第一个
***
```
auto &x = pq.top();
pq.pop();
```
这个引用指向的是堆顶而不是pop出去的元素
***
