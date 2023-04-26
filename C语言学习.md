# C语言学习

## 封装寄存器

- stm32f103 总线结构

  ![image-20230323191454649](C:/Users/Administrator/Desktop/markdown/C%25E8%25AF%25AD%25E8%25A8%2580%25E7%259A%2584%25E6%259C%25AC%25E8%25B4%25A8%25EF%25BC%2588%25E5%259F%25BA%25E4%25BA%258Earm%25E6%25B7%25B1%25E5%2585%25A5%25E5%2588%2586%25E6%259E%2590%25EF%25BC%2589.assets/image-20230323191454649.png)

- 存储结构

  - 存储器和IO外设采用统一编址

  - 空间分为8块，每块512MB，总计4GB

  - 其中Block2用于片上外设（0x4000 0000 ~0x5FFF FFFF）

    ![image-20230323191813655](C:/Users/Administrator/Desktop/markdown/C%25E8%25AF%25AD%25E8%25A8%2580%25E7%259A%2584%25E6%259C%25AC%25E8%25B4%25A8%25EF%25BC%2588%25E5%259F%25BA%25E4%25BA%258Earm%25E6%25B7%25B1%25E5%2585%25A5%25E5%2588%2586%25E6%259E%2590%25EF%25BC%2589.assets/image-20230323191813655.png)

  - GPIOB挂在APB2下（0x4001 0C00 ~ 0x4001 0FFF）![image-20230323191929372](C:/Users/Administrator/Desktop/markdown/C%25E8%25AF%25AD%25E8%25A8%2580%25E7%259A%2584%25E6%259C%25AC%25E8%25B4%25A8%25EF%25BC%2588%25E5%259F%25BA%25E4%25BA%258Earm%25E6%25B7%25B1%25E5%2585%25A5%25E5%2588%2586%25E6%259E%2590%25EF%25BC%2589.assets/image-20230323191929372.png)

- 用指针操作寄存器![image-20230323191116532](C:/Users/Administrator/Desktop/markdown/C%25E8%25AF%25AD%25E8%25A8%2580%25E7%259A%2584%25E6%259C%25AC%25E8%25B4%25A8%25EF%25BC%2588%25E5%259F%25BA%25E4%25BA%258Earm%25E6%25B7%25B1%25E5%2585%25A5%25E5%2588%2586%25E6%259E%2590%25EF%25BC%2589.assets/image-20230323191116532.png)

  GPIO 结构体 （包含GPIO类型的全部寄存器），可以适用于所有GPIO

  ![image-20230323192432297](C:/Users/Administrator/Desktop/markdown/C%25E8%25AF%25AD%25E8%25A8%2580%25E7%259A%2584%25E6%259C%25AC%25E8%25B4%25A8%25EF%25BC%2588%25E5%259F%25BA%25E4%25BA%258Earm%25E6%25B7%25B1%25E5%2585%25A5%25E5%2588%2586%25E6%259E%2590%25EF%25BC%2589.assets/image-20230323192432297.png)

## 函数指针

函数指针：指向函数的地址

![image-20230323193345568](C:/Users/Administrator/Desktop/markdown/C%25E8%25AF%25AD%25E8%25A8%2580%25E7%259A%2584%25E6%259C%25AC%25E8%25B4%25A8%25EF%25BC%2588%25E5%259F%25BA%25E4%25BA%258Earm%25E6%25B7%25B1%25E5%2585%25A5%25E5%2588%2586%25E6%259E%2590%25EF%25BC%2589.assets/image-20230323193345568.png)

函数加不加`&`都是函数地址

回调函数 就是 定义一个函数指针，然后可以往指针中传入符合函数指针类型的函数地址。

## 链表

内存：

- 优点：可以随机访问，存储读取速度快

- 缺点：需要足够连续的一块内存空间，空间大小固定，不能动态扩展插入，删除麻烦

链表

- 优点：内存利用率高，空间可调，扩展灵活，插入删除方便
- 缺点：不能随机查找读取存储或者删除数据需要遍历链表，比较慢

![image-20230323195156853](C:/Users/Administrator/Desktop/markdown/C%25E8%25AF%25AD%25E8%25A8%2580%25E7%259A%2584%25E6%259C%25AC%25E8%25B4%25A8%25EF%25BC%2588%25E5%259F%25BA%25E4%25BA%258Earm%25E6%25B7%25B1%25E5%2585%25A5%25E5%2588%2586%25E6%259E%2590%25EF%25BC%2589.assets/image-20230323195156853.png)

循环链表的插入和删除：

- 插入
  1. 插入结点的分别指向前后结点
  2. 前后结点分别指向插入结点
- 删除
  1. 后结点指向前结点
  2. 前结点指向后节点

定义结点和链表：

```c
typedef struct LIST_NODE{
    int data;
    struct LIST_NODE *pxNext;
    struct LIST_NODE *pxPrevious;
} ListNode   //结点
typedef struct LIST{
    unsigned int NumberOfNodes;
    ListNode RootNode;      //循环链表参考点
}List  //链表

```

## CPU与外设

- 访问单个设备

  ![image-20230323201452135](C:/Users/Administrator/Desktop/markdown/C%25E8%25AF%25AD%25E8%25A8%2580%25E7%259A%2584%25E6%259C%25AC%25E8%25B4%25A8%25EF%25BC%2588%25E5%259F%25BA%25E4%25BA%258Earm%25E6%25B7%25B1%25E5%2585%25A5%25E5%2588%2586%25E6%259E%2590%25EF%25BC%2589.assets/image-20230323201452135.png)

- 访问多个设备

  cpu只负责发送地址，内存管理器，根据地址通过片选引脚选中设备来选择外设。片上外设都属于同一个地址空间

  ![image-20230323201529626](C:/Users/Administrator/Desktop/markdown/C%25E8%25AF%25AD%25E8%25A8%2580%25E7%259A%2584%25E6%259C%25AC%25E8%25B4%25A8%25EF%25BC%2588%25E5%259F%25BA%25E4%25BA%258Earm%25E6%25B7%25B1%25E5%2585%25A5%25E5%2588%2586%25E6%259E%2590%25EF%25BC%2589.assets/image-20230323201529626.png)

- 单个设备自己的片选

## C语言的本质

程序的入口由硬件决定

> 硬件会让cpu从flash中读第一条指令来执行

程序的执行是我们控制的

`char c = "A" `转汇编   STRB 操作一字节

`int b =1`转汇编  STR 操作四字节

声明只是指导编译器工作，根据声明知道操作多少空间	

## 变量

Cpu flash ram（内存）

变量，可以变，可读可写，都存在内存中，指针（地址）在32位处理器中都是4字节

 ## 关键字

- const

  只读的常量放在flash中，加const放于ram中，节省内存

- sizeof（运算符）

  ```c
  Char *p;
  Int *p2;
  
  Sizeof(*p)  = sizeof(int)
  Sizeof(p) = 32
  ```

- Volatile 

  Volatile 防止编译器优化（只在cpu中改变），必须要把值写入内存中用于必须要读的寄存器

- Extern

  Extern 可以在文件中直接写，也可以在包含的头文件里面写

  不建议使用全局变量，要的话用static，可以做一个函数接口 get_x()让别人获得变量的值,Extern建议放在.h文件中声明

## 结构体

struct类型声明不占空间，声明变量占空间

Struct 里面定义的变量类型和非4的倍数，在内存中会优化到占4个字节

对齐保证效率高

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml11152\wps5.jpg) 

 

写几个字节取决于什么类型

## 变量赋值：

p值获取地址，用*p赋值，可能会数据溢出

 

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml11152\wps6.jpg) 

 

```c
Struct person {
	Char a;
	Char b
	Int c;
}

struct person wei = {“1”, ”2”, 1};
struct person *pt;
*pt = wei;  //把wei的值全部赋给*pt
//*pt 也是一个person结构体类型；(故并非传地址)
//pt是指针类型
```



结构体声明中，不可以放结构体，但可以放结构体指针，结构体用.取成员

指针用 ->取成员

 ## 函数指针

```c
Int (*function)(void )
{
}
```

定义函数指针，function是变量，占4字节，function和&function都一样 。

- Typedef （类比 #define,define是宏定义，直接替换），typedef是类型定义 可以创建类型别名，可以让使用更方便。

  ![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml11152\wps7.jpg) 

  A、B、C、D都是类型别名，add_type同理

  ![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml11152\wps8.jpg) 

 

## 结构体指针：

get_lcb 取出结构体指针进行传递 4字节，避免了传递结构体，省空间

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml11152\wps9.jpg) 

## arm架构与汇编

```c
Int a =1;
Int b = 2
a = a+b;
```

汇编

![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml11152\wps10.jpg) 


![img](file:///C:\Users\ADMINI~1\AppData\Local\Temp\ksohtml11152\wps11.jpg)

 

有初始值的全局变量 直接复制到data段

无初始值的全局变量 集中拷贝到ZI段 然后一起置0

ZI段和data段一起叫做全局区

串口 TTL  RS232（3~12 -3~-12） RS485差分