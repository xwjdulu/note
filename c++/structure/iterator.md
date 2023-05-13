注意，insert接收返回值指向插入元素位置，否则原元素位置：插入元素后n位   
```
list<int>a,b;
    auto ita = a.begin(),itb = b.begin();
    for(int i = 1;i<4;i++){
        a.insert(ita,i); 
        cout<<*ita<<" ";
        auto t = ita;
        int s= 0;
        while(t!=a.begin()){
            s++;
            t--;
        }
        cout<<s<<" ";
    }
    for(int i = 1;i<4;i++){
        itb = b.insert(itb,i); 
        cout<<*itb<<" ";
        auto t = itb;
        int s= 0;
        while(t!=b.begin()){
            s++;
            t--;
        }
        cout<<s<<" ";
    }
```
***
new_iterator = prev(iterator，n)

当“n“为正数时，返回传入迭代器“iterator”左边，距离”iterator“ n个单位的迭代器”new_iterator“。

当“n“为负数时，返回传入迭代器“iterator”右边，距离”iterator“ n个单位的迭代器"new_iterator"。

new_iterator = prev(iterator)

