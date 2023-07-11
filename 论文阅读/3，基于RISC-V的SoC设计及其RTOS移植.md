## 基于RISC-V的SoC设计及其RTOS移植

​		借用RISC-V官方提供的参考处理器实现项目Rocket Chip，构建了SoC；利用Design Compiler进行逻辑综合，将设计从RTL代码转换为门级网表，然后利用IC Compiler工具完成设计的后端物理设计，并通过验证得到最终的设计版图；在FPGA开发板上进行板级验证；实现基于FPGA的RISC-V平台上的FreeRTOS移植。

### 2 Rocket Chip项目概述

​		此项目是由加州大学伯克利分校开发的，并不是一个单一的SoC设计实例，而是**一个设计生成器**。具有灵活的参数化设计，便于定制SoC。基于Chisel硬件描述语言，从复杂的生成器库里，将core、cache和interconnect等部件组合成为一个完整的SoC，相当于把所有的碎片设计粘合在一起形成一个完整的设计。

​		标量处理器内核Rocket是基于RV32G和RV64G指令集架构的五级单发射顺序执行内核生成器，支持RISC-V的机器级、管理级和用户级的特权架构扩展。

#### 2.3 RISC-V交叉编译工具链的搭建及测试

​		RISC-V官方提供了RISC-V交叉编译所需的一系列工具，包括比较通用的ELF/Newlib工具链和相对更复杂的Linux-ELF/glibc工具链。

​		Newlib是一个旨在嵌入式系统上使用的C函数库，是由很多免费的库组成的集合，对用户提供且只提供源代码，其源码目前由Red Hat公司维护。

​		glibc是GNU在1988年推出的一个C函数库，现在常见的GNU系统、GNU/Linux系统以及其他基于Linux内核的操作系统基本都使用了glibc。

​		安装好交叉编译链后，通过Spike模拟器、交叉编译工具和riscv-pk，借由一个简单的C程序来测试交叉编译链的正确性。

​		其中Spike是一个RISC-V ISA模拟器，实现了若干个RISC-V线程的功能模型，支持RISC-V是多种指令集模块；riscv-pk是一个支持静态链接的RISC-V ELF二进制文件的小型的执行程序的系统环境，在有限的I/O功能下实现了有限的RISC-V内核。

### 3 基于RISC-V的SoC的前后端实现

#### 3.1 基于Rocket Chip的SoC的前端设计研究

​		定义一个新的类System，继承原来的RocketSubsystem类，并对其进行扩展，增加外设配置各个外设的参数。

> 直接使用官方项目现成的内核，再添加几个外设即可得到一个完整的SoC

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230706110212790.png" alt="image-20230706110212790" style="zoom:50%;" />

> [(29条消息) CLINT和PLIC，risc-v中断_risc-v clic_狮子座硅农（Leo ICer）的博客-CSDN博客](https://blog.csdn.net/qianniuwei321/article/details/123250492)

#### 3.2 基于Rocket Chip的SoC的逻辑综合

​		将数字电路的RTL级描述转化为可用于自动布局布线的门级网表。

​		**逻辑综合主要可分为三个过程：即翻译，由逻辑综合工具将数字电路的RTL描述转换为布尔函数表达式；优化，由逻辑综合工具根据提供的设计要求对电路的布尔函数表达式做一定的逻辑重组和优化；映射，由逻辑综合工具从目标工艺库中找到合适的逻辑单元来替换掉优化后的设计中所有的逻辑单元，得到所需的门级网表。**

##### 3.2.1 设计约束

​		利用Design Compiler工具，基于代工厂0.13μm工艺库，对之前得到的基于Rocket Chip的RTL代码进行逻辑综合。

##### 3.2.2 综合结果

#### 3.3 基于Rocket Chip的SoC的后端物理设计

​		利用IC Compiler工具来完成后端物理设计部分。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230706183901496.png" alt="image-20230706183901496" style="zoom:50%;" />

​		在整个设计过程中，要始终注意设计的时序是否收敛。

### 4 基于RISC-V的SoC平台的验证

#### 4.1 基于RISC-V的SoC平台的软件模拟

​		基于chisel的项目可以生成基于RISC-V的SoC的软件模拟器。

##### 4.1.1 riscv-tests测试集

​		riscv-tests是RISC-V官方提供的一系列测试程序，包括benchmark基准测试、debug测试、isa指令测试、mt矩阵乘法测试的源文件、编译相关文件和一些配置。

##### 4.1.2 软件模拟及测试结果

1. 可以继续利用第二章为测试交叉编译链编写的累加求和程序，通过代理内核riscv-pk，来对SoC进行仿真。但这种方式需要花费较长时间。
2. 可利用riscv-tests测试集的项目文件来编译程序。

##### 4.1.3 用GDB调试RISC-V程序

#### 4.2 基于RISC-V的SoC平台的FPGA原型验证

​		利用vivado工具进行验证。

### 5 基于RISC-V的SoC平台的RTOS移植

#### 5.1 RTOS简介

​		操作系统是一种支持计算机基本功能并为计算机上运行的其他程序或应用程序提供服务的计算机程序。操作系统提供的服务使设计者在编写应用程序时速度更快、方式更简单且易于维护。

​		实时操作系统与一般的操作系统相比，最大的特色就是**“实时性”**，如果有一个任务需要执行，实时操作系统会马上（在较短时间内）执行该任务，不会有较长的延时。这种特性保证了各个任务的及时执行。实时操作系统中都要包含一个**实时任务调度器**，这个任务调度)器与其它操作系统的最大不同是强调：严格按照优先级来分配CPU时间，并且时间片轮转不是实时调度器的一个必选项。 

> [一文详解实时操作系统(RTOS) - 嵌入式技术 - 电子发烧友网 (elecfans.com)](https://www.elecfans.com/emb/202208301886696.html)
>
> [浅谈实时操作系统 (baidu.com)](https://baijiahao.baidu.com/s?id=1746174074181093090&wfr=spider&for=pc)

​		FreeRTOS，主要是针对微控制器和小型微处理器的实时操作系统。

#### 5.2 基于Spike模拟器的FreeRTOS移植

#### 5.3 基于FPGA的RISC-V平台的FreeRTOS移植