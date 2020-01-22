# Math

Math类中无构造方法，但内部的方法都是==静态==的，则可以通过 类名**.**进行调用  

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

# System

属于java.lang 不用import

| 方法名                                 | 说明                                         |
| -------------------------------------- | -------------------------------------------- |
| public static void exit(int status)    | 终止当前运行的 Java 虚拟机，非零表示异常终止 |
| public static long currentTimeMillis() | 返回当前时间(以毫秒为单位)                   |

计时功能:

long start=System.currentTimeMillis()

long end=System.currentTimeMillis()

long end-long start

# object

Object 是类层次结构的根，每个类都可以将 Object 作为超类。所有类都直接或者间接的继承自该类，
换句话说，该类所具备的方法，所有类都会有一份  

## toString

alt+insert 重写toString

```
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

不重写情况下，equals比较对象的地址

重写后，比较内容

```
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

# Array

```java
import java.util.Arrays;

public class ArrayDemo {
    public static void main(String[] args) {
        int arr[] = {13, 65, 11, 99, 47};
        Arrays.sort(arr);
        System.out.println(Arrays.toString(arr));
    }
}
import java.util.Arrays;
```

工具类设计思想
1、构造方法用 private 修饰
2、成员用 public static 修饰  