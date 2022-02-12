# C#常用容器总结---------Tuple<类型，····>
<table><tr><td bgcolor = yellow ><font face = "黑体" size = 6 color = red >现在总结如下：</font></table></tr></td>

## Tuple<类型,··>  (相当于C++中的 pair<类型,·>)

### 1.定义
```cs
    Tuple<类型，类型> 名称 = new Tuple<类型，类型>(element1，element2);

    //例如：

    //一个元素的元组
    Tuple<int> test = new Tuple<int>(34);
 
    //两个元素的元组 1<n<8
    Tuple<string, int> test2 = Tuple.Create<string, int>("str", 2);
    Tuple<int, int> test2_1 = new Tuple<int, int>(2,2);

```

### 2.获取元组内的值
    元组元素可以通过 Item < elementnumber > 属性访问
    
    例如 Item1、 Item2、 Item3等，最多可以访问 Item7属性。
    
    Item1属性返回第一个元素，Item2返回第二个元素，依此类推。
    
```cs
    Tuple<int, string, string> person = new Tuple <int, string, string>(1, "Steve", "Jobs");
    person.Item1; // 返回 1
    person.Item2; // 返回 "Steve"
    person.Item3; // 返回 "Jobs"    
```

