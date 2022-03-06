# SimplifyPath (c++中的split)

**<font color = red size = 15 >利用C++的getline()以及istringstream实现其它语言中的split函数**</font>

## 题目
给你一个字符串 path ，表示指向某一文件或目录的?Unix 风格 绝对路径 （以 '/' 开头），请你将其转化为更加简洁的规范路径。

在 Unix 风格的文件系统中，一个点（.）表示当前目录本身；此外，两个点 （..）?表示将目录切换到上一级（指向父目录）；两者都可以是复杂相对路径的组成部分。任意多个连续的斜杠（即，'//'）都被视为单个斜杠 '/' 。 对于此问题，任何其他格式的点（例如，'...'）均被视为文件/目录名称。

请注意，返回的 规范路径 必须遵循下述格式：

始终以斜杠 '/' 开头。
两个目录名之间必须只有一个斜杠 '/' 。
最后一个目录名（如果存在）不能 以 '/' 结尾。
此外，路径仅包含从根目录到目标文件或目录的路径上的目录（即，不含 '.' 或 '..'）。
返回简化后得到的 规范路径 。

[题目链接：SimplifyPath](https://leetcode-cn.com/problems/simplify-path)


**示例 1：**

输入：path = "/home/"

输出："/home"

解释：注意，最后一个目录名后面没有斜杠。 

**示例 2：**

输入：path = "/../"

输出："/"

解释：从根目录向上一级是不可行的，因为根目录是你可以到达的最高级。

**示例 3：**

输入：path = "/home//foo/"

输出："/home/foo"

解释：在规范路径中，多个连续斜杠需要用一个斜杠替换。

**示例 4：**

输入：path = "/a/./b/../../c/"

输出："/c"
?

**提示：**

1 <= path.length <= 3000
path 由英文字母，数字，'.'，'/' 或 '_' 组成。
path 是一个有效的 Unix 风格绝对路径。

## getline():函数简介

getline()的原型是

<font size = 5>**istream& getline ( istream &is , string &str , char delim );**</font>

- 其中 istream &is 表示一个输入流，譬如cin；
- string&str表示把从输入流读入的字符串存放在这个字符串中（可以自己随便命名，str什么的都可以）；
- **char delim表示遇到这个字符停止读入**，在不设置的情况下系统默认该字符为'\n'，也就是回车换行符（遇到回车停止读入）。

## istringstream sin(s)

istringstream的构造函数原形如下：

- <font size = 5> **istringstream::istringstream(string str);**

  <font color = red> 它的作用是从string对象str中读取字符。</font>

```cpp
#include<iostream>  
#include<sstream>        //istringstream 必须包含这个头文件
#include<string>  
using namespace std;  
int main()  
{  
    string str="i am a boy";  
    istringstream is(str);  
    string s;  
    while(is>>s)  
    {  
        cout<<s<<endl;  
    }    
} 
```

## 思路
    先以 / 为分割符，将字符串分割成许多个字符串（文件名），
    遍历这些字符串，
    如果是正常的文件名就直接入栈，
    如果是".."弹出栈顶元素，
    如果是'.'不用管他，
    到最后再遍历栈，将出栈的元素插入到返回字符串的头上同时加上'/'。

参考了评论的内容

## 代码

```cpp
class Solution {
public:
    string simplifyPath(string path) {
        istringstream sin(path);
        string name;
        stack<string> st;
        while(getline(sin,name,'/'))
        {
            if(name==""||name==".")
            {
                continue;
            }
            else if(name=="..")
            {
                if(st.empty()!=1)
                {
                    st.pop();
                }
            }
            else
            {
                st.push(name);
            }
        }
        string ans = "";
        if(st.empty()==1)
        {
            ans = "/";
        }
        else
        {
            while(st.empty()!=1)
            {
                ans = "/" + st.top() + ans;
                st.pop();
            }
        }
        return ans;
    }
};
```

