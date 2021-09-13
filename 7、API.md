| 包名      | 说明                                                         |
| :-------- | :----------------------------------------------------------- |
| java.lang | 该包提供了Java编程的基础类，例如 Object、Math、String、StringBuffer、System、Thread等，                                不使用该包很难编写Java代码了。 |
| java.util | 该包提供了包含集合框架、遗留的集合类、事件模型、日期和时间实施、国际化和                                                              各种实用工具类（字符串标记生成器、随机数生成器和位数组）。 |

#工具类设计思想

1、**构造方法用 private 修饰**
2、**成员用 public static 修饰  **

# Random（java.util非静态）

创建对象

```java
Random r = new Random();
```

产生随机数

```java
int num = r.nextInt(10);
//10代表的是一个范围，如果括号写10，产生的随机数就是0-9
```

#冒泡排序

轮数：5个数，4轮，每轮确定一个最大或者最小的

每轮：相邻比较大小

```java
public class Maopao {
    public static void main(String[] args) {
        int arr[] = {13, 65, 11, 99, 47};

        for (int x = 0; x < arr.length - 1; x++) {
            for (int i = 0; i < arr.length - 1 - x; i++) {
                if (arr[i] < arr[i + 1]) {
                    int temp = arr[i];
                    arr[i] = arr[i + 1];
                    arr[i + 1] = temp;
                }
            }
        }

        System.out.println(splice(arr));
    }

    public static String splice(int[] arr) {
        StringBuilder sb = new StringBuilder();
        sb.append("[");
        for (int i = 0; i < arr.length; i++) {
            if (i < arr.length - 1) {
                sb.append(arr[i]);
                sb.append(",");
            } else {
                sb.append(arr[i]);
            }
        }
        sb.append("]");
        return sb.toString();
    }
}
```

# Arrays（util静态）

| 方法名                                 | 说明                               |
| -------------------------------------- | ---------------------------------- |
| public static String toString(int[] a) | 返回指定数组的内容的字符串表示形式 |
| public static void sort(int[] a)       | 按照数字顺序排列指定的数组         |

```java
import java.util.Arrays;

public class ArrayDemo {
    public static void main(String[] args) {
        int arr[] = {13, 65, 11, 99, 47};
        Arrays.sort(arr);
        System.out.println(Arrays.toString(arr));
    }
}
```

# Date（util静态）

| 方法名                 | 说明                                                         |
| ---------------------- | ------------------------------------------------------------ |
| public Date()          | 分配一个 Date对象，并初始化，以便它代表它被分配的时间，精确到毫秒 |
| public Date(long date) | 分配一个 Date对象，并将其初始化为表示从标准基准时间起指定的毫秒数 |

| 方法名                         | 说明                                                  |
| ------------------------------ | ----------------------------------------------------- |
| public long getTime()          | 获取的是日期对象从1970年1月1日 00:00:00到现在的毫秒值 |
| public void setTime(long time) | 设置时间，给的是毫秒值                                |

# SimpleDateFormat（util静态）

## date 2 str

```java
Date d=new Date();//日期对象
SimpleDateFormat sdf=new SimpleDateFormat();//日期格式对象
String s=sdf.format(d);
System.out.println(s);
```

##str 2 date

```java
String ss="2019-02-18 15:30:30";
SimpleDateFormat sdf2=new SimpleDateFormat("yyyy年MM月dd日 HH:mm:ss");
Date dd=sdf2.parse(ss);
System.out.println(dd);
```

# Calendar(util非静态)

```java
/*
   获取任何一年的二月有多少天
*/
System.out.println("please input the year");
Scanner sc=new Scanner(System.in);
int year=sc.nextInt();
Calendar c = Calendar.getInstance();//日历对象
c.set(year,2,1);//set方法，3月1日
c.add(Calendar.DATE,-1);//add方法，字段，+-数值
System.out.println(c.get(Calendar.DATE));

```

# java.lang

属于java.lang 不用import

# Math

Math类中无构造方法，但是内部的方法都是==静态==的，则可以通过 ==类名.== 进行调用  

| 方法名 方法名                                | 说明                                            |
| -------------------------------------------- | ----------------------------------------------- |
| public static int abs(int a)                 | 返回参数的绝对值                                |
| public static double ceil(double a)          | 返回大于或等于参数的最小double值，等于一个整 数 |
| public static double floor(double a)         | 返回小于或等于参数的最大double值，等于一个整 数 |
| public static int round(float a)             | 按照四舍五入返回最接近参数的int                 |
| public static int max(int a,int b)           | 返回两个int值中的较大值                         |
| public static int min(int a,int b)           | 返回两个int值中的较小值                         |
| public static double pow (double a,double b) | 返回a的b次幂的值                                |
| public static double random()                | 返回值为double的正值，[0.0,1.0)                 |

#System

| 方法名                                 | 说明                                         |
| -------------------------------------- | -------------------------------------------- |
| public static void exit(int status)    | 终止当前运行的 Java 虚拟机，非零表示异常终止 |
| public static long currentTimeMillis() | 返回当前时间(以毫秒为单位)                   |

计时功能:

long start=System.currentTimeMillis()

long end=System.currentTimeMillis()

long end-long start

# 基本数据类型包装类

## int 2 str

```java
 int num=1;
 String s=String.valueOf(num);
```

## str 2 int

```java
String str="222";
int y=Integer.parseInt(str);
```

## 自动装箱拆箱

```java
 Integer i=100;//自动装箱
 i+=500;//先拆后装
```

# Object

Object 是类层次结构的根，每个类都可以将 Object 作为超类。所有类都直接或者间接的继承自该类，
换句话说，该类所具备的方法，所有类都会有一份  

## toString

alt+insert 重写toString

```java
@Override
    public String toString() {
        return "Student{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }
```

## equals

alt+insert 重写equals

**不重写情况下，equals比较对象的地址**

**重写后，比较内容**

```java
@Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) return false;
        Student student = (Student) o;
        return age == student.age &&
                Objects.equals(name, student.name);
    }
```

# String

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
  
  ==堆！！！==
  
- 直接赋值方式创建
  以“    ”方式给出的字符串，只要字符序列相同(顺序和大小写)，无论在程序代码中出现几次，JVM 都只会建立一个 String 对象，并在==字符串池==中维护
  
- 如果通过string进行拼接操作，是耗时和浪费内存空间的。堆


## 常用方法

length()

charAt(i)

toCharArray()

s.substring(n, s.length()) + s.substring(0, n);

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

## StringBuffer

线程安全

