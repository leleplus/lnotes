MyBatis从入门到放弃
-----
作者:乐乐

## 一、`MyBatis`入门
### (二).`MyBatis`是什么
* MyBatis是一个简化和实现了Java 数据持久化层(persistence layer)的开源框架，它抽象了大量的JDBC冗余代码，并提供了一个简单易用的API和数据库交互方式。
* MyBatis的前身是iBATIS，iBATIS于2002年由ClintonBegin创建。MyBatis3是iBATIS的全新设计，支持注解和Mapper(映射器)。
* MyBatis流行的主要原因在于它的简单性和易使用性。
* MyBatis作用在三层架构的Dao层
* iBATIS一词来源于internet和abatis的组合，是一个在2002年发起的开放源代码项目。于2010年6月16号被谷歌托管，改名为MyBatis。
* [ibatis的官网](http://ibatis.apache.org/) 进去官网会看到下面提示:
	apache ibatis is retired at the apache software foundation (2010/06/16)
	the original project team has moved to mybatis hosted at google code. see http://www.mybatis.org/ for more.
	然而http://www.mybatis.org/这个地址一直处于打不开状态...
	但是我们最终是可以在github中找到mybatis的相关下载的页面
	[mybatis](https://github.com/mybatis/mybatis-3)在github中的地址
	最新版本的mybatis的[下载地址](https://github.com/mybatis/mybatis-3/releases)
	[doc文档下载](http://www.mybatis.org/mybatis-3/)

### (三).数据持久化层
* 将从数据库查询到的数据生成所需要的Java对象；
* 将Java对象中的数据通SQL持久化到数据库中。

* MyBatis通过抽象底层的JDBC代码，自动化SQL结果集产生Java对象、Java对象的数据持久化数据库中的过程使得对SQL的使用变得容易。

### (四).`MyBatis`流行起来的原因
当前有很多Java实现的持久化框架，而`MyBatis`更流行
#### 1.消除了大量的JDBC冗余代码
* Java通过JDBC的API来操作关系型数据库，但是JDBC是一个非常底层的API,我们需要书写大量的代码来完成对数据库的操作。例如:一个数据插入操作
* 但是使用mybatis来完成相同的插入操作要简单方便灵活的多:
	* 第一步:在SQLMapper映射配置文件中配置SQL语句，假定为StudentMapper.xml
		```xml
		<insert id="insertStudent" parameterType="Student">
			INSERT INTO STUDENTS(ID,NAME,EMAIL)
			VALUES(#{id},#{name},#{email})
		</insert>
		```
	* 第二步:创建一个`StudentMapper`接口
		```java
		public interface StudentMapper{
			void insertStudent(Student student);
		}
		```
	* 第三步:编写java代码完成插入操作
		```java
		SqlSession session = getSqlSessionFactory().openSession();

		StudentMapper mapper = session.getMapper(StudentMapper.class);

		mapper.insertStudent(student);
		```

#### 2.低的学习曲线
MyBatis能够流行的首要原因之一在于它学习和使用起来非常简单，它取决于你Java和 SQL方面的知识。如果开发人员很熟悉Java和SQL，他们会发现MyBatis入门非常简单。
#### 3.很好地与传统数据库协同工作
类比其他ORM框架，例如hibernate，mybatis可以更加灵活的和数据库交互，sql语句掌握在程序员手里，可以灵活修改，而hibernate框架则是需要将实体类完全映射到数据到表中，这使得修改起来比较麻烦。
#### 4.接受SQL语句
类比其他ORM框架，例如hibernate，hibernate框架推荐让框架自动生成sql语句，这样以来就不能完全利用到数据库的一些特有的特性。而mybatis框架则是推荐程序自己控制sql语句，这样就可以充分利用数据库特有的特性并且可以准备自定义的查询。
#### 5.提供了与Spring框架的集成支持
MyBatis提供了与Spring框架的集成支持，这将进一步简化MyBatis的使用
#### 6.提供了与第三方缓存类库的集成支持
MyBatis有内建的SqlSession级别的缓存机制，用于缓存Select语句查询出来的结果。除此之外，MyBatis提供了与多种第三方缓存类库的集成支持，如EHCache，OSCache等。
#### 7.更好的性能
MyBatis支持数据库连接池，消除了为每一个请求创建一个数据库连接的开销。
MyBatis提供了内建的缓存机制，在SqlSession级别提供了对SQL查询结果的缓存。
即:如果你调用了相同的select查询，MyBatis 会将放在缓存的结果返回，而不会去再查询数据库。
### (五).`MyBatis`核心配置
`MyBatis`中几个重要的组成部分
	* 框架总配置文件：`mybatis-config.xml`
	* sql语句映射文件：`XxxxMapper.xml`
		`Xxxx`一般为实体类的名字
	* 映射接口`XxxxMapper.java`
	接口中有定义方法，调用方法，执行`XxxxMapper.xml`文件中对应的sql语句
	* `SqlSessionFactory`类型对象
		负责产生`SqlSession`对象，
		mybatis框架读取mybatis-config.xml文件即可创建出该对象。
	* `SqlSession`类型对象
		负责动态创建映射接口`XxxxMapper.java`的实现类对象，使用该实现类对象，调用方法即可执行对应的`sql`语句。
#### 1.核心包
mybatis的核心包只有一个`mybatis-3.x.x.jar`,另外还有一些**可选**的依赖包(日志、代理等),都可以去下载
#### 2.`MyBatis`的两个配置文件
##### (1).`MyBatis`的配置文件`mybatis-config.xml`
* 配置内容包括数据库连接信息、类型别名、映射文件路径等
* 特点:
	* 名字固定
	* 位置:`src/`
* 示例:
```xml
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE configuration PUBLIC "-//mybatis.org//DTD Config 3.0//EN" "http://mybatis.org/dtd/mybatis-3-config.dtd">
<configuration>
	<typeAliases>
		<typeAlias alias="Student" type="com.briup.pojo.Student" />
	</typeAliases>
	<environments default="development">
		<environment id="development">
			<transaction Manager type="JDBC" />
			<dataSource type="POOLED">
				<!--
				<property name="driver" value="com.mysql.jdbc.Driver" />
				<property name="url" value="jdbc:mysql://localhost:3306/test" />
				-->
				<property name="driver" value="oracle.jdbc.driver.OracleDriver" />
				<property name="url" value="jdbc:oracle:thin:@127.0.0.1:1521:XE" />
				<property name="username" value="test" />
				<property name="password" value="test" />
			</dataSource>
		</environment>
	</environments>
	<mappers>
		<mapper resource="com/briup/pojo/StudentMapper.xml" />
	</mappers>
</configuration>
```

##### (2).`MyBatis`的映射文件`XxxxMapper.xml`
* 映射内容包括Xxxx类所对应数据库表的各种增、删、改、查、的sql语句
	例如`StudentMapper.xml`文件中是`Student`类对应的表的各种`select insert update delete`的sql语句
* 特点:
	* 名字一般为`XxxxMapper.xml`,`Xxxx`是对应类的名字
	* 位置不固定,一般放到一个专门的package里面
* 示例:
```xml
<?xml version="1.0" encoding="utf-8"?>
<!DOCTYPE mapper PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN" "http://mybatis.org/dtd/mybatis-3-mapper.dtd">
<mapper namespace="com.briup.pojo.StudentMapper">
	<resultMap type="Student" id="StudentResult">
		<id property="id" column="id" />
		<result property="name" column="name" />
		<result property="email" column="email" />
	</resultMap>
	<select id="findAllStudents" resultMap="StudentResult">
		SELECT * FROM STUDENTS
	</select>
	<select id="findStudentById" parameterType="int" resultType="Student">
		SELECT ID AS STUDID, NAME, EMAIL
		FROM STUDENTS WHERE ID=#{Id}
	</select>
	<insert id="insertStudent" parameterType="Student">
		INSERT INTO STUDENTS(ID,NAME,EMAIL)
		VALUES(#{id },#{name},#{email})
	</insert>
</mapper>
```

#### 3.`MyBatis`中的映射接口
* `XxxxMapper.java`文件是对`XxxxMapper.xml`中的sql语句进行映射,mybatis中除了必须的jar包、各种xml配置文件之外,一般还需要有调用sql语句执行的接口`XxxxMapper.java`
* 示例:
	`StudentMapper`接口就是对`StudentMapper.xml`文件中的SQL语句进行映射
```java
public interface StudentMapper{
	List<Student> findAllStudents();
	Student findStudentById(Integer id);
	void insertStudent(Student student);
}
```
* 注:
	* 接口中的方法的名字和XML文件中，定义SQL映射语句的名称要相同
	* 接口不需要去实现,因为mybatis中提供了相应的方式在运行期间动态生成该接口的实现类对象.

#### 4.`MyBatis`中的`SqlSession`接口和`sqlSessionFactory`接口
* `SqlSession`接口的实现类对象是mybatis中最重要的一个对象,我们可以使用该对象动态获得`XxxxMapper.java`接口的实现类对象,然后就可以调用到`XxxxMapper.java`接口中方法所映射的sql语句(在xml文件中配置的sql语句)。
* `sqlSessionFactory`接口的实现类对象是一个工厂对象,专门负责来产生`SqlSession`对象的
* 例如:
	```java
	InputStream in = Resources.getResourceAsStream("mybatis-config.xml");

	SqlSessionFactory sqlSessionFactory = new SqlSessionFactoryBuilder().build(in);

	SqlSession session = sqlSessionFactory.openSession();
	```
	* 第一种执行sql语句的方式  通过`XxxxMapper`接口的实现类对象来调用,动态获得`XxxxMapper`接口的实现类
		```java
		StudentMapper mapper = session.getMapper(StudentMapper.class);

		mapper.insertStudent(new Student(1,"tom","123@.qq.com"));
		```
	* 第二种执行sql语句的方式  执行调用`XxxxMapper.xml`中写好的sql语句
		(也可以不通过Mapper接口执行映射的SQL,但是，推荐使用 Mapper接口来执行)
		```java
		session.selectOne("com.briup.pojo.StudentMapper.findStudentById",1);
		```

### (五).`MyBatis`核心配置

