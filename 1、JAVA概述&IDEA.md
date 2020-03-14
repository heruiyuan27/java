# JAVA概述

## 介绍

跨平台原理 win mac linux

通过jvm ，即java虚拟机实现

JRE(java runtime environment)=jvm+核心类库

JDK(java development kit)=jre+javac.exe+java.exe

##简单操作

e:

dir

cd cd1\2 前进 /多级前进

cd.. cd\   回退 /多级回退

cls清屏

exit

--------------------------------

java源程序 .java

↓

编译器compi

↓

java字节码文件 .class  →JVM

------------------

eg

javac HelloWorld.java

java  HelloWorld

-------------------------

非法字符一般是中英文符号问题

1.至少要有一个自定义类

2.有且仅有一个主类 main（）

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

无参构造

有参构造

get/set方法









