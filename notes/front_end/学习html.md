
# HTML
-------
作者:乐乐


## 第一章 了解HTMl
### (一).HTML的概念
* 超文本标记语言(HyperText Markup Language),是一种解释执行的文本类标记语言，主要用于Internet上编写网页，“超文本”就是指页面内可以包含图片，链接，甚至音乐，程序等非文字元素。

* `html`也是一种规范，一种标准，它通过标记符号来标记要显示网页中的各个部分。网页文件本身是一种文本文件，通过在文本文件中添加标记，可以告诉浏览器如何显示其中的内容（如：文字如何处理，画面如何安排，图片如何显示等）。浏览器按顺序阅读解析页文件，然后根据标记符解释和显示其标记的内容，对书写出错的标记将不指出其错误，且不停止其解释执行过程，编制者只能通过显示效果来分析出错原因和出错部位。

* 一个最基本的HTML结构
```html
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
<html>
	<head>

	</head>
	<body>

	</body>
</html>
```

### (二).HTML的发展历程
* HTML1.0~2.0,1989~1991,概念不明确
* HTML3,1995,浏览器战争年代，Netscape和Microsoft都在试图争霸世界
* HTML4,1998,浏览器大战结束，万维网联盟(W3C)解救我们，他们的计划是创建一个唯一的HTML标准。计划的关键是将HTML的结构和表现分解为两种语言，一种语言用于实现结构（HTML）一种语言用于表现（CSS）.
* HTML4.01,1999,这段日子过得很惬意，HTML4.01在1999年闪亮登场，称为接下来很多年中HTML"必备"版本
* XHTML1.0,2001,正当我们感觉安逸的时候一个新兴事物引起所有人注意，即XML。它让HTML开始心烦意乱，最终两者结合，XHTML1.0诞生。
* XHTML承诺，由于它的严格，再加上它提供的一些新方法，只要遵循这个标准，WEB的所有争端将就此平息。但是，大多数人都很讨厌XHTML，Web开发人员对HTML的灵活性更感兴趣，而不是XHTML的严格性。
* HTML5,html和xml由于没有得到大家的祝福，这场婚姻的结局并不好，很快被HTML的新版本取代，即HTML5.它支持HTML4.01标准的大部分特性，还提供一些新特性。随着时间的推移，将来HTML5注定成为大家公认的标准。

## 第二章 HTML的基本语法
### 1.文件后缀
* html文件是一个文本文件，可以使用任意的文本编辑器来编写
* html文件后缀`*.html`或者`*.htm`

### 2.注释
HTML语言的注释符号为`<!-- 注释内容 -->`
### 3.基本语法
#### (1)标签
html文件中用标签来标记内容，说明这一段文本的含义，标签使用`<>`包围
分为成对标签和单标签
```html
<!-- 成对标签 -->
<a></a>

<!-- 单标签 -->
<hr>
```
#### (2)元素
一个元素通常由一个开始标签，内容，其他元素以及一个结束标签组成
#### (3)属性
* 与元素相关的特性称为属性，属性由键值对组成。
* 基本构成`<元素名 属性1=值1 属性2=值2 ...></元素名>`
* 通用标签属性

| 属性名  |    表示含义    |
| :-----: | :------------: |
|  `id`   |    唯一标识    |
| `class` |  标识一类元素  |
| `style` |      样式      |
| `title` |    描述信息    |
| `name`  | 名字(可以重复) |

#### (4)规范
元素名和属性都不区分大小写
#### (5).文档结构
最基本的HTML文件
```html
<!DOCTYPE html>
<html>
	<head>
		<title></title>
	</head>
	<body>

	</body>
</html>
```
##### <1>HTML文件声明
* HTML的声明`<!DOCTYPE html>`
* HTML使用DTD来指定文档类型
	1>严格的文档类型
	`<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">`
	2>宽松的文档类型
	`<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">`
	3>frameset框架文档类型
	`<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Frameset//EN" "http://www.w3.org/TR/html4/frameset.dtd">`
	4>H5文档类型
	`<!DOCTYPE html>`

##### <2>HTML文件各部分的含义
```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8"><!-- 元信息 -->
		<title>标题</title>
		<!-- 		元信息
					标题
					脚本
					样式
		-->
	</head>
	<body>
		<!-- 浏览器显示的内容 -->
	</body>
</html>
```
#### (6).`meta`元素
定义文档的元数据
##### <1>定义元数据关键字
给搜索引擎看的
```html
<meta name="Author" content="candice">
<meta name="Copyright" content="版权信息">
<meta name="Description" content="描述信息">
<meta name="keywords" lang="zh-cn" content="精品图书">
<meta name="keywords" lang="en-us" content="good book">
```
##### <2>报头规范
这是给浏览器看的内容
* `<meta http-equiv="Content-Type" content="text/html;charset=utf-8">`
将会创建如下的消息头
`Content-Type:text/html;charset=utf-8`

* `<meta http-equiv="Content-Languaga" content="zh-CN">`
将会创建如下的消息头
`Content-Language:zh-CN`

* `<meta http-equiv="Refresh" content="n;url=http://yourlink">`
定时让网页在指定的时间n内跳转到页面http://yourlink

* `<meta http-equiv="expires"content="Fri,12Jan200118:18:18GMT">`
可以用于设定网页的到期时间。一旦网页过期，必须到服务器上重新传输。

* `<meta http-equiv="Pragma" content="no-cache">`
设置网页禁用浏览器缓存
将会创建如下的消息头：`Pragma:no-cache`

* `<meta http-equiv="Cache-Control" content="no-cache">`
设置网页禁用浏览器缓存

### 4.颜色和大小
#### (1)颜色
* 颜色由红(R),绿(G),蓝(B),三色组成，每个颜色的范围都是`0-255`(byte字节)，用十六进制表示为`00-FF`
* 语法:`#三位十六进制数`或`#六个十六进制数`
* 六个十六进制数一个字节的两位相同时，用三位十六进制缩写表示，例如:`#FFFFFF`等价于`#FFF`
* 颜色的表示方法

| 3位十六进制 | 六位十六进制 |        RGB         |  英文   | 表示颜色 |
| :---------: | :----------: | :----------------: | :-----: | :------: |
|   `#000`    |  `#000000`   |    `rgb(0,0,0)`    | `black` |   黑色   |
|   `#F00`    |  `#FF0000`   |   `rgb(255,0,0)`   |  `red`  |   红色   |
|   `#FFF`    |  `#FFFFFF`   | `rgb(255,255,255)` | `white` |   白色   |

#### (2)大小
像素,用`px`表示

## 第三章 HTMl标签
### (一).块级(block)标签
#### 1.`div`标签
* `<div></div>`
* 特点:独占一行

#### 2.`h1~h6`标题
* `<h1></h1>`
  `<h2></h2>`
  `<h3></h3>`
  `<h4></h4>`
  `<h5></h5>`
  `<h6></h6>`
* 特点:
	* 有字体大小的设置
	* 文本有加粗强调的设置
	* 上下文之间有较大的间距

#### 3.`p`段落
* `<p></p>`
* 特点：
	* 独占一行
	* 上下文之间具有距离

#### 4.有序和无序列表
* 无序列表语法
```html
<ul>
	<li>条目1</li>
	<li>条目2</li>
	<li>...</li>
</ul>
```
* 有序列表语法
```html
<ol>
	<li>条目1</li>
	<li>条目2</li>
	<li>条目3</li>
	<li>...</li>
</ol>
```
* 特点:
	* 配合嵌套使用
	* `ul`、`ol`和`li`都独占一行空间
	* `ul`、`ol`上下文之间有很大空间
	* `li`标签有样式(默认圆点),并且具有文本缩进

#### 5.自定义列表
* 语法
```html
<dl>
	<dt>列表标题</dt>
	<dd>列表内容</dd>
	<dd>列表内容</dd>
	<dd>列表内容</dd>
	<dd>...</dd>
</dl>
```
* 特点
	* 三个标签配合使用，`dl`下面可以有若干`dt`，`dt`下面有若干`dd`.
	* `dl`、`dt`、`dd`独占一行空间
	* `dl`上下文之间有很大的空间
	* `dd`有文本缩进

### (二).行内(内联inline)标签
#### 1.`span`标签
* 语法
`<span></span>`
* 特点
	* 最干净的内联标签(没有任何修饰)
	* 不独占一行

#### 2.`a`标签
* 语法 `<a></a>`
* 特点
	* 不独占一行
	* 点击可以发生跳转(或进行对应的操作),语法颜色为绿色
	* 文本具有颜色，具有下划线，指向后光标为手型，有状态的色彩提示

#### 3.文本修饰标签(decoration)
* 下划线`<u></u>`
* 斜体`<i></i>`
* 加粗`<b></b>`
* 强调`<em></em>`
* 加粗`<strong></strong>`
* 删除线`<s></s>`
* 上标`<sup><sup>`
* 下标`<sub></sub>`

#### 4.`img`标签
* 语法
	`<img src="图片路径">`
* 绝对路径
	`http://www.baidu.com/car.jpg`
	`http://www.baidu.com/demo/one.html`
* 相对路径
	`.` `./` `../`

### (三).超链接
* 从一个web资源到另外一个web资源的连接
* 绝对路径（服务器路径）：
	每个网页都有一个唯一的地址，称为URL 统一资源定位符，也称为该网页的绝对路径。
* 相对路径：
	相对于当前文档所在的路径
	../imgs/a.jpg
	./imgs/a.jpg
	imgs/a.jpg
* 本地连接
	file:///d:/html/index.html
	**超链接中不允许写本地连接**
* 服务器路径
	http://localhost:8888/test/index.html

#### 1.超链接
`<a href="跳转路径">html显示的内容</a>`
* 属性
	`href`定义连接的目标`URI`
	`href`的值
		* 绝对路径：`http://www.baidu.com`
		* 相对路径：`b.html`
		* 邮件地址：`mailto:test@lele.com`
		* 锚点：`#mao`
		* 空连接：`javascript:void(0);`
* 连接状态
	* 未访问
	* 已选择
	* 已访问

* 锚点
	* 锚点可以让用户在文档中设置标记，这些标记通常放在文档的特定主题处或顶部，然后创建到这些锚点的连接，指向网页中的特定位置。
	* 例如
```html
<h2 id="section1">1,什么是万维网</h2>
<p>万维网，是基于Internet的信息服务系统，官方定义为"WWW is a wide-area hypermedia information retrieval initiative aiming to give universal access to a large universe of documents",简而言之，WWW是一个以Internet为基础的计算机网络，它允许用户在一台计算机上通过Internet访问另一台计算机上的信...</p>

<a href="#section1">查看万维网</a>
```

#### 2.`link`文档关系连接
* 只能出现在`<head></head>`标签中，定义了当前文档和另一个资源之间的联系。
通常用于链接到外部样式表
`<link rel="stylesheet" href="style.css" type="text/css">`
* 属性
	* `href`定义关系链接地址
	* `rel`	定义当前文档与所连接文档之间的关系。
	* `type`文档类型

#### 3.`base`基准链接地址
* 设置页面中所有文档相对路径相对的基准`URI`。如果设定了基准链接地址，当前页面中的所有相对路径都基于该路径
**定义在`<head></head>`标签中**
`<base href="http://localhost:8888/web">`

### (四).图片`img`
#### 1.图片类型
适合在网站上进行快速查看的图片格式
* GIF(graphics interchange format,图形交换格式)
	可以将背景设置为透明的，图片最多使用256种颜色，最适合显示色调不连续或具有大面积单一颜色的图片，如导航条，按钮，图标等。由于GIF图片中存储的颜色信息较少，因此占用空间极小，使用起来更方便。
* JPEG(joint photographic experts group,联合图像专家组)
	最适合摄影或连续色调图像的彩色照片，jpeg文件可以包含数百万中颜色，保证图片不失真。JPEG图片无法拥有透明的背景
* PNG(portable network graphics,可移植网络图形)
	PNG可以包含256种以上的颜色，并可以具有透明的背景。PNG文件可保留所有原始层，矢量，灰度，颜色和效果信息，并且在任何时候所有元素都是可以编辑的。

#### 2.标签属性
`<img src="" alt="">`
属性
	* `src`		: 图片的源地址
	* `title`	: 对图片的文字说明，当用户把鼠标放在图片上稍作停留，alt属性的值就会以浮动的形式显示出来。
	* `width`	: 图片的宽度
	* `height`	: 图片的高度
	* `alt`		: 当图片文件找不到的时候显示的文本信息
	* `border`	：图片的边框
	* `align`	：图片和文字的对齐
		当`align`值为`left`时，图片靠在最左方，周围的文字显示在右侧上方
		当`align`值为`right`时，图片靠在最右方，周围的文字显示在左侧上方
		当`align`值为`top`时，图片靠在最上方，周围的文字显示在上方
		当`align`值为`bottom`时，图片靠在最上方，周围的文字显示在下方
	* `hspace`	：图片的水平间距
	* `vspace`	：图片的垂直间距

## 第三章 表格
语法
```html
<table>
	<tbody>
		<tr>
			<td></td>
			<td></td>
		</tr>
		<tr>
			<td></td>
			<td></td>
		</tr>
		<tr>
			<td></td>
			<td></td>
			</tr>
	</tbody>
</table>
```
### (一).`<table></table>`
* 用来定义表格
* 常见属性
	* `border`     :   设置表格边框线条宽度
	* `width`      :   设置表格宽度
	* `align`      :   表格在页面中对其
	* `bgcolor`    :   表格背景色
	* `cellspacing`:   单元格间距
	* `cellpadding`:   单元格边界与单元内容之间的间距

### (二).`<tr></tr>`
定义表格行
### (三).`<th></th>`和`<td></td>`
* `th` 定义单元格
* `td` 定义内容单元格
* 属性
	* `colspan`	跨列，合并列
	* `rowspan`	跨行，合并行
	* `align` 	单元格水平对其
	* `left`,`center`,`right`,`justify`	左，居中，右，两端对其

### (四).`caption`
表格的标题
### (五).表格分组显示
* `thead` 表格头
* `tfoot` 表格尾
* `tbody` 表格主体

## 第三章 框架文档
* 一个框架文档由四部分组成，文档声明，html元素，head元素，frameset元素
* 框架文档声明
`<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Frameset//EN"
"http://www.w3.org/TR/html4/frameset.dtd">`

### (一).`frameset`框架集
* `rows`用来定义将框架水平分隔为子框架的数量和这些子框架的宽度
* `cols`用来定义将框架垂直分隔为子框架的数量和这些子框架的高度。
```html
<frameset rows="10%,90%">
	<frame src="页面1">
	<frameset cols="15%,85%">
		<frame src="页面2">
		<frame src="页面3">
	</frameset>
</frameset>
```
**`html`文件中只能同时包含`body`标签或者`frameset`标签其中之一**

### (二).`frame`框架窗口
属性
	* `src`:设置框架的初始内容
	* `name`:框架名称，作为该框架的标识,可以配合超链接的target属性来使用`<a href="" target=""></a>`
	* `target`:值可以为
		* `_blank`
		* `_parent`
		* `_self`
		* `_top`
		* 框架名

### (三).`iframe`内联框架
iframe允许用户在一个文本中插入一个框架，iframe元素可以使用frame元素的所有属性，实现功能也相同。
```html
<body>
	<iframe src=""></iframe>
</body>
```
**`<iframe></iframe>`可以和`<body></body>`一起使用**
## 第三章 表单
主要用于收集来自用户的信息，并将收集的信息发送给服务器端处理程序处理。表单是客户端和服务器端传递数据的桥梁，是实现与服务器互动的最主要方式。
### (一).`form`标签
表单控制的容器
`<form action=""></form>`
属性
	* `action` 	设定处理表单数据URI的地址
	* `method`	设定数据传送到服务器的方式
		* `get`	 将输入的数据追加到action地址后面
		* `post` 将输入的数据保存到HTTP协议的报文中
	* `name`	设定表单的名称
	* `enctype`	设定表单数据的内容类型
		* `application/x-www-form-urlencoded`	在发送前编码所有字符（默认）
			* 编码方式：
				* 控件的名称和值都被转义，空白字符使用`+`替换，保留的字符一般都是用来实现特定的目的，例如(`:` `/` `?` `;` `@` `=` `&` 等)。非数字和字母的字符使用`%HH`（这里HH表示两个十六进制数字，代表该字符的ASCII码）进行转换，
				* 控件的`名称/值`对按照它们在文档数据流中出现的顺序列出来。"名称"和"值"使用"="分割，两个"名称/值"之间使用&隔开。
		* `multipart/form-data`	 不对字符编码。在使用包含文件上传控件的表单时，必须使用该值。
			数据分成多个部分，每个部分代表一个结构良好的控件，作为文档数据流的一部分，每一个部分都按照它们在文档数据流中出现的顺序依次发送到服务器端，并且，每一部分的边界不会出现在数据中。每一部分有一个content-desposition标题头，它的值的格式是：
			`Content-Disposition:form-data;name="myControl"`
	* `text/plain` 空格转换为`+`加号，但不对特殊字符编码。
	* `accept-charset` 设置服务器端可以处理的字符编码
### (一).`input`标签
基本表单控件
<input type="" name="">
属性
	* `type` 控件类型
		* `text`		单行文本框
		* `textarea`	多行文本框
		* `password`	密码框
		* `checkbox`	复选框
		* `radio`		单选按钮
		* `submit`		提交按钮
		* `reset`		重置按钮
		* `file`		文件
		* `hidden`		隐藏域
		* `image`		图像按钮
		* `button`		普通按钮
	* `name` 控件名称
		这个名称将与控件的当前值形参"名称/值"对 一同随表单提交
	* `value`	用于设定初始化的默认值，可选。
	* `checked` 单选框，复选框默认选中属性
	* `size`	当前控件的初始宽度
		这个宽度以像素为单位。除非控件类型是`text`,`password`，这时宽度是整数值，表示字符的数目
	* `maxlength` 指定可以输入的字符的最大值。适用于控件类型为`text`,`password`。


子绝 父相

