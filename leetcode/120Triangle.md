# Triangle(三角形最小路径和)动态规划
## 题目：
给定一个三角形 triangle ，找出自顶向下的最小路径和。

每一步只能移动到下一行中相邻的结点上。相邻的结点 在这里指的是 下标 与 上一层结点下标 相同或者等于 上一层结点下标 + 1 的两个结点。也就是说，如果正位于当前行的下标 i ，那么下一步可以移动到下一行的下标 i 或 i + 1 。

[120. 三角形最小路径和](https://leetcode-cn.com/problems/triangle)

## 示例

**示例 1：**

输入：triangle = [[2],[3,4],[6,5,7],[4,1,8,3]]

输出：11

解释：如下面简图所示：
   2
  3 4
 6 5 7
4 1 8 3
自顶向下的最小路径和为?11（即，2?+?3?+?5?+?1?= 11）。

**示例 2：**

输入：triangle = [[-10]]

输出：-10

## 解题思路：

**DP五步法**

**1.确定dp数组及其下标的含义**

    首先，分析题意可以知道要求最小路径和，
    因此我们可以设dp[i][j]来代表
    从第0行开始的到第i行的第j个元素所需要的最短路径和

**2.确定递推公式**

    由题意可得，
    到达第i行第j个元素的最短路径可由
    到达第i-1行的第j-1个元素的最小路径和
    以及到达第i-1行的第j个元素的最小路径和
    取最小后加上本元素的路径值得到
    故有以下公式：
    dp[i][j] = triangle[i][j] + min(dp[i-1][j],dp[i-1][j-1]);

**3.初始化DP数组**

    由2可知，我们无法取得两个边界的dp值，
    例如dp[2][0]与dp[2][2],
    因为根据上述公式结合题目限制条件，
    dp[1][-1]与dp[1][2] 都是不存在的，
    因此我们要单独对这些在边界的dp值进行初始化，
    因为他们仅仅只来源于一种情况
    当然还有dp[0][0]
```cpp
int dp[205][205];//表示从第1行到第i行所经过的最短
dp[0][0] = triangle[0][0];
for(int i=1;i<triangle.size();i++)
{
    dp[i][0] = triangle[i][0] + dp[i-1][0];
}
for(int i=1;i<triangle.size();i++)
{
    dp[i][triangle[i].size()-1] = triangle[i][triangle[i].size()-1] + dp[i-1][triangle[i-1].size()-1];
}
```
**4.确定遍历顺序**

    从顶向下，从左至右依次遍历即可

**5.纠错措施**

    可以输出dp值依次观察是否符合自己的预期


## 代码

```cpp
class Solution {
public:
    int minimumTotal(vector<vector<int>>& triangle) {
        int dp[205][205];//表示从第1行到第i行所经过的最短
        dp[0][0] = triangle[0][0];
        for(int i=1;i<triangle.size();i++)
        {
            dp[i][0] = triangle[i][0] + dp[i-1][0];
        }
        for(int i=1;i<triangle.size();i++)
        {
            dp[i][triangle[i].size()-1] = triangle[i][triangle[i].size()-1] + dp[i-1][triangle[i-1].size()-1];
        }
        for(int i=2;i<triangle.size();i++)
        {
            for(int j=1;j<triangle[i].size()-1;j++)
            {
                dp[i][j] = triangle[i][j] + min(dp[i-1][j],dp[i-1][j-1]);
            }
        }
        int ans = 9999999;
        for(int i=0;i<triangle[triangle.size()-1].size();i++)
        {
           ans = min(ans,dp[triangle.size()-1][i]);
        }
        return ans;
    }
};
```

<font color = red size = 50>第一次独立做出动态规划的题目，继续加油！！！</font>

