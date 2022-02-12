# C#���������ܽ�---------Queue<����>
<table><tr><td bgcolor = yellow ><font face = "����" size = 6 color = red >�����ܽ����£�</font></table></tr></td>

## Queue<����>  (�൱��C++�е� queue<����>)

### 1. ����Queue
```cs
    Queue<����> ���� = new Queue<����>();

    //���磺

     Queue<Tuple<int, int>> qu = new Queue<Tuple<int, int>>();
```

### 2. ���Ԫ��
- �ڶ���ĩβ���һ��Ԫ��
```cs
    Queue.Enqueue(element);

    // ���磺

    Queue qu = new Queue();

    qu.Enqueue('A');

```
### 3. ��ȡͷ��Ԫ��
- �ڶ�ȡ֮���ɾ����
```cs
    element = Queue.Dequeue();

    // ���磺

    Queue qu = new Queue();

    qu.Enqueue('A');

    char c;
    
    c = qu.Dequeue();
```
- ֻ��ȡ����ɾ��
```cs
    element = Queue.Peek();

    // ���磺

    Queue qu = new Queue();

    qu.Enqueue('A');

    char c;
    
    c = qu.Peek();
```

### 4. �ж�һ��Ԫ���Ƿ��ڶ�����
```cs
    Queue.Contains(element);//����true/false

    //����

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
## 5.���Queue
```cs
    Queue.Clear();
```
## 7.���Queue��Ԫ�ص�����
```cs
    Queue.Count();

    //���磺

    int count = qu.Count();

    Console.WriteLine("The num of elements in the queue: " +count); 

```