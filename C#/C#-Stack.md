# C#常用容器总结---------Stack<类型>
<table><tr><td bgcolor = yellow ><font face = "黑体" size = 6 color = red >现在总结如下：</font></table></tr></td>

## Stack<类型>  (相当于C++中的 stack<类型>)

### 1. 创建Stack
```cs
    Stack<类型> 名字 = new Stack<类型>();

    //例如：

     Stack<Tuple<int, int>> st = new Stack<Tuple<int, int>>();
```

### 2. 添加元素
- 在栈顶添加一个元素
```cs
    Stack.Push(element);

    // 例如：

    Stack st = new Stack();

    st.Push('A');

```
### 3. 读取栈顶元素
- 在读取之后就删除它
```cs
    element = Stack.Dequeue();

    // 例如：

    Stack st = new Stack();

    st.Push('A');

    char c;
    
    c = st.Pop();
```
- 只读取，不删除
```cs
    element = Stack.Peek();

    // 例如：

    Stack st = new Stack();

    st.Push('A');

    char c;
    
    c = st.Peek();
```

### 4. 判断一个元素是否在堆栈中
```cs
    Stack.Contains(element);//返回true/false

    //例如

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
## 5.清空Queue
```cs
    Stack.Clear();
```
## 7.获得Queue中元素的数量
```cs
    Stack.Count();

    //例如：

    int count = st.Count();

    Console.WriteLine("The num of elements in the stack: " +count); 

```