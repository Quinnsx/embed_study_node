Python学习

# 命名方法

下划线命名 ：适用于变量名 user_name

pascal命名：适用于类 UserAccount

# 执行模式

- 命令行模式

  输入指令不会被保存，适合测试

  

- 交互模式



# 函数

input





# 数据类型

可变类型

- 列表：list = [1，2，3，4]

  方法：append remove   ***方法使用时要为list.remove的格式，区别于函数*** 

  内置函数：max min sorted	

- 字典：contacts = {a:va,b:vb}    a和b为键，va和vb分别为a和b的值

  通过contacts[a]获取a的值    

  ***键的类型必须为不可变（列表不行）*** 需要两个元素作为键值时可以用元组 tuple = (a, b ,c)  圆括号 

  检查是否存在于字典 c in contacts

  增加键值对(存在则覆盖)：contacts[c] = vc

  删除键值对：del contacts[c] = vc

  查询数量：len(contacts)

- 集合 s = {a,b,c}      ***没有键值对***  集合中的元素不允许重复

  方法： set() 可以添加列表 、range、元组等

不可变类型

- tuple = (a, b ,c)      圆括号， 没有方法



## 数据容器

一种能存储多个元素的Python数据类型

列表、元组、字符串、字典、集合

- 序列：列表、元组、字符串、字节数值、range等
  - 序列切片

    序列[起始下标：结束下标：步长]

    从指定位置按步长依次取出元素到结束位置，得到新序列

- 非序列：集合、字典、frozenset等

  

  

 # 判断

if/else 一定要**缩进**

 # 循环

for A in B  

A为变量名 ，B为迭代对象  

变量名会被依次赋值为迭代对象中的每一个元素

在每一次循环中，A为B的值

range（A，B，h）会从A迭代到B-1，每次的步长为h

- 只有两个值时，h默认为1
- 只有一个值的时候默认起始值为0，h默认为1



for循环适用于有明确循环对象或次数

while循环适应于循环次数未知



# 函数

定义函数 

def functionA()

{



}



# 引入模块

- import 语句

  

- for...import...语句 

- from...import * 

![image-20230428142254299](C:\Users\PC\AppData\Roaming\Typora\typora-user-images\image-20230428142254299.png)- 



第一种方法直观，第二和第三种方法可能会导致和别的模块的相同命名函数冲突



可以从第三方库下载模块，然后引入

内置模块直接引入即可



# 面向对象编程

多态

继承

封装



定义类的属性![image-20230428144126867](C:\Users\PC\AppData\Roaming\Typora\typora-user-images\image-20230428144126867.png)



# 路径

- 相对路径![image-20230428152435745](C:\Users\PC\AppData\Roaming\Typora\typora-user-images\image-20230428152435745.png)

- 绝对路径

  ![image-20230428152522532](C:\Users\PC\AppData\Roaming\Typora\typora-user-images\image-20230428152522532.png)



# 文件操作

read

readline

readlines 返回全部文件内容每行组成的列表

![image-20230428160154289](C:\Users\PC\AppData\Roaming\Typora\typora-user-images\image-20230428160154289.png)