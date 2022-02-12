# C#���������ܽ�---------Hash��
<table><tr><td bgcolor = yellow ><font face = "����" size = 6 color = red >�����ܽ����£�</font></table></tr></td>

## Hash�� (�൱��C++�е� map<���ͣ����͡�������>)

## һ��Dictionary<Type,Type>
- Dictionary�����ÿһ��Ԫ�ض���һ����ֵ��(�ɶ���Ԫ����ɣ�����ֵ)
- ��������Ψһ��,��ֵ����ҪΨһ��
- ����ֵ���������κ�����(���磺string, int, �Զ������ͣ��ȵ�)
- ͨ��һ������ȡһ��ֵ��ʱ���ǽӽ�O(1)

<font face = "����" size = 6 color = red >Dictionary��HashTable����</font>

### 1.����
```cs
    Dictionary<string, string> openWith = new Dictionary<string, string>();
```

### 2.���Ԫ��
```cs
    //���Ԫ��
    openWith.Add("txt", "notepad.exe");
    openWith.Add("bmp", "paint.exe");
    openWith.Add("dib", "paint.exe");
    openWith.Add("rtf", "wordpad.exe");
```
### 3.��key��value,����ֵ
```cs
    Console.WriteLine(openWith["rtf"]);

    //����ֵ

    openWith["rtf"] = "winword.exe";
```
### 4.����
- ����key
```cs
    foreach (string key in openWith.Keys)
    {
        Console.WriteLine("Key = {0}", key);
    }
```
- ����value
```cs
     //����value
    foreach (string value in openWith.Values)
    {
        Console.WriteLine("value = {0}", value);
    }
```
- �����ֵ�
```cs
    foreach (KeyValuePair<string, string> kvp in openWith)
    {
        Console.WriteLine("Key = {0}, Value = {1}", kvp.Key, kvp.Value);
    }
```
### 5.�ж�key�Ƿ����
```cs
//�жϼ�����
    if (openWith.ContainsKey("bmp")) // True 
    {
        Console.WriteLine("An element with Key = + bmp + exists.");
    }
```
