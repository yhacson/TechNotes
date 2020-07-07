# C程序内存空间划分
---

## 区域划分
---

C中程序一般由这几个区域组成：

* 栈(stack)

    由编译器自动分配释放

* 堆(heap)

    一般由开发者分配和释放，如果没有释放则程序结束时可能由OS回收

* 全局区

    全局区(静态区)，全局变量和静态变量的存储是放在一块的，其中分为bss段和数据段，程序结束释放

    - bss段(Block Started by Symbol)

        该段用来存放没有被初始化全局变量和静态变量

    - 数据段(Data segment)

        已经初始化的全局变量和静态变量。字符串常量也存放在此段

* 代码段(code/text segment)

    程序的代码段，此段为只读

## 图片示意
---

![img_1](./memory_layout_of_a_c_program_1.png)

<center>*(图 1)*</center>

![img_2](./memory_layout_of_a_c_program_2.png)

<center>*(图 2)*</center>

## 总结解释

1.一般情况下，一个可执行二进制程序(更确切的说，在Linux操作系统下为一个进程单元，在UC/OSII中被称为任务)在存储(没有调入到内存运行)时拥有3个部分，别是代码段(text)、数据段(data)和BSS段。这3个部分一起组成了该可执行程序的文件。

可执行二进制程序 = 代码段(text)＋数据段(data)+BSS段

2.而当程序被加载到内存单元时，则需要另外两个域：堆域和栈域。图1所示为可执行代码存储态和运行态的结构对照图。一个正在运行的C程序占用的内存区域分为码段、初始化数据段、未初始化数据段(BSS)、堆、栈5个部分。

正在运行的C程序 = 代码段+初始化数据段(data)+未初始化数据段(BSS)+堆+栈

3.在将应用程序加载到内存空间执行时，操作系统负责代码段、数据段和BSS段的加载，并将在内存中为这些段分配空间。栈亦由操作系统分配和管理，而不需要程序员示地管理；堆段由程序员自己管理，即显示地申请和释放空间。

—— from [csdn blog](https://blog.csdn.net/love_gaohz/article/details/41310597)