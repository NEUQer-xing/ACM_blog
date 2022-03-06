<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
# C#常用容器总结---------Hash类
<table><tr><td bgcolor = yellow ><font face = "黑体" size = 6 color = red >现在总结如下：</font></table></tr></td>

## Hash类 (相当于C++中的 map<类型，类型····>)

## 一、Dictionary<Type,Type>
- Dictionary里面的每一个元素都是一个键值对(由二个元素组成：键和值)
- 键必须是唯一的,而值不需要唯一的
- 键和值都可以是任何类型(比如：string, int, 自定义类型，等等)
- 通过一个键读取一个值的时间是接近O(1)

<font face = "隶书" size = 6 color = red >Dictionary与HashTable类似</font>

### 1.定义
```cs
    Dictionary<string, string> openWith = new Dictionary<string, string>();
```

### 2.添加元素
```cs
    //添加元素
    openWith.Add("txt", "notepad.exe");
    openWith.Add("bmp", "paint.exe");
    openWith.Add("dib", "paint.exe");
    openWith.Add("rtf", "wordpad.exe");
```
### 3.由key得value,更改值
```cs
    Console.WriteLine(openWith["rtf"]);

    //更改值

    openWith["rtf"] = "winword.exe";
```
### 4.遍历
- 遍历key
```cs
    foreach (string key in openWith.Keys)
    {
        Console.WriteLine("Key = {0}", key);
    }
```
- 遍历value
```cs
     //遍历value
    foreach (string value in openWith.Values)
    {
        Console.WriteLine("value = {0}", value);
    }
```
- 遍历字典
```cs
    foreach (KeyValuePair<string, string> kvp in openWith)
    {
        Console.WriteLine("Key = {0}, Value = {1}", kvp.Key, kvp.Value);
    }
```
### 5.判断key是否存在
```cs
//判断键存在
    if (openWith.ContainsKey("bmp")) // True 
    {
        Console.WriteLine("An element with Key = + bmp + exists.");
    }
```
