# C#���������ܽ�---------List<����>
<table><tr><td bgcolor = yellow ><font face = "����" size = 6 color = red >�����ܽ����£�</font></table></tr></td>

## List<����>  (�൱��C++�е� vector<����>)

### 1.���� List<>

```cs
    List<����> ���� = new List<����>();
    
    //���磺

    List<int> nums = new List<int>();
```
### 2.���Ԫ��
- һ��Ԫ��
```cs
    List.Add(element)�� 
    
    //���磺

    List<string> mList = new List<string>();

    mList.Add("John");
```
- ���һ��Ԫ��
```cs
    List.AddRange(a group of element)
    
    //���磺

    List<string> mList = new List<string>();

    string[] temArr = { "Ha","Hunter", "Tom", "Lily", "Jay", "Jim", "Kuku",  "Locu" };

    mList.AddRange(temArr);   
```
- ��indexλ�ò���Ԫ��
```cs
    List.Insert(index, element);

    //���磺

    List<string> mList = new List<string>();

    mList.Insert(2, "Hei");
```
- ����Ԫ��
    ������for()+index
    Ҳ������foreach()
```cs
    foreach (T element in mList)  //T��������mList����ʱһ��
    {
        Console.WriteLine(element);
    }
```
## 3.ɾ��Ԫ��
- ɾ��һ��Ԫ��
```cs
    List. Remove(element)

    //���磺

    mList.Remove("Hunter");
```
- ɾ���±�Ϊindex��Ԫ��
```cs
    List. RemoveAt(index);   

    //���磺

    mList.RemoveAt(0);
```

- ���±�index��ʼ��ɾ��count��Ԫ��
```cs
    List. RemoveRange(index, count);

    //���磺

    mList.RemoveRange(3, 2);
```
## 4.����Ԫ��
- �ж��Ƿ���List�У�����true/false
```cs
    List.Contains(element);

    //����

     if (mList.Contains("Hunter"))
    {
        Console.WriteLine("There is Hunter in the list");
    }
    else
    {
        mList.Add("Hunter");
        Console.WriteLine("Add Hunter successfully.");
    }
```
## 5.���� 
```cs
    List.Sort();//��������

    List.Sort();
    List.Reverse(); //��������
```
## 6.���List
```cs
    List.Clear();
```
## 7.���List��Ԫ�ص�����
```cs
    List.Count();

    //���磺

    int count = mList.Count();

    Console.WriteLine("The num of elements in the list: " +count); 

```




