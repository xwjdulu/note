
lc2681:  1:求任意子数组，下标没用，有用的是数据大小

2：排序，从小到大的数x，x作为最大数，系数A是能作为最小数的和

3，观察得到：nums[i]每遍历一位，x和y(子数组最小的数)组合的子数组个数就会翻倍：因为多了一个数nums[i-1]选或不选：构造nums[i]和y作为最大最小的子数组
***
lc2763：

认为排序后比之前数大1以上的为目标数

观察数据量：用一个id数组表示一个数在右、在左出现的位置

用rip数组表示右方不含x、x-1的位置
```
int sumImbalanceNumbers(vector<int>& nums) {
    int n = nums.size();
    vector<int>rip(n),id(n+1,n);
    for(int i = n-1;i>=0;i--){
        int x = nums[i];
        rip[i] = min(id[x],id[x-1]);
        id[x] = i;
    }
    int res = 0;
    fill(id.begin(),id.end(),-1);
    for(int i  = 0;i<n;i++){
        int x = nums[i];
        //一个子数组里有多个x，认为最右边位置里那个为目标数，所以求左方没有x-1的位置，右方x-1和x都没有的位置
        res += (i-id[x-1])*(rip[i]-i);  
        id[x] = i; 
    }
    注意：并没有剔除x作为最小值的情况：这个时候其实没有目标数，而每个子数组都有一个最小数
    return res - n*(n+1)/2;
}
```


