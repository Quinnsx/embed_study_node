
#                                                               ARM架构及编程

# 嵌入式概念及硬件组成

## 处理器的区分

CPU (MPU)->专用 CPU(个人电脑)

CPU (MPU)->MCU->AP(手机、能运行linux的设备)

## 嵌入式系统硬件组成

MCU 

Memory controller

非XIP设备（spi、LCD、SD、USB）

XIP：ROM、RAM、

> XIP：execute in place，即芯片内执行，指应用程序可以直接在flash闪存中取指然后译码、执行，不必再把代码读到系统RAM中，flash内执行时指Nor flash不需要初始化，可以直接在flash内执行代码，但往往只执行部分代码，比如用于初始化RAM等。
>
> Nand Flash 和 Nor Flash：**Nor Flash能在芯片内执行，指的是CPU能够直接从Nor flash中取指令，供后面的译码器和执行器来使用。**

# 硬件知识

直接接二极管：芯片驱动能力够

经过三极管接发光二极管：芯片驱动能力不足 

不关心主芯片输出电平，只关心主芯片输出的逻辑状态



# LED编程

![image-20230503164210052](C:\Users\PC\AppData\Roaming\Typora\typora-user-images\image-20230503164210052.png)

.text 表示后面部分是处于代码段

.global 表示start是全局





![image-20230503173118911](C:\Users\PC\AppData\Roaming\Typora\typora-user-images\image-20230503173118911.png)

![image-20230503174233839](C:\Users\PC\AppData\Roaming\Typora\typora-user-images\image-20230503174233839.png)

> P表示会烧写，Offset表示烧到哪个位置。

![image-20230503163515714](C:\Users\PC\AppData\Roaming\Typora\typora-user-images\image-20230503163515714.png)

> 上电后，固件里面有程序，会把boot1/2分区里面的程序读出来到内存中运行，boot1/2的程序去初始化硬件，接着boot1/2的程序把user data area里面的程序读到ram中对应位置	

DDR

> 全称为Double Data Rate SDRAM，中文名为“双倍数据流SDRAM”。DDR SDRAM在原有的SDRAM的基础上改进而来。   

EMMC包括Flash

# 地址空间

- ARM

  CPU对于内存只有读和写操作，运算在内部，

  CPU只能直接控制片上外设，这些片上外设位于一个地址空间，片外的外设如外接的flash则位于另一个地址空间

  ![image-20230503183136223](C:\Users\PC\AppData\Roaming\Typora\typora-user-images\image-20230503183136223.png)

- X86

![image-20230503183308460](C:\Users\PC\AppData\Roaming\Typora\typora-user-images\image-20230503183308460.png)



## ARM内部寄存器

运行a+b指令时，cpu的运行过程

![image-20230504175416557](C:\Users\PC\AppData\Roaming\Typora\typora-user-images\image-20230504175416557.png)

M3/M4架构的XPSR实际上对应3个寄存器APSR/IPSR/EPSR

这些程序状态寄存器，保留某些比较结果

![image-20230504175607391](C:\Users\PC\AppData\Roaming\Typora\typora-user-images\image-20230504175607391.png)



# 汇编指令格式

指令集：arm thumb thumb2





![image-20230504182728405](C:\Users\PC\AppData\Roaming\Typora\typora-user-images\image-20230504182728405.png)



MOV 寄存器之间传递数据，或者传递立即数（LDR只能传递常数（不超过32位的数））

STR 往内存写数据

LDR 从内存读数据