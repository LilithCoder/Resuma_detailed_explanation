# 内存分配方式一般有哪些？堆和栈的差别？


### 一般来说，程序运行时有三种内存分配方式：静态的、栈式的、堆式的：
---

1. 静态存储：是在程序编译时就已经分配好的，在整个运行期间都存在，如全局变量、常量。

2. 栈式存储：由编译器自动分配释放 ，存放函数参数、局部变量等。

3. 堆式存储：一般由程序员分配释放，若程序员不释放，程序结束时可由 OS 自动回收。如我们用 new，malloc 分配内存，用 delete，free来释放内存。


### 堆和栈的区别主要有以下几点：
---

1. 申请方式

    栈：由系统自动分配；

    堆：需要程序员自己申请，并指明大小。

2. 申请后系统的响应

    栈：只要剩余空间大于所申请空间，系统将为程序提供内存，否则将报异常提示栈溢出；

    堆：操作系统有一个记录空闲内存地址的链表，当系统收到程序的申请时，会遍历该链表，寻找第一个空间大于所申请空间的堆结点，然后将该结点从空闲结点链表中删除，并将该结点的空间分配给程序。

3. 申请效率的比较

    栈：由系统自动分配，速度较快。但程序员是无法控制的。

    堆：是由 new 分配的内存，一般速度比较慢，而且容易产生内存碎片,不过用起来最方便。

4. 申请大小的限制

    栈：栈是向低地址扩展的数据结构，是一块连续的内存的区域。即栈顶的地址和栈的最大容量是系统预先规定好的，能从栈获得的空间较小。

    堆：堆是向高地址扩展的数据结构，是不连续的内存区域。这是由于系统是用链表来存储的空闲内存地址的，自然是不连续的，而链表的遍历方向是由低地址向高地址。堆的大小受限于计算机系统中有效的虚拟内存。由此可见，堆获得的空间比较灵活，也比较大。

5. 堆和栈中的存储内容

    栈：在函数调用时，第一个进栈的是主函数中函数调用后的下一条指令的地址，然后是函数的各个参数，然后是函数中的局部变量。 当本次函数调用结束后，局部变量先出栈，然后是参数，最后栈顶指针指向最开始存的地址，也就是主函数中的下一条指令，程序由该点继续运行。

    堆：一般是在堆的头部用一个字节存放堆的大小，堆中的具体内容有程序员安排。