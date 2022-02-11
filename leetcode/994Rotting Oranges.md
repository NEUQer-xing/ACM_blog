# ���õ����ӣ�BFS��
## ��Ŀ����
�ڸ����������У�ÿ����Ԫ���������������ֵ֮һ��

ֵ?0?����յ�Ԫ��
ֵ?1?�����������ӣ�
ֵ?2?�����õ����ӡ�
ÿ���ӣ��κ��븯�õ����ӣ��� 4 ���������ϣ����ڵ��������Ӷ��ḯ�á�

����ֱ����Ԫ����û����������Ϊֹ�����뾭������С����������������ܣ�����?-1��
## ��Ŀ����
[��Ŀ����](https://leetcode-cn.com/problems/rotting-oranges/)

## ��Ŀ����
### ʾ��1��

���룺[[2,1,1],[1,1,0],[0,1,1]]

�����4

### ʾ�� 2��

���룺[[2,1,1],[0,1,1],[1,0,1]]

�����-1

���ͣ����½ǵ����ӣ��� 2 �У� �� 0 �У���Զ���ḯ�ã���Ϊ����ֻ�ᷢ���� 4 �������ϡ�

### ʾ�� 3��

���룺[[0,2]]

�����0

���ͣ���Ϊ 0 ����ʱ�Ѿ�û�����������ˣ����Դ𰸾��� 0 ��

## ������ص㻷��
- ������Ϊ[ [0] ]ʱ��˵��������Ҳû�����������ˣ��ʴ�ʱ���ܷ���-1����Ӧ���Ƿ��� time��Ϊ0

- **��δ�����Դͬʱ��ʼ��Ⱦ�ļ�ʱ���⣺**

ͨ����¼ÿ�δ�ȾԴ�ĸ�����ͳ��ʱ�䣬��Ҫ�õ����е���
��size()����

���Ĵ��룺
```cpp
if(flag==0)//����־Ϊ0ʱ��˵�����Խ�����һ����Ⱦʱ����
{
    flag = 1;
    num = qu.size();
}
num--;
if(num==0)//�ȵ��û��ڵĻ����Ӷ����ӣ��ſ���ʹtime++
{
    flag = 0;
    time++;
}
```

## ������ʱ



## ��������

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


