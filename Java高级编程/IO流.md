# 1.File类的使用

## 1.1 常用构造器

![image-20220310110845590](D:\编程学习\笔记\JavaEE\Java高级编程\image-20220310110845590.png)

## 1.2 常用方法

![image-20220310111001236](D:\编程学习\笔记\JavaEE\Java高级编程\image-20220310111001236.png)

![image-20220310111046429](D:\编程学习\笔记\JavaEE\Java高级编程\image-20220310111046429.png)

![image-20220310111054310](D:\编程学习\笔记\JavaEE\Java高级编程\image-20220310111054310.png)



## 1.3 流的分类

- 按操作数据单位不同分为：字节流(8 bit)，字符流(16 bit)
- 按数据流的流向不同分为：输入流，输出流
- 按流的角色的不同分为：**节点流，处理流**
- ![image-20220312143420083](D:\编程学习\笔记\JavaEE\Java高级编程\image-20220312143420083.png)



![image-20220312144822975](D:\编程学习\笔记\JavaEE\Java高级编程\image-20220312144822975.png)

## 1.4 操作实例

### 1.4.1 将硬盘内容读入内存

```java
 public void test() {
        //实例化File类的对象
        FileReader fr = null;
        try {
            File file = new File("hello.txt");
            //提供具体的流
            fr = new FileReader(file);
            //数据的读入,read()返回读入的一个子符，如果达到末尾，则返回-1
            int data;
            while (((data = fr.read()) != -1)){
                System.out.print((char)data);
            }
        } catch (IOException e) {
            e.printStackTrace();
        }finally {
            //流的关闭
            try {
                if(fr!=null){
                fr.close();
                }
            } catch (IOException e) {
                e.printStackTrace();
            }
        }

    }
```

 注：idea下ctrl+alt+t可以快速包代码

### 1.4.2 从内存中写出数据到硬盘里

说明:
1.输出操作，对应的FiLe可以不存在的。并不会报异常

2. File对应的硬盘中的文件如果不存在，在输出的过程中，会自动创建此文件。

​    File对应的硬盘中的文件如果存在:
如果流使用的构造器是: Filewriter(file,false)/ Filewriter(file):对原有文件进行覆盖

如果流使用的构造器是: Filewriter(file,true)：对原有文件进行追加

```java
 public void TestFileWriter() throws IOException {
        FileWriter fw = null;

        try {
            //1.提供File类的对象
            File file = new File("hello.txt");
            //2.提供FileWriter对象，用于写出
            fw = new FileWriter(file,true);
            //3.写出
            fw.write("abap");
        } catch (IOException e) {
            e.printStackTrace();
        }finally {
            //4.流的关闭
            fw.close();
        }


    }
}
```

### 1.4.3 文件的复制

































