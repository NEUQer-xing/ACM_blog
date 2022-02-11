# Letter Case Permutation(回溯)
## 题目大意：
给定一个字符串S
通过将字符串S中的每个字母转变大小写，我们可以获得一个新的字符串。
返回所有可能得到的字符串集合。

[**题目链接:Letter Case Permutation**](https://leetcode-cn.com/problems/letter-case-permutation/)

## 样例

输入：S = "a1b2"

输出：["a1b2", "a1B2", "A1b2", "A1B2"]

输入：S = "3z4"

输出：["3z4", "3Z4"]

输入：S = "12345"

输出：["12345"]

提示：
S?的长度不超过12。
S?仅由数字和字母组成。

## 代码
```cpp
class Solution {
public:
    vector<string> ans;
    void back(string s,int i)
    {
        if(i==s.length())
        {
            ans.push_back(s);
            return ;
        }
        if(s[i]>='0'&&s[i]<='9')
        {
            back(s,i+1);
        }
        else
        {
            back(s,i+1);
            s[i] = s[i] - 'a' + 'A';
            back(s,i+1);
        }
    }
    vector<string> letterCasePermutation(string s) {
        for(int i=0;i<s.length();i++)
        {
            if(s[i]>='A'&&s[i]<='Z')
            {
                s[i] = s[i] - 'A' + 'a'; 
            }
        }
        back(s,0);
        return ans;
    }
};
```


