# C#���������ܽ�---------Tuple<���ͣ���������>
<table><tr><td bgcolor = yellow ><font face = "����" size = 6 color = red >�����ܽ����£�</font></table></tr></td>

## Tuple<����,����>  (�൱��C++�е� pair<����,��>)

### 1.����
```cs
    Tuple<���ͣ�����> ���� = new Tuple<���ͣ�����>(element1��element2);

    //���磺

    //һ��Ԫ�ص�Ԫ��
    Tuple<int> test = new Tuple<int>(34);
 
    //����Ԫ�ص�Ԫ�� 1<n<8
    Tuple<string, int> test2 = Tuple.Create<string, int>("str", 2);
    Tuple<int, int> test2_1 = new Tuple<int, int>(2,2);

```

### 2.��ȡԪ���ڵ�ֵ
    Ԫ��Ԫ�ؿ���ͨ�� Item < elementnumber > ���Է���
    
    ���� Item1�� Item2�� Item3�ȣ������Է��� Item7���ԡ�
    
    Item1���Է��ص�һ��Ԫ�أ�Item2���صڶ���Ԫ�أ��������ơ�
    
```cs
    Tuple<int, string, string> person = new Tuple <int, string, string>(1, "Steve", "Jobs");
    person.Item1; // ���� 1
    person.Item2; // ���� "Steve"
    person.Item3; // ���� "Jobs"    
```

