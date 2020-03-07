JSP从入门到放弃
-----
作者:乐乐

## 一、`JSP`概述
### (一).JSP是什么
### (二).JSP的运行
### (三).JSP和Servlet的关系

## 二、`JSP`的生命周期
### (一).编译
### (二).初始化
### (三).执行
### (四).销毁

## 三、JSP的页面组成和编写
### (一).JSP脚本元素
#### 1.表达式`<%= %>`
* 语法
```jsp
<%= %>
```
* 编译位置
`_jspService()`方法中`out.print();`里面的值，等价于`System.out.println()`可以输出什么，`<%= %>`就可以写什么
* JSP的表达式里是没有`;`的
* 实例
```jsp
<%= 变量、数学运算式、调用有返回值的方法等 %>
<%=basePath %>
<%=user.username %>
```

#### 2.脚本`<% %>`
* 语法
```jsp
<!-- 可以写在一行 -->
<% %>
<%
	/* 也可以展开写 */
%>
```
* 编译位置
`_jspService()`方法中的代码，相当于写在一个方法中的代码，在Java的普通方法中，可以写什么代码，`<% %>`可以写什么代码
* 每一句写完，都是要加`;`,因为在Java的方法中，每一句代码写完都是以`;`结尾的
* 在`<% %>`中声明定义的变量，是可以在`<%= %>`中使用的，但是有先后顺序，先声明，后使用
* 实例
```jsp
<%
	List<String> list = new ArrayList<>();
	list.add("lele");

	list.forEach(l->System.out.println(l));

	int count = 0;

	User u = new User();

	u.setUsername("");
	u.getUsername();

	if(u.getEmail()==null && "".equals(u.getEmail())){

	}
%>
```

#### 3.声明`<%! %>`
* 语法
```jsp
<%!
	/* Your code is here! */
%>
```
* 编译位置
编译到Java类中的代码，一个类中可以写哪些代码，`<%! %>`就可以写哪些代码
* 定义变量要加`;`,定义方法不加`;`,跟在一个普通Java类中写代码是一样的
* 实例
```jsp
<%!
	private int count;

	private List<User> userslist = new ArrayList<>();

	private String driver;
	private String url;
	private String user;
	private String password;


	public Connection getConnection()throws Exception{

		Class.forName(driver);

		Connection conn = DriverManager.getConnection(url, user, password);
		return conn;
	}
%>
```

### (二).JSP指令元素
jsp指令元素是程序员给jsp引擎给的指令，告诉jsp引擎，在编译这个jsp页面时，需要对这个jsp页面做哪些处理，例如，应该使用哪种编码，导入哪些Java类，使用哪种编程语言等(目前只支持Java)
#### 1.语法`<%@ %>`
```jsp
<%@指令 属性="值" 属性="值" 属性="值" ...%>
```
#### 2.`page`指令
* 语法
```jsp
<%@page
		language="java"
		import=""
		pageEncoding="UTF-8"
		contentType="text/html; charset=UTF-8"
		extends=""
		session="true"
		isThreadSafe="true"
		errorPage=""
		isErrorPage="false"
%>
```
* 属性
	* `language`当前页面的编程语言,目前只有Java
	* `import `当前页面导入的Java类，包名
	* `pageEncoding`设置页面编码,一般是`UTF-8`
	* `contentType`服务器输出给浏览器时，使用什么编码
	* `extends`当前页面编译成Java类，需要继承的父类，默认有一个父类，一般不用设置
	* `session`设置当前页面是否支持session对象的使用，默认为`true`
	* `isThreadSafe`设置当前页面是否是线程安全的,布尔类型的值
	* `errorPage`设置当前页面访问出现错误后要跳转的页面
		访问一旦出现错误，自动跳转到设置的错误页面
	* `isErrorPage`设置当前页面是不是访问出错时要跳转的页面，默认为`false`
		设置为`true`，这个页面就是专门用来显示错误信息的页面，就可以使用内置对象exception来显示错误信息了

#### 3.`include`指令
* `include`指令可以把另外一个页面的内容引入到当前的页面，属于静态包含
	* 静态包含:编译期间，被包含页面的内容会被需要包含的页面原封不动的搬过来一起编译，然后输出
* 语法
```jsp
<%@include file="" %>
```

#### 4.`taglib`指令
* 为当前页面引入标签库
* 语法
```jsp
<%@taglib
	uri=""
	prefix=""
	tagdir=""
%>

<!-- 引入JSTL标签库 -->
<%@taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c"%>
```
* 属性
	* `uri`标签库的地址
	* `prefix`使用标签库的前缀
	* `tagdir`标签目录，一般不写

### (三).JSP动作元素
#### 1.语法`<jsp:></jsp:>`
#### 1.语法`<jsp:></jsp:>`
#### 1.语法`<jsp:></jsp:>`

## 四、注释
### (一).html页面注释`<!--  -->`
### (二).JSP注释`<%-- --%>`
### (三).Java语言注释

## 五、JSP内置对象
* 只能在`<% 脚本 %>`和`<%= 表达式 %>`中使用
* 内置对象在`_jspService()`方法中默认声明了.在jsp页面表达式和脚本中所写的java代码将来是要编译到`_jspService()`方法中,所以我们在表达式和脚本中写java代码的时候可以直接使用这些对象.
* 九大内置对象
	request
	response
	session
	application
	config
	page
	pageContext
	out
	exception

## 六、JSP页面基准路径
## 七、EL表达式
## 八、JSTL标签库
## 九、自定义标签





JSP全称Java Server Pages
后缀名`*.jsp`
JSP是动态页面
html是静态页面
