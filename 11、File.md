#File

File类：顺序文件
RandomAccessFile类：随机文件

##构造方法

生成File对象：==在内存中==

| 方法名                            | 说明                                                        |
| --------------------------------- | ----------------------------------------------------------- |
| File(String pathname)             | 通过将给定的路径名字符串转换为抽象路径名来创建新的 File实例 |
| File(String parent, String child) | 从父路径名字符串和子路径名字符串创建新的 File实例           |
| File(File parent, String child)   | 从父抽象路径名和子路径名字符串创建新的 File实例             |

File fileObject=new File(“d:/save/Hello.java”);

File fileObject=new File(“d:/save”,”Hello.java”);

File dirObject=new File(“d:/save”); File fileObject=new File(dirObject,”Hello.java”);

## 创建功能

创建File或Directory：==在磁盘上==

| 方法名                         | 说明                                                         |
| ------------------------------ | ------------------------------------------------------------ |
| public boolean createNewFile() | 当具有该名称的文件不存在时，创建一个由该抽象路径名命名的新空 文件 |
| public boolean mkdir()         | 创建由此抽象路径名命名的目录                                 |
| ==public boolean mkdirs()==    | 创建由此抽象路径名命名的目录，包括任何必需但不存在的父目录   |

##判断功能

| 方法名                       | 说明                                 |
| ---------------------------- | ------------------------------------ |
| public boolean isDirectory() | 测试此抽象路径名表示的File是否为目录 |
| public boolean isFile()      | 测试此抽象路径名表示的File是否为文件 |
| public boolean exists()      | 测试此抽象路径名表示的File是否存在   |

##获取功能

| 方法名                          | 说明                                                     |
| ------------------------------- | -------------------------------------------------------- |
| public String getAbsolutePath() | 返回此抽象路径名的绝对路径名字符串                       |
| public String getPath()         | 将此抽象路径名转换为路径名字符串                         |
| public String getName()         | 返回由此抽象路径名表示的文件或目录的名称                 |
| public String[] list()          | 返回此抽象路径名表示的目录中的文件和目录的名称字符串数组 |
| public File[] listFiles()       | 返回此抽象路径名表示的目录中的文件和目录的File对象数组   |

##删除功能

| 方法名                  | 说明                               |
| ----------------------- | ---------------------------------- |
| public boolean delete() | 删除由此抽象路径名表示的文件或目录 |

- 创建目录下的文件，先创建目录，后创建文件

- 目录下有文件，先删除文件，后删除目录

# 递归遍历文件内容

```java
public class Test3 {
    public static void main(String[] args) {
        File srcFile=new File("C:\\itcast");
        getAllFile(srcFile);
    }

    public static void getAllFile(File srcFile){
        File[] files = srcFile.listFiles();
        if(files!=null){
            for(File file:files){
                if(file.isFile()){
                    System.out.println(file);
                }else{
                    getAllFile(file);
                }
            }
        }
    }
}
```