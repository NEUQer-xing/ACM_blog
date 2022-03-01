# open_cv + python
# 基本概念 : 电脑眼中的图片
- 表示两种颜色:黑白
    - 用 0 表示 黑
    - 用 1 表示 白

例如:

<img src = "https://cdn.jsdelivr.net/gh/NEUQer-xing/Markdown_images/images/20220302001043.png" width = 300px> 
<img src = "https://cdn.jsdelivr.net/gh/NEUQer-xing/Markdown_images/images/20220302001301.png" width = 300px>

----

- 用0,1两种状态表示颜色所形成的图片

<img src ="https://cdn.jsdelivr.net/gh/NEUQer-xing/Markdown_images/images/20220302002446.png" 
 width = 450px>

----
- 加入更多的状态来表示不同的灰度级别

例如:

<img src ="https://cdn.jsdelivr.net/gh/NEUQer-xing/Markdown_images/images/20220302003101.png"  width = 450px>

<font face = "宋体" size = 5 color = black >**利用8位bit来分别表示256种不同的灰度等级,从而可以使得画质更加的清晰**</font>

----
- 彩色图片(RGB)
  
<img src ="https://cdn.jsdelivr.net/gh/NEUQer-xing/Markdown_images/images/20220302003615.png " width = 450px >

同理:
- 红:0-256 表示不同程度的红色
- 绿:0-256 表示不同程度的绿色
- 蓝:0-256 表示不同程度的蓝色

<font face = "宋体" size = 5 color = black >**使用`[Red,Green,Blue]`三元组来调配三者的比例,从而实现彩色画面**</font>

<img src =" https://cdn.jsdelivr.net/gh/NEUQer-xing/Markdown_images/images/20220302004211.png" width = 450px >

----

# 安装OpenCv+读取图片
## 安装OpenCV 
- 建议直接在cmd里面安装
- <font face = "隶书" size = 4 color = red >在安装时,记得把fan_qiang关掉</font>
- 千万别像我一样,默认清华镜像但那个还开着,直接报错:
  
        Could not find a version that satisfies the requirement opencv-python
        No matching distribution found for opencv-python
- 安装成功的样子:

![20220302012032](https://cdn.jsdelivr.net/gh/NEUQer-xing/Markdown_images/images/20220302012032.png)

----
## 读取图片









