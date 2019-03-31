# How To Use F12
## Introduction

F12是前端开发人员的利器，以Chrome浏览器为例，在Chrome开发者工具中，调试时使用最多的三个功能页面是：元素（ELements）、控制台（Console）、源代码（Sources），此外还有网络（Network）等。

• 元素（Elements）：用于查看或修改HTML元素的属性、CSS属性、监听事件、断点等。

•控制台（Console）：控制台一般用于执行一次性代码，查看JavaScript对象，查看调试日志信息或异常信息。

•源代码（Sources）：该页面用于查看页面的HTML文件源代码、JavaScript源代码、CSS源代码，此外最重要的是可以调试JavaScript源代码，可以给JS代码添加断点等。

•网络（Network）：网络页面主要用于查看header等与网络连接相关的信息。


### 1、元素（Elements）

查看元素代码：点击菜单栏左侧箭头（或用者用快捷键Ctrl+Shift+C）进入选择元素模式，然后从页面中选择需要查看的元素，然后可以在开发者工具元素（Elements）一栏中定位到该元素源代码的具体位置 。

查看元素属性：可从被定位的源码中查看部分，如class、src，也可在右边的侧栏中查看全部的属性。

修改元素的代码与属性：可直接双击想要修改的部分，然后就进行修改，或者选中要修改部分后点击右键进行修改。


### 2、控制台（Console）

•查看JS对象的及其属性

•执行JS语句

•查看控制台日志：当网页的JS代码中使用了console.log()函数时，该函数输出的日志信息会在控制台中显示。日志信息一般在开发调试时启用，而当正式上线后，一般会将该函数去掉。

### 3、源代码（Sources）

其主要功能如下介绍

![Sources](https://img-blog.csdn.net/2018041018293410?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L20wXzM3NzI0MzU2/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

### 4、网络（Network）

大体功能如下：

![Network](https://img-blog.csdn.net/20180410184756216?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L20wXzM3NzI0MzU2/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

 



### 如何使用浏览器的F12调试页面？

一个程序员按照要求编写一个网页，不可能一次编写就完全达到目的，一般要对自己的的代码修改调试几次后才能到达要求，浏览器的F12开发人员工具就可以很方便的帮助程序员调试自己的代码。

F12 开发人员工具是一套按需采用的工具，网站开发人员可以随时在任何网页上使用 F12 工具，从而快速调试 JavaScript、HTML 和级联样式表 (CSS)，还可以跟踪并查明网页或网络的性能问题。

F12调试页面各个功能分别是什么？

#### Elements标签页

Elements标签页的左侧就是对页面HTML结构的查看与编辑，你可以直接在某个元素上双击修改元素的属性。

![Elements](https://img2018.cnblogs.com/blog/1017421/201810/1017421-20181009112204863-862968394.png)

#### Network标签页

Network标签页对于分析网站请求的网络情况、查看某一请求的请求头和响应头还有响应内容很有用。注意是在你打开Chrome开发者工具后发起的请求，才会在这里显示

![Network](https://img2018.cnblogs.com/blog/1017421/201810/1017421-20181009112227978-1348717541.png)

#### Sources标签页

Sources标签页可以查看到请求的资源情况，包括CSS、JS、图片等的内容。也可以设置各种断点。对存储的内容进行编辑然后保存也会实时的反应到页面上。

![Sources](https://img2018.cnblogs.com/blog/1017421/201810/1017421-20181009112236552-1469961277.png)

#### Audits标签页

这个对于优化前端页面、加速网页加载速度很有用;点击run按钮，就可以开始分析页面，分析完了就可以看到分析结果了

![Audits](https://img2018.cnblogs.com/blog/1017421/201810/1017421-20181009112245949-1069130619.png)

#### Console标签页

就是Javascript控制台了

![Console](https://img2018.cnblogs.com/blog/1017421/201810/1017421-20181009112254204-1403249234.png)

在控制台中可以直接模拟手机、调整UA、修改网络连接状态。

![](https://img2018.cnblogs.com/blog/1017421/201810/1017421-20181009112303609-14395621.png)






