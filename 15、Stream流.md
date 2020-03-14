#生成Stream流

- Collection体系集合
  使用默认方法stream()生成流， default Stream stream()

- Map体系集合
  把Map转成Set集合，间接的生成流

  ```java
  Map<String,Integer> map = new HashMap<>();
  Stream<Map.Entry<String, Integer>> entryStream = map.entrySet().stream();
  Stream<Integer> valueStream = map.values().stream();
  Stream<String> keyStream = map.keySet().stream();
  ```

- 数组
  通过Stream接口的静态方法of(T... values)生成流  

  ```java
  String[] strArray = {"hello","world","java"};
  Stream<String> strArrayStream = Stream.of(strArray);
  ```

Stream流的好处

- 直接阅读代码的字面意思即可完美展示无关逻辑方式的语义
- Stream流把真正的函数式编程风格引入到Java中  

#Stream流中间操作方法  

| 方法名                                   | 说明                                                        |
| ---------------------------------------- | ----------------------------------------------------------- |
| Stream filter(Predicate predicate)       | 用于对流中的数据进行过滤                                    |
| Stream limit(long maxSize)               | 返回此流中的元素组成的流，截取前指定参数个数的数据          |
| Stream skip(long n)                      | 跳过指定参数个数的数据，返回由该流的剩余元素组成的 流       |
| static Stream concat(Stream a, Stream b) | 合并a和b两个流为一个流                                      |
| Stream distinct()                        | 返回由该流的不同元素（根据Object.equals(Object) ）组 成的流 |
| Stream sorted()                          | 返回由此流的元素组成的流，根据自然顺序排序                  |
| Stream sorted(Comparator comparator)     | 返回由该流的元素组成的流，根据提供的Comparator进行 排序     |
| Stream map(Function mapper)              | 返回由给定函数应用于此流的元素的结果组成的流                |
| IntStream mapToInt(ToIntFunction mapper) | 返回一个IntStream其中包含将给定函数应用于此流的元素 的结果  |

# Stream流终结操作方法  

| 方法名                        | 说明                     |
| ----------------------------- | ------------------------ |
| void forEach(Consumer action) | 对此流的每个元素执行操作 |
| long count()                  | 返回此流中的元素数       |

#Stream流的收集操作  

| 方法名                         | 说明               |
| ------------------------------ | ------------------ |
| R collect(Collector collector) | 把结果收集到集合中 |

工具类Collectors提供了具体的收集方式  

| 方法名                                                       | 说明                   |
| ------------------------------------------------------------ | ---------------------- |
| public static Collector toList()                             | 把元素收集到List集合中 |
| public static Collector toSet()                              | 把元素收集到Set集合中  |
| public static Collector toMap(Function keyMapper,Function valueMapper) | 把元素收集到Map集合 中 |

```java
public class ActorDemo {
    public static void main(String[] args) {
        //创建集合
        ArrayList<String> manList = new ArrayList<String>();
        manList.add("周润发");
        manList.add("成龙");
        manList.add("刘德华");
        manList.add("吴京");
        manList.add("周星驰");
        manList.add("李连杰");
        ArrayList<String> womanList = new ArrayList<String>();
        womanList.add("林心如");
        womanList.add("张曼玉");
        womanList.add("林青霞");
        womanList.add("柳岩");
        womanList.add("林志玲");
        womanList.add("王祖贤");

        //男演员只要名字为3个字的前三人
        
        //女演员只要姓林的，并且不要第一个
        
        Stream<Actor> sa=Stream.concat(manList.stream().filter(s -> s.length() == 3).limit(3),
                womanList.stream().filter((s -> s.startsWith("林"))).skip(1))
                .map(s -> new Actor(s));
        List<Actor> la = sa.collect(Collectors.toList());
        for(Actor a:la){
            System.out.println(a);
        }

    }
}
```