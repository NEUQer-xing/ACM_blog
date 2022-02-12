# C#���������ܽ�---------Stack<����>
<table><tr><td bgcolor = yellow ><font face = "����" size = 6 color = red >�����ܽ����£�</font></table></tr></td>

## Stack<����>  (�൱��C++�е� stack<����>)

### 1. ����Stack
```cs
    Stack<����> ���� = new Stack<����>();

    //���磺

     Stack<Tuple<int, int>> st = new Stack<Tuple<int, int>>();
```

### 2. ���Ԫ��
- ��ջ�����һ��Ԫ��
```cs
    Stack.Push(element);

    // ���磺

    Stack st = new Stack();

    st.Push('A');

```
### 3. ��ȡջ��Ԫ��
- �ڶ�ȡ֮���ɾ����
```cs
    element = Stack.Dequeue();

    // ���磺

    Stack st = new Stack();

    st.Push('A');

    char c;
    
    c = st.Pop();
```
- ֻ��ȡ����ɾ��
```cs
    element = Stack.Peek();

    // ���磺

    Stack st = new Stack();

    st.Push('A');

    char c;
    
    c = st.Peek();
```

### 4. �ж�һ��Ԫ���Ƿ��ڶ�ջ��
```cs
    Stack.Contains(element);//����true/false

    //����

     if (st.Contains("Hunter"))
    {
        Console.WriteLine("There is Hunter in the stack");
    }
    else
    {
        st.Enqueue("Hunter");
        Console.WriteLine("Add Hunter successfully.");
    }
```
## 5.���Queue
```cs
    Stack.Clear();
```
## 7.���Queue��Ԫ�ص�����
```cs
    Stack.Count();

    //���磺

    int count = st.Count();

    Console.WriteLine("The num of elements in the stack: " +count); 

```