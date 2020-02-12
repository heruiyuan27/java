# String（java.lang）

- 双引号“字符串”都是 String 类的对象  
- 字符串不可变，其值在创建后不能被更改
- 虽然 String 的值不可变，但是可以被共享
- 字符串效果上相当于字符数组( char[] )，但是底层原理是字节数组( byte[] )  

## 构造方法

| 方法名                    | 说明                                      |
| ------------------------- | ----------------------------------------- |
| public String()           | 创建一个空白字符串对象，不含有任何内容    |
| public String(char[] chs) | 根据字符数组的内容，来创建字符串对象      |
| public String(byte[] bys) | 根据字节数组的内容，来创建字符串对象      |
| String s = “abc”;         | 直接赋值的方式创建字符串对象，内容就是abc |

- 构造方法创建
通过 new 创建的字符串对象，每一次 new 都会申请一个内存空间，虽然内容相同，但是地址值不同
- 直接赋值方式创建
以“    ”方式给出的字符串，只要字符序列相同(顺序和大小写)，无论在程序代码中出现几次，JVM 都只会建立一个 String 对象，并在字符串池中维护
- 如果通过string进行拼接操作，是耗时和浪费内存空间的【常量池】

## ==

- 比较基本数据类型：比较的是具体的值
- 比较引用数据类型：比较的是对象地址值  

## equals()  

s1.equals(s2)  

比较两个字符串内容是否相同、区分  

# StringBuilder（java.lang）

StringBuilder 是一个可变的字符串类，我们可以把它看成是一个容器，这里的可变指的是 StringBuilder 对象中的
内容是可变的  

## 构造方法

| 方法名                           | 说明                                       |
| -------------------------------- | ------------------------------------------ |
| public StringBuilder()           | 创建一个空白可变字符串对象，不含有任何内容 |
| public StringBuilder(String str) | 根据字符串的内容，来创建可变字符串对象     |

## 常用方法

| 方法名                                 | 说明                                                |
| -------------------------------------- | --------------------------------------------------- |
| public StringBuilder append (任意类型) | 添加数据，并返回对象本身                            |
| public StringBuilder reverse()         | 返回相反的字符序列                                  |
| public int length()                    | 返回长度，实际存储值                                |
| public String toString()               | 通过toString()就可以实现把StringBuilder转换为String |

# StringBuilder和String相互转换

StringBuilder→String  StringBuilder的toString方法

String→StringBuilder  StringBuilder的构造方法

```java
StringBuilder sb=new StringBuilder("java");
sb.append("hello").append("world");
System.out.println(sb);
sb.reverse();
System.out.println(sb);
```

