---
title: Typora Markdown 笔记
date: 2019-01-28 14:50:59
tags: 笔记
toc: true
description: typora markdown 常见语法介绍。。。。。。
---

### 1. 基本操作

#### 1.1 内容目录

* 语法

```
[toc]
```

#### 1.2 标题

* 语法

```reStructuredText
#          一级标题
##         二级标题
###        三级标题
####       四级标题
#####      五级标题
######     六级标题
```

#### 1.3 引用

* 语法

``` reStructuredText
>  引用内容1
>  引用内容2
>> 引用内容3
```

* 效果

> 引用内容1
>
> 引用内容2
>
> >
> >
> > 引用内容3
>
>



### 2. 代码

#### 2.1 单行代码

* 语法

``` reStructuredText
`String str1="hello";`
```

* 效果

`String str1 = "hello";`

#### 2.2 多行代码

* 语法

  ``` reStructuredText
  ~~~
  ​```
  ~~~java
  ​```c
  ```

* 效果

~~~java
int a = 10;
int b = 20;
~~~

### 3.列表

#### 3.1 无序列表

- 语法

~~~ reStructuredText
* 无序列表1
+ 无序列表2
- 无序列表3
~~~

* 效果
* 无序列表1
* 无序列表2
* 无序列表3

#### 3.2 多行无序列表

* 语法

~~~reStructuredText
* 多行无序列表1
TAB * 多行无序列表2
TAB TAB * 多行无序列表3
~~~

* 效果

* 多行无序列表1
  * 多行无序列表2
    * 多行无序列表3

#### 3.3 有序列表

* 语法

~~~reStructuredText
1. 有序列表1
2. 有序列表2
3. 有序列表3
~~~

* 效果

1. 有序列表1
2. 有序列表2
3. 有序列表3

#### 3.4多行有序列表

* 语法

~~~reStructuredText
1. 多行有序列表1
2. 多行有序列表2
	1. 多行有序列表2-1
	2. 多行有序列表2-1
3. 多行有序列表2
	1. 多行有序列表3-1
	2. 多行有序列表3-1
~~~

* 效果

1. 多行有序列表1
2. 多行有序列表2
   1. 多行有序列表2-1
   2. 多行有序列表2-2

#### 3.5 任务列表

* 语法

~~~reStructuredText
-[ ] 抽烟
-[x] 喝酒
-[ ] 烫头
~~~

* 效果

-[  ] 抽烟 

-[x] 喝酒

-[ ] 烫头

#### 3.6 表格

* 语法

~~~ reStructuredText
|姓名|性别|年龄|手机号|
|:---|:--:|:--:|---:|
|张三|男|21|18975346876|
|李四|女|23|17789548964|
|王五|男|25|15876513546|
~~~

* 效果

| 姓名 | 性别 | 年龄 |      手机号 |
| :--- | :--: | :--: | ----------: |
| 张三 |  男  |  21  | 18975346876 |
| 李四 |  女  |  23  | 17789548964 |
| 王五 |  男  |  25  | 15876513546 |

### 4.链接

#### 4.1 图片

* 语法1（*本地图片*）

~~~ reStructuredText
[图片上传失败...(image-)]
~~~

* 语法2（*网络图片*）

~~~ reStructuredText
![typroa.jpg](https://upload-images.jianshu.io/upload_images/1538862-d91e815790b81e4a.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)
~~~

* 效果2

![typroa.jpg](https://upload-images.jianshu.io/upload_images/1538862-d91e815790b81e4a.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


#### 4.2 超链接

- 语法1（*行内式链接*）

~~~ reStructuredText
[百度][https://www.baidu.com/]
~~~

* 效果

[百度][https://www.baidu.com/]

* 语法2（*参考式链接*）

~~~ reStructuredText
[CSDN][CSDN网址]
[CSDN网址]:https://www.csdn.net/
~~~

* 效果2

[CSDN]:https://www.csdn.net/

* 语法3（*自动链接*）

~~~ :arrow_heading_down:
<https://github.com/>
~~~

* 效果

[https://github.com/](https://link.jianshu.com/?t=https%3A%2F%2Fgithub.com%2F)

### 5. 其它

#### 5.1 斜体

* 语法

~~~ :arrow_heading_up:
*斜体*
_斜体_
~~~

* 效果

*斜体*

_斜体_

#### 5.2 加粗

* 语法

~~~ reStructuredText
**加粗**
___加粗__
~~~

* 效果

**加粗**

__加粗__

#### 5.3 下划线

* 语法

~~~ :arrow_heading_down:
<u>下划线</u>
~~~

* 效果

<u>下划线</u>

#### 5.4 删除线

* 语法

~~~ reStructuredText
~~删除线~~
~~~

* 效果

~~删除线~~

#### 5.5 分隔线

* 语法

~~~ :black_heart:
***
---
___
~~~

* 效果

***

---

____

#### 5.6 注脚

* 语法

~~~ reStructuredText
Typroa[^1]
[^1]markdown editor
~~~

* 效果

Typroa[^1]

[^1] A markdown editor

#### 5.7 上下标

* 语法

~~~ :arrow_heading_down:
$3^2=9$
$3^{(3-1)}=9$
$H_2SO_4$
$H_{2SO_4}$
~~~

* 效果

$3^2 = 9$

$3^{(3-1)} = 9$

$H_2SO_4$

$H_{2SO_4}$

#### 5.8 符号的输入

* 语法

~~~ reStructuredText
\\   反斜线
\`   反引号
\*   星号
\_   底线
\{ \}  花括号
\[ \]  方括号
\( \)  括弧
\#   井字号
\+   加号
\-   减号
\.   英文句点
\!   惊叹号
~~~

* 效果

\\ \` \* \_ \{\} \[\] \(\) \# \+ \- \. \! 

#### 5.9 特殊符号

* 语法

~~~ reStructuredText
&copy;      版权      
&reg;       注册商标
&trade;     商标
&nbsp;      空格
&amp;       和号
&quot;      引号
&apos;      撇号
&lt;        小于号
&gt;        大于号
&ne;        不等号
&le;        小于等于
&ge;        大于等于
&cent;      分
&pound;     磅
&euro;      欧元
&yen;       元
&sect;      节
&times;     乘号
&divide;    除号
&plusmn;    正负号
~~~

* 效果

&copy; &reg; &trade; &nbsp; &amp; &quot; &apos; &lt; &gt; &ne; &le; &cent; &pound; &euro; &yen; &sect; &times; &divide; &plusmn; 