# Math（lang静态）

Math类中无构造方法，但内部的方法都是==静态==的，则可以通过 ==类名.== 进行调用  

属于java.lang 不用import

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

# System（lang静态）

属于java.lang 不用import

| 方法名                                 | 说明                                         |
| -------------------------------------- | -------------------------------------------- |
| public static void exit(int status)    | 终止当前运行的 Java 虚拟机，非零表示异常终止 |
| public static long currentTimeMillis() | 返回当前时间(以毫秒为单位)                   |

计时功能:

long start=System.currentTimeMillis()

long end=System.currentTimeMillis()

long end-long start

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

重写后，比较内容

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

# 冒泡排序

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

# Array（util静态）

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

==工具类设计思想==
1、**构造方法用 private 修饰**
2、成员用 public static 修饰  

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

# Date（静态）

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

