# 转型

## 向上转型(upcasting)

注意: parent=child，**父类引用**指向**子类对象**就是向上转型  
1. 等价于：parent=(Parent)child;
2. parent引用的是子类实例
3. parent只能引用与父类成员同名的那些成员

典型多态

1. parent.变量，引用的是父类中的变量【变量：静态绑定
2. parent.成员方法，引用的是子类的方法【方法：动态绑定

```java
Animal a=new Cat();//父类引用指向子类对象,向上转型
a.eat();//方法-动态绑定,猫吃鱼
//a.playGame();动物类没有此方法

System.out.println(a.age);//变量-静态绑定，动物年龄5000
//System.out.println(a.weight);动物类没有此变量
```

## 向下转型(downcasting)

```java
Animal a=new Cat();
Cat c=(Cat)a;
c.eat();
c.playGame();
System.out.println(c.age);
System.out.println(c.weight);
```

注意: child = (Child) parent ；子类型 对象名 = (子类型)父类引用  

1. java检查：parent对象引用的实例是不是子类对象，如果是进行转换。否则引起ClassCastException异常。
2. 检查语句：instanceof 。格式：对象 instanceof  类
3. **child.**变量、**child.**方法：子类的变量或方法。

# 多态

定义：对于同一个消息，同一个类的对象（引用）可以作出不同反映的现象被称为多态性。

实现：Upcasting后，parent对象（引用）通过调用若干个child对象的相同签名的成员方法，
使得若干个child对象体现多态性。

多态：**动态绑定**的结果， 属于**运行**时的现象。 

<img src="C:\Users\Hery\Desktop\GitHub\java\image\image-20200204163931533.png" alt="image-20200204163931533" style="zoom: 33%;" />


多态的前提
- 要有继承或实现关系
- 要有方法的重写
- 要有父类引用指向子类对象 

多态的好处与弊端

- 好处
提高程序的扩展性。
定义方法时候，使用父类型作为参数，在使用的时候，使用具体的子类型参与操作
- 弊端
不能使用子类的特有成员。

## 抽象类及其多态

```java
//抽象类的定义
public abstract class Animal {
    
    //抽象方法的定义
	public abstract void eat();
}

```
抽象类特点：
- 抽象类有 ==抽象方法【没有方法体】==，也可以有==普通方法==
- 抽象类不能实例化
- 抽象类主要是用来派生(derive)子类，且在子类中必须 ==重写抽象类中的所有抽象方法==，实现多态

  如果没有实现，则子类也必须定义为抽象类。
- static 、private 和final修饰符不能修饰抽象方法和抽象类 。

## 接口及其多态

### **接口特点**

- 接口是一种更特殊的抽象类，内部只允许包含==常量==和==抽象方法==。
- 成员变量默认修饰符==public static final==【可以不写
- 成员方法默认修饰符==public abstract==【可以不写
接口规范公共操作方法，不实现具体操作细节。　


```java
public interface Jumping {
    public static final int height=100;
    public abstract void jump();
}
```
### **接口实现类**

- 重写接口抽象方法
- 定义为抽象类

```java
public class Cat implements Jumping {
    @Override
    public void jump() {
        System.out.println("cat jump "+height+" m");
    }
}
```

<img src="C:\Users\Hery\Desktop\GitHub\java\image\image-20200205105942183.png" alt="image-20200205105942183" style="zoom:50%;" />

### **接口默认/静态/私有方法**

```java
public default void run() {
    System.out.println("run");
}
```

- 默认方法不是抽象方法，所以不强制被重写。但是可以被重写，重写的时候去掉default关键字
- public可以省略，default不能省略  

```java
public static void show() {
    System.out.println(height);
}
```

- 静态方法只能通过接口名调用，不能通过实现类名或者对象名调用
- public可以省略，static不能省略  

```java
private void show() {
}  

private static void method() {
}  

```

- 默认方法可以调用私有的静态方法和非静态方法
- 静态方法只能调用私有的静态方法  

# 类和接口的关系

## 继承与实现

1、类和类：==继承关系==【单继承，但是可以多层继】

2、类和接口：==实现关系==【多实现，一个类实现多个接口】

```java
public class InterImpl extends Object implements Inter1,Inter2 {
}
```

3、接口和接口：==继承关系==【多继承】

```java
public interface Inter3 extends Inter1,Inter2 {
}
```

抽象类和接口的区别：

- 抽象类：
变量,常量；有构造方法；有抽象方法,也有非抽象方法【普通类+抽象方法】
- 接口：
常量；抽象方法  

## 参数传递

类名作为形参和返回值：该类对象

抽象类作为形参和返回值  ：子类对象

接口名作为形参和返回值  ：实现类对象

# 内部类

- 内部类可以直接访问外部类的成员，包括私有
- 外部类要访问内部类的成员，必须创建对象  

##  成员内部类

==public Inner==：

Outer.Inner oi = new Outer().new Inner();  

------------------------------------

==private Inner==：【通过Outer里的public方法访问成员内部类private Inner】

```java
public class Outer {
    private int n = 1;

    private class Inner {
        public void showOut() {
            System.out.println(n);
        }
    }

    public void showInner() {
        Inner i = new Inner();
        i.showOut();
    }
}
```

## 局部内部类

局部内部类是在方法中定义的类  

```java
public class Outer {

    private int n = 10;

    public void method() {
        class Inner {

            public void show() {
                System.out.println(n);

            }
        }

        Inner i=new Inner();
        i.show();
    }
}
```

局部内部类，外界是无法直接使用，需要在方法内部创建对象并使用
该类可以直接访问外部类的成员，也可以访问方法内的局部变量  

## 匿名内部类（重要）

通常使用接口方式：

1、创建实现类

2、接口引用 →实现类对象（接口多态方式）

-------------------------------------------

匿名方式不用通过创建具体类

直接得到不同override的对象

【接口&抽象类】

```java
new Jumping() {//接口实现类对象
    @Override
    public void jump() {
        System.out.println("dog can jump");
    }
}
```

```java
public class Test {
    public static void main(String[] args) {
        new Animal(){//抽象类子类对象
            @Override
            public void eat() {
                System.out.println("cat eat fish");
            }
        }.eat();
    }
}
```

# Lambda

Lambda表达式是函数式思想的体现  

格式：
==(形式参数) -> {代码块}==

省略规则

- 参数类型可以省略。但是有多个参数的情况下，不能只省略一个。
- 如果参数有且仅有一个，那么小括号可以省略
- 如果代码块的语句只有一条，可以省略大括号和分号，和return关键字  

使用前提

- 使用Lambda必须要有接口，并且要求接口中有且仅有一个抽象方法
- 必须有上下文环境，才能推导出Lambda对应的接口
	
  根据**局部变量的赋值**得知Lambda对应的接口
  

Runnable r = () -> System.out.println("Lambda表达式");	  

​	   根据**调用方法的参数**得知Lambda对应的接口

new Thread(() -> System.out.println("Lambda表达式")).start();  

## Lambda和匿名内部类的区别

- 实现原理不同
  匿名内部类：编译之后，产生一个单独的.class字节码文件
  Lambda表达式：编译之后，没有一个单独的.class字节码文件。对应的字节码会在运行的时候动态生成  
  
- 所需类型不同
  匿名内部类：可以是接口，也可以是抽象类，还可以是具体类（具体类也要重写方法）
  Lambda表达式：只能是接口，且仅有一个抽象方法【==函数式接口==@FunctionalInterface  

```java
public class Demo1 {//函数式接口作为方法参数
    public static void main(String[] args) {
        startThread(new Runnable() {
            @Override
            public void run() {
                System.out.println(Thread.currentThread().getName()+"线程启动了");
            }
        });
        System.out.println("-------");
        startThread(()-> System.out.println(
        	Thread.currentThread().getName()+"线程启动了")
        );

    }
    private static void startThread(Runnable r){
        new Thread(r).start();
    }
}
```
```java
public class Demo2 {//函数式接口作为返回值
    public static void main(String[] args) {
        ArrayList<String> array = new ArrayList<String>();
        array.add("cccc");
        array.add("aa");
        array.add("b");
        array.add("ddd");
        System.out.println("排序前：" + array);
        Collections.sort(array, getCom());
        System.out.println("排序后：" + array);
    }

    private static Comparator<String> getCom(){
/*        return new Comparator<String>(){
            @Override
            public int compare(String s1, String s2) {
                return s1.length()-s2.length();
            }
        };*/
        return (s1,s2)->s1.length()-s2.length();
    }
}
```

## 方法引用

通过方法引用来使用已经存在的方案  

```java
public class Test {
    public static void main(String[] args) {
        //匿名内部类，创建接口实现类对象，重写抽象方法
        useStr2int(new Str2int() {
            @Override
            public int convert(String s) {
                return Integer.parseInt(s);
            }
        });
        //lambda
        useStr2int(s ->  Integer.parseInt(s)  );
        //引用方法：类方法
        useStr2int(Integer::parseInt);
    }

    private static void useStr2int(Str2int inter){
        int num=inter.convert("10086");
        System.out.println(num);
    }
}
```

```java
public class Test {
    public static void main(String[] args) {
        usePrintable(new Printable() {
            //匿名内部类，创建接口实现类对象，重写抽象方法
            @Override
            public void printUpperCase(String s) {
                System.out.println(s.toUpperCase());
            }
        });
        System.out.println("----------");

        usePrintable(
            //lambda
                s -> System.out.println(s.toUpperCase()));

        System.out.println("----------");
        //引用方法：对象方法
        usePrintable(new PrintUp()::printUp);

    }
    private static void usePrintable(Printable p){
        p.printUpperCase("hello");

    }
}
```

# 函数式接口

【==函数式接口==@FunctionalInterface 】

##Supplier提供

```java
public class SupplierDemo {
    public static void main(String[] args) {
        int[] array={12,56,88,6,99};
//匿名内部类:重写get方法
        int num=getMax(new Supplier<Integer>() {
            @Override
            public Integer get() {
                int max=array[0];
                for(int i=0;i<array.length;i++){
                    if(array[i]>max){
                        max=array[i];
                    }
                }
                return max;
            }
        });
        System.out.println(num);
//lambda
        int n=getMax(()->{
            int max=array[0];
            for(int i=0;i<array.length;i++){
                if(array[i]<max){
                    max=array[i];
                }
            }
            return max;
        });
        System.out.println(n);
    }
    private static int getMax(Supplier<Integer> sup){
        return sup.get();
    }
}
```

## Consumer消费

```java
public class ConsumerDemo {
    public static void main(String[] args) {
        String[] strArray = {"林青霞,30", "张曼玉,35", "王祖贤,33"};

        printInfo(strArray, new Consumer<String>() {
            //匿名内部类:重写accept方法
            @Override
            public void accept(String s) {
                System.out.print(s.split(",")[0]+"的年龄是");
            }
        }, //lambda
            s -> System.out.println(s.split(",")[1]));
    }

    private static void printInfo(String[] strarray, Consumer<String> con1,Consumer<String> con2){
        for(String s:strarray){
            con1.andThen(con2).accept(s);
        }
    }
}
```

##Predicate判断

```java
public class PredicateDemo {
    public static void main(String[] args) {
        String[] strArray = {"林青霞,30", "柳岩,34", "张曼玉,35", "貂蝉,31", "王祖贤,33"};
        ArrayList<String> array=method(strArray, new Predicate<String>() {
            //匿名内部类:重写test方法
            @Override
            public boolean test(String s) {
                return s.split(",")[0].length()>=2;
            }
        },
            //lambda                          
            s -> Integer.parseInt(s.split(",")[1])>32);
        for(String s:array){
            System.out.println(s);
        }
    }
    private static ArrayList<String> method(String[] strArray, Predicate<String> p1, Predicate<String> p2){
        ArrayList<String> array=new ArrayList<>();
        for(String s:strArray){
            if(p1.and(p2).test(s)){
                array.add(s);
            }
        }
        return array;
    }
}
```

## Function转换

```java
public class FunctionDemo {
    public static void main(String[] args) {
        String s = "林青霞,30";
        //lambda+方法引用+匿名内部类
        method(s, s1 -> s1.split(",")[1], Integer::parseInt, new Function<Integer, Integer>() {//重写apply方法
            @Override
            public Integer apply(Integer integer) {
                return integer+20;
            }
        });
    }

    private static void method(String s, Function<String,String> f1,Function<String,Integer> f2,
                          Function<Integer,Integer> f3){
        Integer i = f1.andThen(f2).andThen(f3).apply(s);
        System.out.println(i);
    }
}
```

