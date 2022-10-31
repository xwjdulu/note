序列化：
剑指 Offer 37         652 寻找重复的子树
第一种方法是使用层序遍历的方法进行序列化

第二种方法是使用递归的方法进行序列化
x(左子树的序列化结果)(右子树的序列化结果)

第三种使用三元组进行唯一表示，即 (x, l, r)，它们分别表示：根节点的值为 x；左子树的序号为 l；右子树的序号为r。

constexpr表示这玩意儿在编译期就可以算出来（前提是为了算出它所依赖的东西也是在编译期可以算出来的）。而const只保证了运行时不直接被修改（但这个东西仍然可能是个动态变量）。

explicit为清晰的;明确的之意.顾名思义,关键字explicit可以阻止隐式转换的发生
implicit

size_t是一些C/C++标准在stddef.h中定义的，size_t类型表示C中任何对象所能达到的最大长度，它是无符号整数。

线段树：一个节点下标为i，父节点为(i-1)/2,左子树为2*i+1,右子树为2*i+2,
总为完全二叉树，叶节点总为[x,x],根节点下标为0；
根节点区间[0,a],左节点区间[0,a/2]
每个结点保存数组 \textit{nums}nums 在区间 [s, e][s,e] 的最小值、最大值或者总和等信息。
若原数组nums的长度为n，线段树深度h应为⌈log2^n + 1 ⌉ 
则该完全二叉树的数组长度应为2^(h+1)<=4*n
    void build(int s,int e,int index){
        if(s == e){
            segtree[index] = ori[s];
            return ;
        }
        int mid = s+(e-s)/2;
        build(s,mid,index*2+1);
        build(mid+1,e,index*2+2);
        segtree[index] = segtree[index*2+1]+segtree[index*2+2];
        return;
    }
    index 代表线段树数组下标，s和e代表区间范围
线段树：懒操作：set。emplace某个树节点，代表这个区间内都需要变化

前序：
vector<int> preorderTraversal(TreeNode* root) {
    vector<int> ans;
    stack<TreeNode*> stk;
    stk.push(root);
    while (stk.size()) {
        auto t = stk.top();
        stk.pop();
        if (!t) continue;
        ans.push_back(t->val);
        stk.push(t->right);
        stk.push(t->left);
    }
    return ans;
}
后序：
    while(!st.empty() || root){
        if(root){
            st.push(root);
            root = root->left;
        }
        else{
            root = st.top();
            st.pop();
            k--;
            if(k == 0)
                return root->val;
            root = root->right;
        }
    }
注意栈的顺序

树状数组：
每个二进制的最后一位的大小表示了原本数组的长度和
所以树状数组下标从1开始
    void add(int pos){
        while(pos<vc.size()){
            vc[pos]++;
            pos += pos & (-pos);
        }
    }

    int query(int pos){
        int ret = 0;
        while(pos>0){
            ret += vc[pos];
            pos -= pos & (-pos); 
        }
        return ret;
    }

