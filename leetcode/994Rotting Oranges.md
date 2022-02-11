# 腐烂的橘子（BFS）
## 题目详情
在给定的网格中，每个单元格可以有以下三个值之一：

值?0?代表空单元格；
值?1?代表新鲜橘子；
值?2?代表腐烂的橘子。
每分钟，任何与腐烂的橘子（在 4 个正方向上）相邻的新鲜橘子都会腐烂。

返回直到单元格中没有新鲜橘子为止所必须经过的最小分钟数。如果不可能，返回?-1。
## 题目链接
[题目链接](https://leetcode-cn.com/problems/rotting-oranges/)

## 题目例子
### 示例1：

输入：[[2,1,1],[1,1,0],[0,1,1]]

输出：4

### 示例 2：

输入：[[2,1,1],[0,1,1],[1,0,1]]

输出：-1

解释：左下角的橘子（第 2 行， 第 0 列）永远不会腐烂，因为腐烂只会发生在 4 个正向上。

### 示例 3：

输入：[[0,2]]

输出：0

解释：因为 0 分钟时已经没有新鲜橘子了，所以答案就是 0 。

## 处理的重点环节
- 当输入为[ [0] ]时，说明桌子上也没有正常橘子了，故此时不能返回-1，而应该是返回 time，为0

- **如何处理多个源同时开始感染的计时问题：**

通过记录每次传染源的个数来统计时间，需要用到对列当中
的size()函数

核心代码：
```cpp
if(flag==0)//当标志为0时，说明可以进行下一个感染时期了
{
    flag = 1;
    num = qu.size();
}
num--;
if(num==0)//等到该环节的坏橘子都出队，才可以使time++
{
    flag = 0;
    time++;
}
```

## 代码用时



## 完整代码

```cpp
class Solution {
public:
    int orangesRotting(vector<vector<int>>& grid) {
        int p[4] = {-1,0,0,1};
        int q[4] = {0,-1,1,0};
        struct ZB
        {
            int x;
            int y;
        };
        ZB zb[1000];
        int n=0;
        queue<ZB> qu;
        int health = 0;
        for(int i=0;i<grid.size();i++)
        {
            for(int j=0;j<grid[i].size();j++)
            {
                if(grid[i][j]==2)
                {
                    zb[n].x = i;
                    zb[n].y = j;
                    qu.push(zb[n]);
                    n++;
                }
                else if(grid[i][j]==1)
                {
                    health++;
                }
            }
        }
        ZB t;
        int time=-1;
        int num = 0;
        int flag = 0;
        while(qu.empty()!=1)
        {
            if(flag==0)
            {
                flag = 1;
                num = qu.size();
            }
            num--;
            if(num==0)
            {
                flag = 0;
                time++;
            }
            int xx = qu.front().x;
            int yy = qu.front().y;
            qu.pop();
            for(int i=0;i<4;i++)
            {
                int next_x = xx + p[i];
                int next_y = yy + q[i];
                if(next_x>=0&&next_x<grid.size()&&next_y>=0&&next_y<grid[0].size())
                {
                    if(grid[next_x][next_y]==1)
                    {
                        grid[next_x][next_y] = 2;
                        health--;
                        t.x = next_x;
                        t.y = next_y;
                        qu.push(t);
                    }
                }
            }
        }
        if(health>0)
        {
            return -1;
        }
        else
        {
            if(n==0)
            {
                return 0;
            }
            else
            {
                return time;
            }
        }
    }
};
```


