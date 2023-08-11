#关于const
```
const ll m = 1e18;
for(ll i = 2;i<1e6;i++){
        ll cur = i*i;
        ll sum = cur+i+1;
        while(sum<m){
            s.insert(sum);
            /*
            if(cur>(m/i))
                break;
            */
            cur *= i;
            sum += cur; 
        } 
    }
```  
需要加注释，否则溢出死循环，比如cur = 1e17,i = 1e5;  
***
const成员函数：不能修改成员变量
***
常量与指针
```
const *int p1 = &a          //常量指针 ，地址可变，值不变
* int const p2 = &b;            //指针常量，地址不变，值可变
```
对于const 和 * ： 谁在前就先读，谁在前就不可改变     
***
哈希冲突4种解决：

1.再次散列，找到新地址直到不冲突

2.链式地址，哈希地址以链表形式可以存储多value

3.建立溢出区

4.多哈希函数
***

