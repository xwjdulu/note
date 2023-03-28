template<typename T>
void func(T a, T b){
    T c;
    return; 
}
可以指定T，具体的模板

模板类的成员函数可以在类外实现
<T=数据类型>可以缺省

用户在实例化一个 priority_queue 时，必须为元素类型（class T）重载<运算符，以用于元素排序！
struct Ratio {
        int pass, total;
        bool operator < (const Ratio& oth) const {
            return (long long) (oth.total + 1) * oth.total * (total - pass) < (long long) (total + 1) * total * (oth.total - oth.pass);
        }
    };
priority_queue<Ratio> q;

struct node{
    int x;
    int y;
};
bool operator< (node a, node b) {
	//return a.y < b.y; //大根堆
    //return a.y > b.y; //小根堆
}
priority_queue<node> prque;

struct cmp //重写仿函数
{
	bool operator() (node a, node b)
	{
		//return a.y < b.y; //大根堆
        //return a.y > b.y; //小根堆
	}
};	
priority_queue<node,vector<node>,cmp> prque;