![success.jpg](https://pic.leetcode-cn.com/1649131816-tGmefr-success.jpg)

# 思路一：利用C++中的accumulate函数
## 思路：
---

c++ STL中的accumulate（）函数

accumulate定义在#include<numeric>中，作用有两个，一个是累加求和，另一个是自定义类型数据的处理

主要作用是求和：一是求数字数组的和，二是将字符型数组转变为string类型

例如：

`int sum = accumulate(vec.begin() , vec.end() , 0);  `

accumulate带有三个形参：头两个形参指定要累加的元素范围，第三个形参则是累加的初值。

accumulate函数将它的一个内部变量设置为指定的初始值，然后在此初值上累加输入范围内所有元素的值。

accumulate算法返回累加的结果，其返回类型就是其第三个实参的类型。

**可以使用accumulate把string型的vector容器中的元素连接起来：**

`string sum = accumulate(v.begin() , v.end() , string(" "));  `

这个函数调用的效果是：从空字符串开始，把vec里的每个元素连接成一个字符串。

---
## 代码
```cpp
class NumArray {
public:
  vector<int> temp;
  int sum = 0;
  NumArray(vector<int> &nums) {
    temp = nums;
    sum = accumulate(temp.begin(), temp.end(), 0);
  }

  void update(int index, int val) {
    sum = sum - temp[index];
    temp[index] = val;
    sum = sum + temp[index];
  }

  int sumRange(int left, int right) {
    return sum - accumulate(temp.begin(), temp.begin() + left, 0) -
           accumulate(temp.begin() + right + 1, temp.end(), 0);
  }
};
```

# 思路二：线段树
将数组与前缀和统筹起来的方法，可以实现在多次修改和多次计算区间和的时间复杂度下降至$\log(n)$
[推荐视频，讲解线段树特别清晰，看一遍基本就能懂了，今天又新学了个知识，哈哈哈](https://www.bilibili.com/video/BV1cb411t7AM?spm_id_from=333.880.my_history.page.click)
```cpp
class NumArray {
public:

    NumArray(vector<int>& nums) {
        nt = nums;
        build_tree(0,nt.size()-1,0);
        // for(int i = 0; i < 3; i++)
        // {
        //     cout<<tree[i]<<' ';
        // }
    }
    
    void update(int index, int val) {
        int start = 0;
        int end = nt.size() - 1;
        updatee(start,end,0,val,index);
        // cout<<endl;
        // for(int i = 0; i < 3; i++)
        // {
        //     cout<<tree[i]<<' ';
        // }
        // cout<<endl;
    }
    
    int sumRange(int left, int right) {
        int start = 0;
        int end = nt.size() - 1;
        return summ(start,end,0,left,right);
    }

    void build_tree(int start,int end,int node)
    {
        if(start==end)
        {
            tree[node] = nt[start];
            return ;
        }
        int node_left = node * 2 + 1;
        int node_right = node * 2 + 2;
        int mid = (start + end) / 2;
        build_tree(start,mid,node_left);
        build_tree(mid+1,end,node_right);
        tree[node] = tree[node_left] + tree[node_right];
        return ;
    }
    void updatee(int start,int end,int node,int val, int index)
    {
        if(start==end)
        {
            tree[node] = val;
            nt[index] = val;
            return ;
        }
        int mid = (start + end)  / 2;
        int node_left = node * 2 + 1;
        int node_right = node * 2 + 2;
        if(index>=start&&index<=mid)
        {
            updatee(start,mid,node_left,val,index);
        }
        else if(index>mid&&index<=end)
        {
            updatee(mid+1,end,node_right,val,index);
        }
        tree[node] = tree[node_left] + tree[node_right];
        return ;
    }
    int summ (int start,int end,int node,int L,int R)
    {
        // cout<<"start:"<<start<<endl;
        // cout<<"end:"<<end<<endl;
        if(end<L||start>R)
        {
            return 0;
        }
        else if(L<=start&&R>=end)
        {
            return tree[node];
        }
        else if(start==end)
        {
            return tree[node];
        }
        
        int mid = (start + end) / 2;
        int node_left = node * 2 + 1;
        int node_right = node * 2 + 2;
        return summ(start,mid,node_left,L,R)+summ(mid+1,end,node_right,L,R);
    }
private:
    vector<int> nt;
    int tree[5000000];
};

/**
 * Your NumArray object will be instantiated and called as such:
 * NumArray* obj = new NumArray(nums);
 * obj->update(index,val);
 * int param_2 = obj->sumRange(left,right);
 */
```