![image-20231218102913408](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231218102913408.png)

### 偏置电路设计：

​		LDO电路中所需的偏置包括偏置电压 VREF和 VSET 以及偏置电流，采用带隙基准电路产生基准电压，进而利用基准电压产生所需的偏置电压和偏置电流。

![image-20231218103042222](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231218103042222.png)

​		中基准电流 IBIAS0 为带隙基准电路中的运 放 OP_BG 提供偏置电流，IBIAS1 为控制电压 VSET产生电路中误差放大器所用偏置 电流，IBIAS2 为 LDO 核心电路提供偏置电流

其中的OP_BG如下：此运放的增 益不得低于 60 dB，相位裕度不得低于 60°。

![image-20231218103314356](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231218103314356.png)

![image-20231218103054759](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231218103054759.png)

![image-20231218103534903](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231218103534903.png)

​		为保证VSET和VREF的精度，运放的增益不得低于75 dB， 相位裕度不得低于 60°

### 主体LDO电路设计：

​		主要电路结构，分为 PartA 和 PartB 两部分。。PartA 部分的功能主要是由带隙基准与运放产生两个偏置电压 VREF 和 VSET；PartB 的功 能是在上述两个偏置电压的基础上利用 FVF 结构得到 LDO 的输出电压 VOUT。

![image-20231218103858067](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231218103858067.png)

​		产生Vref电压的电路中以单位增益的运放构成缓冲器与基准输出隔离，避免 LDO 输出 回馈对基准的影响。



### 1，直流特性仿真

#### （1）输入输出特性

​		在最大负载的情况下， 采用 DC 扫描输入电压的方式得到输出电压的变化。输入电压扫描范围 0 V-3.3 V，步长 0.1 V：

![image-20231218165701952](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231218165701952.png)

​		随着输入电压 AVDD从 0 V 增加到 3.3 V 的过程中，LDO 分别依次经过关断区、压 降区和稳压区，在电源电压为 1.4V 时，LDO 进入稳压区，即最小工作电压为 1.4V。

#### （2）压差

​		最小工作电压为1.4V时，功率管压差为199.99 mV，此时 LDO 的效率最高；当工作在最大输入电压 3.3 V 时，功率管压差增加到 2.10101 V，此时 LDO 的效率最低。

#### （3）线性调整率

​		同样是在最大和最小负载的情况下，采用 DC 扫描输入电压的方式得到输出电 压随输入电压的变化。输入电压扫描范围 1.5 V-3.3 V，步长 0.1 V，在 TT 工艺 角下，当输入电压为最小值 1.5 V 时，输出电压为 1.20001 V；当输入电压为最大值 3.3 V 时，输出电压为 1.19899 V。

​		根据线性调整率的定义，可计算得<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231218171013740.png" alt="image-20231218171013740" style="zoom: 33%;" />0.0447％或为0.537mV/V。

### 2，瞬态特性仿真

#### （1）负载调整率

​		仿真时利用理想电流源模拟输出负 载情况，在最大和最小电压的情况下，采用 DC 扫描输出负载电流的方式得到输出电压随负载电流的变化。输出电流扫描范围 5 mA-50 mA，步长 0.1 mA，

![image-20231218213422056](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231218213422056.png)

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231218213456588.png" alt="image-20231218213456588" style="zoom: 80%;" /><img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231218213656096.png" alt="image-20231218213656096" style="zoom:25%;" />=  0.3396 ppm



#### （2）静态电流

​		仿真采用瞬态仿真，电源电压 1.8 V，仿真时间 0 到 10 ms，负载空载（负载电流源为0）

![image-20231218214011939](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231218214011939.png)

​		静态电流为39uA左右

#### （3）电路启动

​		仿真采用瞬态仿真，电源电压 1.8 V，仿真时间 0 到 12 ms，同时对上电时间进 行扫描，扫描范围 1 ms-10.1 ms，步长为 1 ms，负载电流最大

![image-20231218205038211](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231218205038211.png)

#### （4）负载瞬态响应

​		仿真采用瞬态仿真，电源电压 1.8 V，仿真时间 0 到 50 μs，负载电流上升时间 1 μs，下降时间 1 μs，保持时间 3 μs，变化范围 1 mA 到 50 mA。

![image-20231218214459055](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231218214459055.png)

![image-20231218214612530](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231218214612530.png)

![image-20231218214656833](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231218214656833.png)

### 3，交流特性仿真

#### （1）环路稳定性

​		输入电压为直流 1.8 V，负载电流从 1 mA 变化到 50 mA，步长 10 mA。

![image-20231218215301400](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231218215301400.png)

#### （2）电源抑制比

​		仿真采用交流仿真，电源电压为 1.8 V，频率范围 1 Hz 到 1 GHz，负载电流为 1 mA 和 50 mA 两种不同的情况。

![image-20231218221317798](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231218221317798.png)



最终电路：

![image-20231221162059414](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231221162059414.png)

### 1，直流特性仿真

#### （1）输入输出特性

​		在最大负载的情况下， 采用 DC 扫描输入电压的方式得到输出电压的变化。输入电压扫描范围 0 V-5 V，步长 0.1 V：

![image-20231221160342431](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231221160342431.png)

​		随着输入电压 AVDD从 0 V 增加到 4.5 V 的过程中，LDO 分别依次经过关断区、压降区和稳压区，在电源电压为 2V 时，LDO 进入稳压区，即最小工作电压为 2V。

#### （2）压差

​		最小工作电压为2V时，功率管压差为198 mV，此时 LDO 的效率最高；当工作在最大输入电压 4.5 V 时，功率管压差增加到 2.7 V，此时 LDO 的效率最低。

#### （3）线性调整率

​		在最大负载的情况下，采用 DC 扫描输入电压的方式得到输出电压随输入电压的变化。输入电压扫描范围 2 V-4.5 V，步长 0.1 V，在 TT 工艺 角下，当输入电压为最小值 2 V 时，输出电压为 1.801962243 V；当输入电压为最大值 4.5 V 时，输出电压为 1.79745 V。

​		根据线性调整率的定义，可计算得<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231218171013740.png" alt="image-20231218171013740" style="zoom: 33%;" />0.1％或为1.8mV/V。

### 2，瞬态特性仿真

#### （1）负载调整率

​		仿真时利用理想电流源模拟输出负载情况，在最大和最小电压的情况下，采用 DC 扫描输出负载电流的方式得到输出电压随负载电流的变化。输出电流扫描范围1mA-10 mA，步长 0.1 mA，

![image-20231221165807805](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231221165807805.png)

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231218213456588.png" alt="image-20231218213456588" style="zoom: 80%;" /><img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231221165725073.png" alt="image-20231221165725073" style="zoom: 25%;" />=  0.2459 ppm



#### （2）静态电流

​		仿真采用瞬态仿真，电源电压 2 V，仿真时间 0 到 10 ms，负载空载（负载电流源为0）

![image-20231221170209082](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231221170209082.png)

​		静态电流为206nA左右

​		振荡原因：当负载电流太小的时候增益太低，零负载情况下的环路增益、相位裕度和输出电压结果

![image-20231221200455210](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231221200455210.png)

​		可见输出电压是稳定的。

#### （3）电路启动

​		仿真采用瞬态仿真，电源电压 2 V，仿真时间 0 到 12 ms，同时对上电时间进行扫描，扫描范围 10us-10.1 ms，步长为 1 ms，负载电流最大

![image-20231221201348725](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231221201348725.png)

​		TT 工艺角下，该 LDO 在上电时间从 10 μs 到 10 ms 变化时，当启动时间过长时LDO不能够正常启动，故需要增加一个启动电路解决。

#### （4）负载瞬态响应

​		仿真采用瞬态仿真，电源电压 2 V，仿真时间 0 到 500 μs，负载电流上升时间 1 μs，下降时间 1 μs，保持时间 300 μs，变化范围 100 nA 到 10 mA。

![image-20231222103150096](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231222103150096.png)

![image-20231222103241560](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231222103241560.png)

![image-20231222103317379](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231222103317379.png)

### 3，交流特性仿真

#### （1）环路稳定性

​		输入电压为直流 2 V，负载电流  10 mA

![image-20231222103906900](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231222103906900.png)

​		输入电压为直流 2 V，负载电流  100 nA

![image-20231222104013573](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231222104013573.png)

#### （2）电源抑制比

​		仿真采用交流仿真，电源电压为 2 V，频率范围 1 Hz 到 1 GHz，负载电流为 100 nA 和 50 mA 两种不同的情况。

![image-20231222110216113](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231222110216113.png)

![image-20231222110124175](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231222110124175.png)

