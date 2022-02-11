# Permutation
## ��Ŀ��
����һ�������ظ����ֵ����� nums �������� ���п��ܵ�ȫ���� ������� ������˳�� ���ش𰸡�

[**��Ŀ���ӣ�46.permutation**](https://leetcode-cn.com/problems/permutations/)

## ������

**ʾ�� 1��**

���룺nums = [1,2,3]
�����[[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]

**ʾ�� 2��**

���룺nums = [0,1]
�����[[0,1],[1,0]]

**ʾ�� 3��**

���룺nums = [1]
�����[[1]]

## �ص���䣺
    �ǳ���Ҫ�ĺ����� ***next_permutation(begin,end)***

## ���룺
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
