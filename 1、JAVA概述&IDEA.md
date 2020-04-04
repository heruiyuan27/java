# JAVA概述

## 介绍

跨平台【win mac linux】原理:通过JVM【java虚拟机】实现

JRE(java runtime environment)=JVM+核心类库

JDK(java development kit)=JRE+javac.exe+java.exe

-------------------------

java源程序 .java

​			↓

编译器compiler

​			↓

java字节码文件 .class

​			↓

 		 JVM

------------------

eg.

javac HelloWorld.java

java  HelloWorld

-------------------------

- 非法字符一般是中英文符号问题

1. 至少要有一个自定义类

2. 有且仅有一个主类 main（）

##DOS简单操作

dir,cd, md,rd,copy,del等

### dir

```
dir C:\develop\Java\jdk-11.0.5\bin\javac.exe
dir C:\users\hery
dir /p
```

当前目录：命名提示符所在的路径 C:\Users\Hery>

父目录：     ..

当前目录：  .

根目录:        \  

相对路径 C:\Users\Hery>dir PycharmProjects

绝对路径 C:\Users\Hery>dir C:\Users\Hery\PycharmProjects

###cd

cd命令只能进入当前盘符中的目录，其中“cd \”为返回到根目录，“cd..”为返回到上一层目录。

cd 或cd1\2 →前进 或多级前进

### md

举例：md temp

表示在当前盘符下建立一个名为temp的目录。

### rd

举例：rd temp

表示删除当前路径下的temp目录，需要注意的是，此命令只能删除空目录。

### copy

举例1：copy c:\*.com d:\"

表示将c盘根目录下所有扩展名为com的文件拷贝到d盘根目录中。

举例2：copy c:\autoexec.bat c:\autoexec.bak

表示将autoexec.bat文件复制成为扩展名为bak的文件。输入dir命令，可以发现此变化。

### del

举例：del c:\ *.bak  /p

表示删除当前目录下所有扩展名为bak的文件，

参数/p表示可以使用户在删除多个文件时对每个文件都显示删除询问。

###其他

cls清屏

exit

#文件结构

Project

Module→==project structure==

Package

Class

1、创建一个空项目（JavaSE_Code)  →IdeaProjects目录下

2、创建一个新模块→myClass

3、在模块下src文件夹创建包

4、在包下新建类

#快捷键

| 快捷键             | 功能                                   |
| ------------------ | -------------------------------------- |
| ==Alt+Enter==      | 导入包，自动修正代码                   |
| Ctrl+Y             | 删除光标所在行                         |
| Ctrl+D             | 复制光标所在行的内容，插入光标位置下面 |
| ==Ctrl+Alt+L==     | 格式化代码                             |
| ==Ctrl+/==         | 单行注释                               |
| ==Ctrl+Shift+/==   | 选中代码注释，多行注释，再按取消注释   |
| Alt+Shift+上下箭头 | 移动当前代码行                         |

psvm=public static void main（String[] args）

sout=System.out.println（）

修改相同文字：shift+F6

#Debug

设置断点

F7 go ahead

- Console查看输出，或者是键盘录入
- Frames查看调用方法
- Variables查看变量



#ALT+INSERT

无参构造+有参构造

get/set方法

equals()

toString()











