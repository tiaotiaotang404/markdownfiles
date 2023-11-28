## 基于RISC-V架构的SoC设计与实现



### 3 RISC-V SoC的核心设计

#### 3.1 RISC-V SoC整体结构

​		RISC-V Core使用单发射三级流水结构，支持RV32I和RV32M，使用哈佛存储器架构，总线采用开源免费的Silicore的Wishbone总线。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230706204700733.png" alt="image-20230706204700733" style="zoom:50%;" />

#### 3.2 SoC的流水线设计

​		设计了三级流水，将访存和写回放在了流水线的第三级，因为并不是所有指令都需要经过访存阶段后再去写回，只是由存储器访问指令时才会用到访存阶段。

​		关于流水线的冒险问题：结构冒险，分别设计了片上ROM和RAM作为指令存储器数据存储器；数据冒险，因为处理器的执行和写回功能在同一时钟周期，所以数据冒险主要产生在有加载指令中的程序，采用数据前递和流水线停顿的方式解决；控制冒险，使用静态分支预测，默认预测条件分支不发生跳转。

##### 3.2.1 取指模块设计

​		主要由程序计数器PC，指令存储器ROM和静态分支预测单元组成。

​		在取指令的过程中，可以将得到的指令 分为分支跳转指令和非分支跳转指令，RV32I中有2条无条件跳转指令，还有6条有条件跳转指令，采用静态分支预测的方式来对分支跳转指令进行预测。

##### 3.2.2 译码模块设计

​		把从取指单元取出的指令进行翻译，并把相关译码信息发送给执行单元。译码阶段还需要一个寄存器堆的结构，也称为通用寄存器组。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230707092222722.png" alt="image-20230707092222722" style="zoom: 33%;" />

##### 3.2.3 执行模块设计

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230707092429168.png" alt="image-20230707092429168" style="zoom: 50%;" />		                                                                                                                                                                                                                                              

​		指令集中有8条存储器访问指令，其中5条存储器读和3条存储器写。

​		整数乘除法单元，采用单周期乘法器和独立的多周期除法模块，其中除法模块采用了简单的试商法，一次除法需要几十个时钟周期，故在进行除法运算时，需要暂停流水线几十个时钟周期。

#### 3.3 流水线控制模块

​		主要负责流水线的暂停、冲刷功能，流水线的暂停信号主要来自译码模块、执行模块、调试模块和中断异常模块。

#### 3.4 中断异常模块设计

​		在RISC-V指令集架构文档中定义了四种中断类型，分别是外部、计数器、软件和调试中断。RISC-V架构官方文档中定义了一个中断控制器PLIC，可以通过配置PLIC中相关寄存器来对多个外部中断源进行管理。

​		文章设计的SoC支持前三种中断类型，并通过mcause寄存器去定义中断响应优先级顺序。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230707100233734.png" alt="image-20230707100233734" style="zoom:50%;" />

#### 3.5 调试模块设计

​		调试单元在处理器的设计中十分重要，目前常采用“交互式调试”和“追踪调试”两种调试机制。

​		文章采用GDB和OpenOCD的组合进行软件程序下载和部分调试功能。其中，GDB是RISC-V的GNU工具链中的调试软件，可广泛用于调试C，C++等各种高级语言和汇编语言编写的程序。OpenOCD是一款免费开源的调试工具，支持大多数主流的开发板和调试器。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230707101240228.png" alt="image-20230707101240228" style="zoom:50%;" />

#### 3.6 总线设计

​		文章使用Wishbone总线。同一时刻，只允许一个Master和一个Slave进行通信。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230707102633004.png" alt="image-20230707102633004" style="zoom:50%;" />

​		<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230707102830728.png" alt="image-20230707102830728" style="zoom:50%;" />

### 4 RISC-VSoC的嵌入式软件设计

​		文章在SoC硬件实现的基础上，还开发了配套的SDK，并基于该平台搭建了基于windows下的图形化IDE，便于该SoC平台进行嵌入式开发。

#### 4.2 RISC-V软件工具链

		1. 支持RISC-V架构的GNU工具链riscv-gnu-toolchain，包括riscv gcc编译器、实现C标准库的riscv-glibc、GDB调试软件和一些二进制工具。
		2. 基于OpenOCD的RISC-V调试器软件riscv-openocd
		3. 用于指令集测试的riscv-tests

#### 4.4 搭建Windows图形化开发环境IDE

​		Platform IO 是面向嵌入式系统工程师和为嵌入式产品编写应用程序的软件开发人员的跨平台，跨体系结构， 多框架的专业工具，支持许多不同的软件开发工具包（SDK） 或框架，并包括复杂的调试，可以在任何现代操作系统上运行。

### 5 RISC-V SoC的仿真与验证

#### 5.1 riscv-tests

​		选择lcarus Verilog（iverilog）作为仿真器工具，再结合gtkwave工具查看仿真波形。

#### 5.2 软件功能测试

#### 5.3 FPGA平台验证

#### 5.4 运行CoreMark跑分程序





### RISC-V SoC的嵌入式软件设计

1. 基于RISC-V SoC开发相应的板级支持包
2. 使用RISC-V汇编语言编写相应系统引导程序
3. 使用高级语言C编写若干软件程序

#### 1 RISC-V 软件工具链

​		高级语言程序转换为可执行代码的过程：翻译、汇编、链接

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230710110054600.png" alt="image-20230710110054600" style="zoom: 50%;" />

​		RISC-V 根据上述代码转换的过程所需的软件工具链：

​	1. 支持RISC-V架构的GNU工具链riscv-gnu-toolchain，包括riscv gcc编译器、实现C标准库的riscv-glibc、GDB调试软件和一些二进制工具。

2. 基于OpenOCD的RISC-V调试器软件riscv-openocd
3. 用于指令集测试的riscv-tests

#### 2 软件开发包

​		文章的软件开发包内容结构如下：

![image-20230710110715584](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230710110715584.png)

​		通过内容结构的对比发现，和tinyriscv的内容结构相同，推测文章的SDK是在此基础上修改所得。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230710111027392.png" alt="image-20230710111027392" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230710111121644.png" alt="image-20230710111121644" style="zoom:50%;" />

##### 2.1 系统链接脚本

​		链接脚本文件存放在link.ld文件中，链接脚本主要功能时告知链接器实际物理内存的分区，即为程序分配合适的存储空间。

​		文章通过链接脚本配置了片上ROM和RAM的存储大小和地址空间，并将程序和数据存储在ROM，由于程序直接在ROM中运行，故加载地址和虚拟地址相同，而数据需要从ROM复制到RAM中使用，故加载地址和虚拟地址不同。

##### 2.2 系统启动引导程序

​		引导程序负责初始化硬件和将数据从fiash复制到ram中，最后再去执行主函数，通常使用汇编语言编写。

​		将文章展示的部分引导代码内容和tinyrsicv（tests--FreeRTOS--start.S）进行对比，内容一致。

##### 2.3 系统异常和中断处理程序

​		主要包括文件如下：

​		init.c：设置中断入口函数

​		trap_entry.S：设置中断和异常入口程序（.S是汇编语言源程序）

​		trap_handler.c：设置中断和异常函数的文件

上述三个文件在tinyriscv中都包括。

#### 3 搭建Windows图形化开发环境IDE

​		Platform IO 是面向嵌入式系统工程师和为嵌入式产品编写应用程序的软件开发人员的跨平台，跨体系结构， 多框架的专业工具，支持许多不同的软件开发工具包（SDK） 或框架，并包括复杂的调试，可以在任何现代操作系统上运行。

​		文章实现方式：在VScode中安装Platform IO进行扩展，进而搭建图形化开发环境IDE。

  		1. 在VScode中安装Platform IO进行扩展
  		2. 将软件开发包SDK安装到Platform IO
  		3. 对项目的编译、链接和调试方式进行相关的设置（文章举了个例子展示了完整的设置过程，其中涉及到一些脚本文件的编写）
