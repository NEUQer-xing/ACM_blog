# C#常用容器总结---------Queue<类型>
<table><tr><td bgcolor = yellow ><font face = "黑体" size = 6 color = red >现在总结如下：</font></table></tr></td>

## Queue<类型>  (相当于C++中的 queue<类型>)

### 1. 创建Queue
```cs
    Queue<类型> 名字 = new Queue<类型>();

    //例如：

     Queue<Tuple<int, int>> qu = new Queue<Tuple<int, int>>();
```

### 2. 添加元素
- 在队列末尾添加一个元素
```cs
    Queue.Enqueue(element);

    // 例如：

    Queue qu = new Queue();

    qu.Enqueue('A');

```
### 3. 读取头部元素
- 在读取之后就删除它
```cs
    element = Queue.Dequeue();

    // 例如：

    Queue qu = new Queue();

    qu.Enqueue('A');

    char c;
    
    c = qu.Dequeue();
```
- 只读取，不删除
```cs
    element = Queue.Peek();

    // 例如：

    Queue qu = new Queue();

    qu.Enqueue('A');

    char c;
    
    c = qu.Peek();
```

### 4. 判断一个元素是否在队列中
```cs
    Queue.Contains(element);//返回true/false

    //例如

     if (qu.Contains("Hunter"))
    {
        Console.WriteLine("There is Hunter in the queue");
    }
    else
    {
        qu.Enqueue("Hunter");
        Console.WriteLine("Add Hunter successfully.");
    }
```
## 5.清空Queue
```cs
    Queue.Clear();
```
## 7.获得Queue中元素的数量
```cs
    Queue.Count();

    //例如：

    int count = qu.Count();

    Console.WriteLine("The num of elements in the queue: " +count); 

```