# Permutation
## 题目：
给定一个不含重复数字的数组 nums ，返回其 所有可能的全排列 。你可以 按任意顺序 返回答案。

[**题目链接：46.permutation**](https://leetcode-cn.com/problems/permutations/)

## 样例：

**示例 1：**

输入：nums = [1,2,3]
输出：[[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]

**示例 2：**

输入：nums = [0,1]
输出：[[0,1],[1,0]]

**示例 3：**

输入：nums = [1]
输出：[[1]]

## 重点记忆：
    非常重要的函数： ***next_permutation(begin,end)***

## 代码：
```cpp
class Solution {
public:
    vector<vector<int>> permute(vector<int>& nums) {
        vector<int> x;
        vector<vector<int>> ans;
        sort(nums.begin(),nums.end());
        do
        {
            ans.push_back(nums);
        }while(next_permutation(nums.begin(),nums.end()));
        return ans;
    }
};
```
