# 面试题目整理

乐乐

## Java基础类

##### 1.一个`.java`源文件中是否可以包括多个类(不是内部类)？有什么限制？
答案:可以有多个类，但只能有一个`public`的类，并且`public`的类名必须与文件名相一致。

##### 2.Java有没有`goto`?
答案:java中的保留字.

##### 3.`&`和`&&`的区别
* 相同点
	都可以用作逻辑与的运算符，表示逻辑与`and`，当运算符两边的表达式的结果都为`true`时，整个运算结果才为`true`，否则，只要有一方为`false`，则结果为`false`。
* 不同点
	* `&&`具有短路的功能，即如果第一个表达式为`false`，则不再计算第二个表达式
		例如，对于`if(str!= null&& !str.equals(s))`表达式，当`str`为`null`时，后面的表达式不会执行，所以不会出现`NullPointerException`如果将`&&`改为`&`，则会抛出`NullPointerException`异常。`If(x==33 &++y>0)`中`y`会增长，`If(x==33 && ++y>0)`中`y`不会增长

	* `&`还可以用作位运算符，当`&`操作符两边的表达式不是`boolean`类型时，`&`表示按位与操作
		我们通常使用`0x0f`来与一个整数进行`&`运算，来获取该整数的最低4个bit位，例如，`0x31 & 0x0f`的结果为`0x01`。

##### 4.在Java中如何跳出当前的多重嵌套循环？
(1).label标签
在Java中，要想跳出多重循环，可以在外面的循环语句前定义一个标号，然后在里层循环体的代码中使用带有标号的`break`语句，即可跳出外层循环
eg:
```java
a:for (int i = 0; i < args.length; i++) {
	for (int j = 0; j < args[i].length; j++) {
		if(i==4) {
			break a;
		}
	}
}
```
(2).设置flag
```java
int arr[][] = {
		{ 1, 2, 3, 4 },
		{ 5, 6, 7},
		{ 8, 9, 10 }
};

boolean flag = true;
for (int i = 0; i < arr.length && flag; i++) {
	for (int j = 0; j < arr[i].length; j++) {
		System.out.println(i+" : "+j);
		if(arr[i][j] == 6) {
			flag = false;
			break;
		}
	}
}
```

(3).`return`

##### 5.`switch`语句可以使用的数据类型
JDK 1.7之前支持`byet`、` short`、` char`、` int`
JDK 1.5支持`Byte`、` Short `、`Character `、`Integer`，底层有了自动拆箱操作

JDK 1.7之后支持枚举类型
实际上是比较的枚举包装类下的方法`public final int ordinal()`调用之后输出的序列值
```java
enum Flag {
	NORMAL, UNNORMAL
}

public static void way() {
	Flag key = Flag.UNNORMAL;


	switch (key) {
	case NORMAL:

		break;
	case UNNORMAL:

		break;

	default:
		break;
	}

}
```
JDK 1.7之后支持的`String`

##### 6.用最有效率的方法算出2乘以8等于几?
`2<<3`，(左移三位)因为将一个数左移n位，就相当于乘以了2的n次方，那么，一个数乘以8只要将其左移3位即可，而位运算cpu直接支持的，效率最高，所以，2乘以8等於几的最效率的方法是`2<<3`。

##### 7.使用`final`关键字修饰一个变量时，是引用不能变，还是引用的对象不能变？
使用`final`关键字修饰一个变量时，是指引用变量不能变，引用变量所指向的对象中的内容还是可以改变的。
eg:
```java
final StringBuffer str = new StringBuffer("hello");

// str = new StringBuffer(" "); 编译报错

// 编译通过
str.append("world");
```
##### 8.静态变量和实例变量的区别？
在语法定义上的区别：静态变量前要加`static`关键字，而实例变量前则不加。

在程序运行时的区别：实例变量属于某个对象的属性，必须创建了实例对象，其中的实例变量才会被分配空间，才能使用这个实例变量。静态变量不属于某个实例对象，而是属于类，所以也称为类变量，只要程序加载了类的字节码，不用创建任何实例对象，静态变量就会被分配空间，静态变量就可以被使用了。总之，实例变量必须创建对象后才可以通过这个对象来使用，静态变量则可以直接使用类名来引用,静态变量是被所有的类对象所共享的。

##### 9.`Math.round(11.5)`等于多少?`Math.round(-11.5)`等于多少?
`public static long round(double a)`对于正数四舍五入，对于负数，`0.5`以下(包含)舍向数字大的方向,`0.5`以上进向数字小的方向
`public static double ceil(double a)` `ceil`意思为天花板，方法表示向数字大的方向取整
`public static double floor(double a)` `floor`意思为地板，方法表示为向数字小的方法取整

eg:
```java
System.out.println(Math.round(11.2));//11
System.out.println(Math.round(11.5));// 12
System.out.println(Math.round(11.6));//12
System.out.println(Math.round(-11.2));//-11
System.out.println(Math.round(-11.5));//-11
System.out.println(Math.round(-11.6));//-12

System.out.println(Math.ceil(11.5));//12.0
System.out.println(Math.ceil(11.6));//12.0
System.out.println(Math.ceil(-11.5));//-11.0
System.out.println(Math.ceil(-11.6));//-11.0

System.out.println(Math.floor(11.5));//11.0
System.out.println(Math.floor(11.5));//11.0
System.out.println(Math.floor(-11.5));//-12.0
System.out.println(Math.floor(-11.5));//-12.0
```




























进程的物种





