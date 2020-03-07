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


# start和run方法的区别
start()方法:启动线程，在新线程中执行，异步执行
run()方法，线程方法，方法内的代码称为线程体，调用该方法相当于调用一个普通方法，同步执行


# 接口和抽象类的区别
都不能实例化
抽象类用来定制模板，即重用代码，接口用来定制标准，即解耦合

接口可以多继承

抽象类
可以有抽象或者非抽象方法public 或者protected修饰
private方法必须是普通方法
不能有default方法

可以不实现抽象类和接口中的方法

属性可以是final的，也可以是static的，不能用default修饰
可以有static方法,可以直接方法

可以有构造方法，但是不能实例化


接口
接口可以多继承
默认的方法是public abstract
default方法不能是抽象的
不能有proteced和private方法

属性默认是final的只能使用public修饰，也可以是static的

没有构造方法，不能实例化






# set集合的不重复怎么实现

add()方法后，值作为key放到了hashmap中,value是一个Object的虚拟值
调用了hashmap的put()
又调用了putVal()
新添加的元素不会覆盖旧元素

>首先根据key的hashCode()返回值决定该Entry的存储位置，如果两个key的hash值相同，那么它们的存储位置相同。如果这个两个key的equals比较返回true。那么新添加的Entry的value会覆盖原来的Entry的value，key不会覆盖。且HashSet中add()中 map.put(e, PRESENT)==null 为false，HashSet添加元素失败。因此,如果向HashSet中添加一个已经存在的元素，新添加的集合元素不会覆盖原来已有的集合元素。


# ArrayList和 LinkedList 比较

都实现了List接口
非线程安全，允许重复
ArrayList
基于动态数组
新加入的对象放在数组的尾部
使用数组，查询速度快(时间复杂度O(1))
插入删除时需要移动当前索引后面所有的元素，速度慢，时间复杂度O(n)
数组扩容，每次扩容后的大小为之前的1.5倍，之后复制全部元素，很耗时

最好初始化时传入大小

LinkedList
基于链表
新加入的作为最后一个节点链接在链表上
查找元素，从头到尾遍历，时间复杂度O(n/2)
插入删除移动指针，时间复杂度O(1)
双向链表，不需要扩容，直接在前后添加

# ArrayList和Vector的区别
都是有序不可重复的集合




# Spring IOC和Spring AOP比较

# mysql和Oracle的区别
(1)对事务的提交
MySQL默认是自动提交，而Oracle默认不自动提交，需要用户手动提交，需要在写commit;指令或者点击commit按钮
(2) 分页查询
MySQL是直接在SQL语句中写"select... from ...where...limit  x, y",有limit就可以实现分页;而Oracle则是需要用到伪列ROWNUM和嵌套查询
(3) 事务隔离级别
MySQL是read commited的隔离级别，而Oracle是repeatable read的隔离级别，同时二者都支持serializable串行化事务隔离级别，可以实现最高级别的
读一致性。每个session提交后其他session才能看到提交的更改。Oracle通过在undo表空间中构造多版本数据块来实现读一致性，每个session
查询时，如果对应的数据块发生变化，Oracle会在undo表空间中为这个session构造它查询时的旧的数据块
MySQL没有类似Oracle的构造多版本数据块的机制，只支持read commited的隔离级别。一个session读取数据时，其他session不能更改数据，但
可以在表最后插入数据。session更新数据时，要加上排它锁，其他session无法访问数据
(4) 对事务的支持
MySQL在innodb存储引擎的行级锁的情况下才可支持事务，而Oracle则完全支持事务
(5) 保存数据的持久性
MySQL是在数据库更新或者重启，则会丢失数据，Oracle把提交的sql操作线写入了在线联机日志文件中，保持到了磁盘上，可以随时恢复
(6) 并发性
MySQL以表级锁为主，对资源锁定的粒度很大，如果一个session对一个表加锁时间过长，会让其他session无法更新此表中的数据。
虽然InnoDB引擎的表可以用行级锁，但这个行级锁的机制依赖于表的索引，如果表没有索引，或者sql语句没有使用索引，那么仍然使用表级锁。
Oracle使用行级锁，对资源锁定的粒度要小很多，只是锁定sql需要的资源，并且加锁是在数据库中的数据行上，不依赖与索引。所以Oracle对并发性的支持要好很多。

(13)最重要的区别
MySQL是轻量型数据库，并且免费，没有服务恢复数据。
Oracle是重量型数据库，收费，Oracle公司对Oracle数据库有任何服务。
(13) 自动增长的数据类型处理
MYSQL有自动增长的数据类型，插入记录时不用操作此字段，会自动获得数据值。ORACLE没有自动增长的数据类型，需要建立一个自动增长的序列号，插入记录时要把序列号的下一个值赋于此字段。
```sql
CREATE SEQUENCE 序列号的名称 (最好是表名+序列号标记) INCREMENT BY 1
START WITH 1 MAXVALUE 99999 CYCLE NOCACHE;
```
其中最大的值按字段的长度来定, 如果定义的自动增长的序列号 NUMBER(6) , 最大值为999999
INSERT 语句插入这个字段值为: 序列号的名称.NEXTVAL

(14) 单引号的处理
MYSQL里可以用双引号包起字符串，ORACLE里只可以用单引号包起字符串。在插入和修改字符串前必须做单引号的替换：把所有出现的一个单引号替换成两个单引号。



# Mybatis的使用流程
# http协议
# 模拟请求 http
# `==`和`equals()`的区别
==对于基本数据类型比较的是值

equals()方法是Object中的方法，里面使用的是`==`作比较
String 重写了equals()方法






