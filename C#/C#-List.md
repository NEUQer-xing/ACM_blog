# C#常用容器总结---------List<类型>
<table><tr><td bgcolor = yellow ><font face = "黑体" size = 6 color = red >现在总结如下：</font></table></tr></td>

## List<类型>  (相当于C++中的 vector<类型>)

### 1.创建 List<>

```cs
    List<类型> 名字 = new List<类型>();
    
    //例如：

    List<int> nums = new List<int>();
```
### 2.添加元素
- 一个元素
```cs
    List.Add(element)； 
    
    //例如：

    List<string> mList = new List<string>();

    mList.Add("John");
```
- 添加一组元素
```cs
    List.AddRange(a group of element)
    
    //例如：

    List<string> mList = new List<string>();

    string[] temArr = { "Ha","Hunter", "Tom", "Lily", "Jay", "Jim", "Kuku",  "Locu" };

    mList.AddRange(temArr);   
```
- 在index位置插入元素
```cs
    List.Insert(index, element);

    //例如：

    List<string> mList = new List<string>();

    mList.Insert(2, "Hei");
```
- 遍历元素
    可以用for()+index
    也可以用foreach()
```cs
    foreach (T element in mList)  //T的类型与mList声明时一样
    {
        Console.WriteLine(element);
    }
```
## 3.删除元素
- 删除一个元素
```cs
    List. Remove(element)

    //例如：

    mList.Remove("Hunter");
```
- 删除下标为index的元素
```cs
    List. RemoveAt(index);   

    //例如：

    mList.RemoveAt(0);
```

- 从下标index开始，删除count个元素
```cs
    List. RemoveRange(index, count);

    //例如：

    mList.RemoveRange(3, 2);
```
## 4.查找元素
- 判断是否在List中：返回true/false
```cs
    List.Contains(element);

    //例如

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
## 5.排序 
```cs
    List.Sort();//升序排序

    List.Sort();
    List.Reverse(); //降序排序
```
## 6.清空List
```cs
    List.Clear();
```
## 7.获得List中元素的数量
```cs
    List.Count();

    //例如：

    int count = mList.Count();

    Console.WriteLine("The num of elements in the list: " +count); 

```




