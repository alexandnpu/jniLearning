# jniLearning

主要参考的还是这个[教程](https://www.ibm.com/developerworks/java/tutorials/j-jni/j-jni.html)，
但是它上面只介绍了在solaris上的操作步骤，在linux上工作还需要以下的一些修正。

创建的步骤如下

1. 首先编写Sample1.java
1. 使用`javah Sample1.java`生成`Sample1.h`文件
1. 编写`Sample.c`文件
1. 使用如下命令生成`libSample1.so`文件 

    ```
    gcc -I/usr/lib/jvm/java-8-oracle/include/ -I/usr/lib/jvm/java-8-oracle/include/linux Sample1.c -o libSample1.so -shared -Wl,-soname,libSample1.so.1  -lc -fPIC
    ```
1. 运行`java -Djava.library.path=/home/alex.zheng/work/jni Sample1`

```
.
intMethod: 25
booleanMethod: false
stringMethod: java
intArrayMethod: 33
```
