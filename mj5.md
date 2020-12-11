异常是发生在程序执行过程中阻碍程序正常执行的错误事件；

比如打开的文件不存在、网络连接中断、操作数组越界等都会导致出现异常。

异常的基类为 Throwable，Error 和 Exception 都继承自 Throwable

## Error: 程序无法处理的错误。

这些错误表示故障发生于虚拟机自身、或者发生在虚拟机试图执行应用时，一般不需要程序处理。

## Exception: 代码异常

这种异常分两大类 RuntimeException(运行时异常)和 CheckedException(编译时异常

### 常见的 RuntimeException 有：
ArrayIndexOutOfBoundsException(数组索引越界异常)
NullPointerException(空指针异常)
ClassNotFoundException(找不到类异常)
IllegalArgumentException(非法参数异常)
SecurityException(安全性异常)复制代码
### 常见的 CheckedException 有：
NoSuchMethodException(方法未找到抛出的异常)
ClassCastException(类型转换异常类)
NumberFormatException(字符串转换为数字抛出的异常)
IOException(操作输入流和输出流时可能出现的异常)


异常出现时，会像 Java 中其他对象的创建一样，使用 new 在堆上创建异常对象

然后终止当前的执行路径，并且从当前环境中弹出异常对象的引用

此时，异常机制接管程序，并开始**寻找一个恰当的地方继续执行程序**

这个恰当的地方就是异常处理程序，它的任务是将程序从错误状态中恢复，以使程序能要么换一种方式运行，要么继续下去。