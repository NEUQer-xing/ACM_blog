# SimplifyPath (c++�е�split)

**<font color = red size = 15 >����C++��getline()�Լ�istringstreamʵ�����������е�split����**</font>

## ��Ŀ
����һ���ַ��� path ����ʾָ��ĳһ�ļ���Ŀ¼��?Unix ��� ����·�� ���� '/' ��ͷ�������㽫��ת��Ϊ���Ӽ��Ĺ淶·����

�� Unix �����ļ�ϵͳ�У�һ���㣨.����ʾ��ǰĿ¼�������⣬������ ��..��?��ʾ��Ŀ¼�л�����һ����ָ��Ŀ¼�������߶������Ǹ������·������ɲ��֡�������������б�ܣ�����'//'��������Ϊ����б�� '/' �� ���ڴ����⣬�κ�������ʽ�ĵ㣨���磬'...'��������Ϊ�ļ�/Ŀ¼���ơ�

��ע�⣬���ص� �淶·�� ������ѭ������ʽ��

ʼ����б�� '/' ��ͷ��
����Ŀ¼��֮�����ֻ��һ��б�� '/' ��
���һ��Ŀ¼����������ڣ����� �� '/' ��β��
���⣬·���������Ӹ�Ŀ¼��Ŀ���ļ���Ŀ¼��·���ϵ�Ŀ¼���������� '.' �� '..'����
���ؼ򻯺�õ��� �淶·�� ��

[��Ŀ���ӣ�SimplifyPath](https://leetcode-cn.com/problems/simplify-path)


**ʾ�� 1��**

���룺path = "/home/"

�����"/home"

���ͣ�ע�⣬���һ��Ŀ¼������û��б�ܡ� 

**ʾ�� 2��**

���룺path = "/../"

�����"/"

���ͣ��Ӹ�Ŀ¼����һ���ǲ����еģ���Ϊ��Ŀ¼������Ե������߼���

**ʾ�� 3��**

���룺path = "/home//foo/"

�����"/home/foo"

���ͣ��ڹ淶·���У��������б����Ҫ��һ��б���滻��

**ʾ�� 4��**

���룺path = "/a/./b/../../c/"

�����"/c"
?

**��ʾ��**

1 <= path.length <= 3000
path ��Ӣ����ĸ�����֣�'.'��'/' �� '_' ��ɡ�
path ��һ����Ч�� Unix ������·����

## getline():�������

getline()��ԭ����

<font size = 5>**istream& getline ( istream &is , string &str , char delim );**</font>

- ���� istream &is ��ʾһ����������Ʃ��cin��
- string&str��ʾ�Ѵ�������������ַ������������ַ����У������Լ����������strʲô�Ķ����ԣ���
- **char delim��ʾ��������ַ�ֹͣ����**���ڲ����õ������ϵͳĬ�ϸ��ַ�Ϊ'\n'��Ҳ���ǻس����з��������س�ֹͣ���룩��

## istringstream sin(s)

istringstream�Ĺ��캯��ԭ�����£�

- <font size = 5> **istringstream::istringstream(string str);**

  <font color = red> ���������Ǵ�string����str�ж�ȡ�ַ���</font>

```cpp
#include<iostream>  
#include<sstream>        //istringstream ����������ͷ�ļ�
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

## ˼·
    ���� / Ϊ�ָ�������ַ����ָ�������ַ������ļ�������
    ������Щ�ַ�����
    ������������ļ�����ֱ����ջ��
    �����".."����ջ��Ԫ�أ�
    �����'.'���ù�����
    ������ٱ���ջ������ջ��Ԫ�ز��뵽�����ַ�����ͷ��ͬʱ����'/'��

�ο������۵�����

## ����

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

