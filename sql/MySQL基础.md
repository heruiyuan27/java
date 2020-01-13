# MySQL数据库软件

1. 安装
	
	* 参见《MySQL基础.pdf》
2. 卸载
	1. 去mysql的安装目录找到my.ini文件
		* 复制 datadir="C:/ProgramData/MySQL/MySQL Server 5.5/Data/"
	2. 卸载MySQL
	3. 删除C:/ProgramData目录下的MySQL文件夹。
	
3. 配置
	* MySQL服务启动
		1. 手动。
		2. cmd--> services.msc 打开服务的窗口
		3. 使用管理员打开cmd
			* net start mysql : 启动mysql的服务
			* net stop mysql:关闭mysql服务
		
	* ==MySQL登录==
		
		1. ==mysql -uroot -p==密码 （默认本地MySQL）
		
		2. ==mysql -hip地址 -uroot -p==连接目标的密码 
		
	   eg：mysql -h192.168.1.101 -uroot -p
		
		   查看本地ip ：ipconfig
		
		3. mysql --host=ip地址 --user=root --password=连接目标的密码
		
	* MySQL退出
		1. exit
		2. quit
	
	* MySQL目录结构
		1. ==MySQL安装目录==：basedir="C:\Program Files\MySQL\\"
			* 配置文件 my.ini
			* bin→配置到环境变量下
		2. ==MySQL数据目录==：datadir="C:\ProgramData\MySQL\MySQL Server 5.5\data"
		  * 几个概念
		  	* 数据库：文件夹
		  	* 表：文件
		  	* 数据：数据

# SQL

Structured Query Language：结构化查询语言

定义了操作所有关系型数据库的规则。每一种数据库操作的方式存在不一样的地方，称为“方言”。

--------------------------------------

SQL 语句可以单行或多行书写，以**分号结尾**。

MySQL 数据库的 SQL 语句**不区分大小写**，**关键字**建议使用**大写**。

3 种注释

* 单行注释: -- 注释内容 或 # 注释内容(mysql 特有) 
* 多行注释: /* 注释 */

---------------------------

SQL分类
1) DDL(Data Definition Language)数据定义语言
	用来定义数据库对象：数据库，表，列等。关键字：create, drop,alter 等
2) DML(Data Manipulation Language)数据操作语言
	用来对数据库中表的数据进行增删改。关键字：insert, delete, update 等
3) DQL(Data Query Language)数据查询语言
	用来查询数据库中表的记录(数据)。关键字：select, where 等
4) DCL(Data Control Language)数据控制语言(了解)
	用来定义数据库的访问权限和安全级别，及创建用户。关键字：GRANT， REVOKE 等

--------------------

## DDL操作数据库、表

### 1操作数据库 CRUD+use

1. **C(Create):创建**

创建数据库：
* ==create database 数据库名称==;
* create database if not exists 数据库名称;
* create database 数据库名称==character set 字符集名==;
* 练习： 创建db4数据库，判断是否存在，并制定字符集为gbk
		* create database if not exists db4 character set gbk;
2. **R(Retrieve)：查询**
	* 查询所有数据库的名称:
		* ==show databases==;
	* 查询某个数据库的字符集:查询某个数据库的创建语句
		* ==show create database 数据库名称==;
3. **U(Update):修改**
	* 修改数据库的字符集
		* ==alter database 数据库名称 character set 字符集名称==;
4. D(Delete):删除
	* 删除数据库
		* ==drop database 数据库名称==;
	* 判断数据库存在，存在再删除
		* drop database if exists 数据库名称;
5. 使用数据库
	* 查询当前正在使用的数据库名称
		* ==select database()==;
	* 使用数据库
		* ==use 数据库名称==;

### 2操作表CRUD

前提：use db1；使用某个数据库

--------------------------

1. C(Create):创建

   创建表
   ==create table student3==(
   			id int,
   			name varchar(32),
   			age int ,
   			score double(4,1),
   			birthday date,
   			insert_time timestamp
   		);

   ![image-20200111192207010](C:\Users\Hery\Desktop\GitHub\java\image\image-20200111192207010.png)

   	* 复制表：
   		* ==create table 表名 like 被复制的表名==;	 

2. R(Retrieve)：查询
     * ==show tables==; 数据库下的表格
     * ==show create table student==;
     * ==desc 表名==; 具体表格的结构

3. U(Update)：修改

     	1. 修改表名
          	alter table 表名 rename to 新的表名;
     	2. 修改表的字符集

     		alter table 表名 character set 字符集名称;
     	3. 添加一列
     		alter table 表名 add 列名 数据类型;
     	4. 修改列名称 类型
     		alter table 表名 change 列名 新列别 新数据类型;
     		alter table 表名 modify 列名 新数据类型;
     	5. 删除列
     		alter table 表名 drop 列名;

4. D(Delete):删除
		* ==drop table 表名==;
	* drop table  if exists 表名 ;

## DML增删改表中数据

1. 添加数据:

   insert into student (id,name) values(1,'sun')

   insert into student values(2,'zh','man','tju')

2. 删除数据：

   delete from student where id=4;

   delete from student;删除所有

3. 更新数据:

   update student set sex='woman';

   update student set sex='man' where id=2;

   update student set age=1,address='bj' where id=3;

## DQL：查询表中的记录

###语法
select
	字段列表
from
	表名列表
where
	条件列表

group by
	分组字段
having
	分组之后的条件
order by
	排序
limit
	分页限定

### 基础查询

select * from student

select name,age from student

select name as 姓名,age as 年龄 from student

------------------------

select address from student

select ==distinct==  address from student

-------------------------------------------

select math+5 from student

select * ,(math+english) as total from student

### 条件查询

**运算符**：
\> 、< 、<= 、>= 、= 、<>
BETWEEN...AND  :

​		SELECT * FROM student WHERE age BETWEEN 20 AND 30;
IN( 集合) :

​		SELECT * FROM student WHERE age IN (22,18,25);
LIKE(模糊查询)：

| %      | 匹配任意多个字符串 |
| ------ | ------------------ |
| **_ ** | **匹配一个字符**   |

​		select * from student3 where name like '%德%';  

​		select * from student3 where name like '%德'; 

​		select * from student3 where name like '德%';  

​		select * from student3 where name like '_德';  

IS NULL:

​		select * from student3 where english is null;  
and  或 &&
or  或 || 
not  或 !



