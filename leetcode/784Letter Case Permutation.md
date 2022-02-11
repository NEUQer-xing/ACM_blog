# Letter Case Permutation(����)
## ��Ŀ���⣺
����һ���ַ���S
ͨ�����ַ���S�е�ÿ����ĸת���Сд�����ǿ��Ի��һ���µ��ַ�����
�������п��ܵõ����ַ������ϡ�

[**��Ŀ����:Letter Case Permutation**](https://leetcode-cn.com/problems/letter-case-permutation/)

## ����

���룺S = "a1b2"

�����["a1b2", "a1B2", "A1b2", "A1B2"]

���룺S = "3z4"

�����["3z4", "3Z4"]

���룺S = "12345"

�����["12345"]

��ʾ��
S?�ĳ��Ȳ�����12��
S?�������ֺ���ĸ��ɡ�

## ����
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


