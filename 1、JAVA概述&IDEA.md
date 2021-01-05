# JAVA概述

跨平台【win mac linux】原理:通过JVM【java虚拟机】实现

JRE 是Java运行时环境

JRE(java runtime environment)=JVM+Java类库+Java命令

JDK是功能齐全的 Java SDK  

JDK(java development kit)=JRE+编译器javac.exe+⼯具（如 javadoc 和 jdb）  

-------------------------

java源程序 .java

​			↓

编译器javac

​			↓

java字节码文件 .class

​			↓

 		 JVM

eg.

javac HelloWorld.java

java  HelloWorld

-------------------------

- 非法字符一般是中英文符号问题

1. 至少要有一个自定义类

2. 有且仅有一个主类 main（）

#DOS简单操作

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

#IDEA快捷键

##ctrl
Ctrl + F 在当前文件进行文本查找 （必备）
Ctrl + R 在当前文件进行文本替换 （必备）

Ctrl + W 递进式选择代码块。可选中光标所在的单词或段落，连续按会在原有选中的基础上再扩展选中范围（必备）

Ctrl + Y 删除光标所在行 或 删除选中的行 （必备）
Ctrl + D 复制光标所在行 或 复制选择内容，并把复制内容插入光标位置下面 （必备）

Ctrl + E 显示最近打开的文件记录列表 （必备）
Ctrl + N 根据输入的名/类名 查找类文件 （必备）

Ctrl + U 前往当前光标所在的方法的父类的方法 / 接口定义 （必备）
Ctrl + B 进入光标所在的方法/变量的接口或是定义处，等效于 Ctrl + 左键单击 （必备）

Ctrl + / 释光标所在行代码，会根据当前不同文件类型使用不同的注释符号 （必备）

##ctrl+alt
Ctrl + Alt + L 格式化代码，可以对当前文件和整个包目录使用 （必备）
Ctrl + Alt + O 优化导入的类，可以对当前文件和整个包目录使用 （必备）
Ctrl + Alt + T 对选中的代码弹出环绕选项弹出层 （必备）

##ctrl+shift

ctrl+shift+up/down 移动语句

##alt+insert

Alt + Enter IntelliJ IDEA 根据光标所在问题，提供快速修复选择，光标放在的位置不同提示的结果也不同 （必备）
Alt + Insert 代码自动生成，如生成对象的 set / get 方法，构造函数，toString() 等 （必备）

##其他

psvm=public static void main（String[] args）
sout=System.out.println（）
iter
修改相同文字：shift+F6



