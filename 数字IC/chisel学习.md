### 使用 MLIR-based firrtl compiler 和我使用emitVerilog(new NPC(), Array("--target-dir", "generated"))有什么区别？

使用 MLIR-based firrtl compiler 和 `emitVerilog(new NPC(), Array("--target-dir", "generated"))` 的区别在于所使用的编译器和生成的目标。

1. MLIR-based firrtl compiler：MLIR（Multi-Level Intermediate Representation）是一种多层次中间表示，它可以用于表示不同级别的程序和硬件描述。MLIR-based firrtl compiler 是使用 MLIR 构建的一个编译器，它可以将 Chisel 或 firrtl 代码转换为其他形式的中间表示或目标代码。它具有灵活的扩展性和优化能力，可以实现更高级的转换和优化操作。使用 MLIR-based firrtl compiler 可能会提供更多的编译和优化选项。

2. `emitVerilog(new NPC(), Array("--target-dir", "generated"))`：这是使用 Chisel 提供的内置函数 `emitVerilog` 生成 Verilog 代码的方法。它将 Chisel 代码转换为 Verilog，并生成相应的 Verilog 文件。使用这种方法可以快速、简单地生成 Verilog 代码，但在转换和优化方面可能没有 MLIR-based firrtl compiler 提供的灵活性和功能。

总的来说，使用 MLIR-based firrtl compiler 可能提供更多的编译和优化选项，并能够进行更高级的转换和优化操作。而使用 `emitVerilog` 函数则更简单直接，适合快速生成 Verilog 代码。选择使用哪种方法取决于具体的需求和项目的要求。

### 使用 MLIR-based firrtl compiler 可能提供更多的编译和优化选项是指？

使用 MLIR-based firrtl compiler 可能提供更多的编译和优化选项是指它可以进行更复杂和高级的编译和优化操作，以改进生成的硬件电路的性能、功耗和面积等方面。

MLIR（Multi-Level Intermediate Representation）作为一种多层次中间表示，具有灵活的表达能力和可扩展性。MLIR-based firrtl compiler 使用 MLIR 进行编译和优化，因此可以应用各种高级优化技术和转换算法来改进硬件电路的质量和效能。一些可能的编译和优化选项包括：

1. 高级优化技术：MLIR-based firrtl compiler 可能支持更复杂的优化技术，如常量传播、复杂算术优化、控制流分析和转换等，以提高电路的性能和效率。

2. 资源分配和调度：MLIR-based firrtl compiler 可能提供更灵活的资源分配和调度策略，以实现更优化的电路布局和资源利用，减少功耗和面积等方面的开销。

3. 指令调度和流水线优化：MLIR-based firrtl compiler 可能支持更高级的指令调度和流水线优化，以最大限度地提高硬件电路的性能和吞吐量。

4. 自定义转换和优化：MLIR-based firrtl compiler 可能允许用户定义自己的转换和优化规则，以满足特定的需求和约束。

这些都是 MLIR-based firrtl compiler 可能提供的一些编译和优化选项的示例。它可以帮助用户更精确地控制和改进生成的硬件电路的质量和性能。

### chisel时序电路（一）：chisel寄存器（Register）

构建时序逻辑电路的最基础的元素是寄存器，寄存器在数字逻辑电路中，本质就是D触发器的集合。寄存器会在时钟的上升沿用输入的值更新输出的值。

![image-20230604082311929](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230604082311929.png)

1. chisel中，输入为d输出为q的寄存器表示如下：

```c
val q = RegNext(d)
```

也可以分两步定义：

```c
val delayReg = Reg(UInt(4.W))
delayReg := delayIn
```

> chisel命名：变量名通常用小写字母开头，类通常用大写字母开头

在初始化的时候复位：

```c
val valReg = RegInit(0.U(4.W))
valReg := inVal
```

chisel默认是同步复位。

![image-20230604083154908](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230604083154908.png)

![image-20230604083345320](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230604083345320.png)

2. 带使能信号的寄存器

![image-20230604083419773](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230604083419773.png)

```c
val enableReg = Reg(UInt(4.W))
when(enable){
    enableReg := inVal
}
```

也可以使用RegEnable函数直接构造：

```c\
val enableReg = RegEnable(inVal, enzble)
```

寄存器还可以在不命名的情况下作为表达式的一部分，

```c
val risingEdge = din & !RegNext(din)
```

用来检测一个信号的上升沿。

### chisel时序电路（二）：chisel计数器（counter）

本质来说，计数器也是一个寄存器，只不过计数器的输出会连接到一个加法器，加法器的另一个输入为计数的步进值

![image-20230604084402942](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230604084402942.png)

1. 用chisel实现一个4位计数器：

```scala
val cntReg = RegInit(0.U(4.W))
cntReg := cntReg + 1.U
```

2. 向上计数/向下计数

向上计数直到某个特定值，然后再重新从零开始

```scala
val cntReg = RegInit(0.U(8.W))

when(cntReg === N) {
    cntReg := 0.U
}.otherwise {
    cntReg := cntReg + 1.U
}
```

也可以用Mux来替代实现：

```scala
val cntReg = RegInit(0.U(8.W))

cntReg := Mux(cntReg === N, 0.U, cntReg + 1.U)
```

从某个最大值开始向下计数，直到0，再复位到最大值

```scala
val cntReg = RegInit(N)

cntReg := Mux(cntReg === 0.U, N, cntReg - 1.U)
```

参数化计数器：

```scala
// 返回计数器的函数
def genCounter(n: Int) = {
    val cntReg = RegInit(0.U(8.W))
    cntReg := Mux(cntReg === n.U, 0.U, cntReg + 1.U)
    cntReg
}

// 可以直接用这个的函数创建各种不同上限的计数器
val counter10 = genCounter(10)
val counter99 = genCounter(99)
```

3. 计数器的优化

标准的计数器包括：一个寄存器，一个加法器/减法器，一个比较器

其中寄存器和加法器无法优化，比较器可以。

不管向上计数还是向下计数都是需要比较所有位的，**那如果我们计数从`N-2`到`-1`，负数的最高有效位是1，正数的最高有效位为0，故只需比较最高一位即可**

```scala
val MAX = (N-2).S(8.W)
val cntReg = RegInit(MAX)
io.tick := false.B
    
cntReg := cntReg - 1.S
when(cntReg(7)){
    cntReg := MAX
    io.tick := true.B
}
```

4. 定时器

![image-20230604091359169](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230604091359169.png)

```scala
val cntReg = RegInit(0.U(8.W))
val done = cntReg === 0.U

next = WireDefault(0.U)
when(load) {
    next := din
} .elsewhen (!done) {
    next := cntReg - 1.U
} .otherwise {
    next := 0.U
}

cntReg := next
```

5. 计数器实现脉冲宽度调制(PWM波)

每十个时钟周期生成三个时钟周期的high信号：

```scala
def pwm(nrCycles: Int, din: UInt) = {
    val cntReg = RegInit(0.U(unsignedBitLength(nrCycles-1).W))
    cntReg := Mux(cntReg === (nrCycles-1).U, 0.U, cntReg + 1.U)
    din > cntReg
}

val din = 3.U
val dout = pwm(10, din)
```

`pwm`函数是PWM生成器，参数`nrCycles`用于配置PWM的时钟周期数，参数`din`用于给定占空周期数，即PWM输出信号的脉冲宽度。

### chisel时序电路（三）：chisel移位寄存器（Shift Register）

移位寄存器是顺序连接的一组触发器。

1. 实现

```scala
val shiftReg = Reg(UInt(4.W))//创建一个4位寄存器
shiftReg := Cat(shiftReg(2,0),din)
val dout = shiftReg(3)
```

代码第二行可以更新输入。

2. 并行输出移位寄存器

![image-20230604131013413](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230604131013413.png)

```scala
val outReg = RegInit(0.U(4.W))
outReg := Cat(serIn, outReg(3, 1))
val q = outReg
```

3. 并行输入移位寄存器

![image-20230604131229525](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230604131229525.png)

```scala
val loadReg = RegInit(0.U(4.W))
when(load) {
    loadReg := d
} .otherwise {
    loadReg := Cat(0.U, loadReg(3, 1))
}
val serOut = loadReg(0)
```

### chisel(四)：chisel内存（Memory）

1. 实现

![image-20230604132226628](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230604132226628.png)

```scala
class Memory() extends Module {
    val io = IO(new Bundle {
        val rdAddr = Input(UInt(10.W))
        val rdData = Output(UInt(8.W))
        val wrEnable = Input(Bool())
        val wrAddr = Input(UInt(10.W))
        val wrData = Input(UInt(8.W))
    })
    
    val mem = SyncReadMem(1024, UInt(8.W))
    
    io.rdData := mem.read(io.rdAddr)
    
    when(io.wrEnable) {
        mem.write(io.wrAddr, io.wrData)
    }
}
```

2. 带读写转发的同步内存

在同一个时钟周期内对内存的同一个存储单元进行读写操作时，对于存储单元内的内容不确定，读取到的值有可能是新值，也有可能是旧值。因此，如果想要读取到新写入的值的话，可以构建一个转发电路。

![image-20230604133605874](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230604133605874.png)

当读操作和写操作的地址相同时，将要写入的新值直接输出给`dout`。

```scala
class ForwardingMemory() extends Module {
    val io = IO(new Bundle {
        val rdAddr = Input(UInt(10.W))
        val rdData = Output(UInt(8.W))
        val wrEnable = Input(Bool())
        val wrAddr = Input(UInt(10.W))
        val wrData = Input(UInt(8.W))
    })
    
    val mem = SyncReadMem(1024, UInt(8.W))
    
    val wrDataReg = RegNext(io.wrData)
    val doForwardReg = RegNext(io.wrAddr === io.rdAddr && io.wrEnabale)
    
    val memData = mem.read(io.rdAddr)
    
    when(io.wrEnable) {
        mem.write(io.wrAddr, io.wrData)
    }
    
    io.rdData := Mux(doForwardReg, wrDataReg, memData)
}
```





