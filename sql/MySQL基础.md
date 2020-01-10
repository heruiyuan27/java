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

## DDL









