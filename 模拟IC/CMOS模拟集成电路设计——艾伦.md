## CMOS模拟集成电路前仿真设计流程

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231007180842490.png" alt="image-20231007180842490" style="zoom:50%;" />

### 从仿真库中寻找V~T~和计算UC~OX~参数：

- 使用 n_12_lprvt模型：

​		阈值电压V~T~：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231007183850652.png" alt="image-20231007183850652" style="zoom: 67%;" />

​		UC~OX~：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231007184010347.png" alt="image-20231007184010347" style="zoom:67%;" /><img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231007184028983.png" alt="image-20231007184028983" style="zoom:67%;" />

- 使用 p_12_lprvt模型：

​		阈值电压V~T~：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231007184130994.png" alt="image-20231007184130994" style="zoom:67%;" />

​		UC~OX~：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231007184146792.png" alt="image-20231007184146792" style="zoom: 67%;" /><img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231007184205592.png" alt="image-20231007184205592" style="zoom:67%;" />

> 其中：![image-20231007184354915](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231007184354915.png)

结果：![image-20231007184315190](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231007184315190.png)

## 第四章 模拟CMOS子电路

### 第一节 单个MOS管

![image-20230810210805252](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230810210805252.png)

1. 注意区分大信号和小信号
2. **MOS管本质上是压控电流源**
3. *μ*——载流子迁移率；C<sub>ox</sub>——栅氧化极的厚度

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230810211457580.png" alt="image-20230810211457580" style="zoom:50%;" />

#### 交流放大倍数：

![image-20230907094251165](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230907094251165.png)**g<sub>m</sub>表示MOS管将输入的电压转换成电流的能力，其中<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230907094839664.png" alt="image-20230907094839664" style="zoom:50%;" />是通过使用大信号的值替代其附近交流小信号的放大倍数。**

​		其中的 β = μC~OX~W/L

#### 交流电阻：

![image-20230907094522167](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230907094522167.png)

#### 小结：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230810213726011.png" alt="image-20230810213726011" style="zoom:50%;" />

### 第二节 两个MOS管——如何放大（放大电路主要研究是对交流信号的放大）

![image-20230810214458319](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230810214458319.png)

#### MOS管构成的放大电路，根据负载的不同分为下面三种：

![image-20230810215857986](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230810215857986.png)

（1）负载是一个 栅极和漏极相连的MOS管：

​		**M2一旦导通就处于饱和区**

![image-20230907111456885](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230907111456885.png)

（2）负载是一个输入为直流偏置电压的MOS管：

​		由于栅极和源极的输入均为直流电压，没有交流成分，即等效于交流放大倍数g<sub>m</sub>为0，故此MOS管等效于一个电阻（MOS管一般等效于一个电流源g<sub>m</sub>*V<sub>GS</sub>和一个有限的输出电阻r<sub>o</sub>），交流输出电阻大小r<sub>o</sub> = 1/λI

​		在交流输入信号情况下，两个管子的等效电阻并联（V<sub>DD</sub>是直流电压，相对于交流信号来说等效于地）

（3）两个管子互为放大管和负载管

#### 总结：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230810223139284.png" alt="image-20230810223139284" style="zoom: 67%;" />

​		其中MOS二极管是指栅漏短接的MOS管；

​		由于<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230810223308900.png" alt="image-20230810223308900" style="zoom:33%;" />，所以尽量让MOS管工作在饱和区（负载电阻越大，放大电路的增益就越大）。

### 第三节 电流源和电流沉

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230817215131342.png" alt="image-20230817215131342" style="zoom: 67%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230817215210379.png" alt="image-20230817215210379" style="zoom:67%;" />

​		注：其中V<sub>MIN</sub>就是过驱动电压V<sub>OD</sub>。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230817215327571.png" alt="image-20230817215327571" style="zoom:67%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230817215544675.png" alt="image-20230817215544675" style="zoom: 50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230817215630138.png" alt="image-20230817215630138" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230817215921752.png" alt="image-20230817215921752" style="zoom: 50%;" />

​		注：衬偏效应即体效应。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230817220433800.png" alt="image-20230817220433800" style="zoom: 50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230817220747321.png" alt="image-20230817220747321" style="zoom:50%;" />

​		注：即**带源极负反馈的共源极电路**。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230817221315539.png" alt="image-20230817221315539" style="zoom: 50%;" />

​		注：即**共源共栅极电路**。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230817221500239.png" alt="image-20230817221500239" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230817222557942.png" alt="image-20230817222557942" style="zoom:50%;" />

​		注：由于M<sub>3</sub>截止，故电流无法流通，只能通过导线流至M<sub>3</sub>的栅极，由于栅极对地有一个电容，随着栅极流入的电流越来越多，不断给电容进行充电，导致M<sub>3</sub>的栅极电压不断增大，最后使得M<sub>3</sub>导通。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230817224213850.png" alt="image-20230817224213850" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230817224244109.png" alt="image-20230817224244109" style="zoom:50%;" />

​		注：即低压电流共源共栅电流镜

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230817224326844.png" alt="image-20230817224326844" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230817224439796.png" alt="image-20230817224439796" style="zoom:50%;" />

### 第四节 电流镜

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230911212244193.png" alt="image-20230911212244193" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230911212501336.png" alt="image-20230911212501336" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230911212527198.png" alt="image-20230911212527198" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230911214332888.png" alt="image-20230911214332888" style="zoom: 50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230911214557049.png" alt="image-20230911214557049" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230911214700051.png" alt="image-20230911214700051" style="zoom:50%;" />

### 第五节 电流和电压基准

- 与电源电压无关
- 与温度无关
- 与工艺变化无关
- 与噪声和干扰无关

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230911215715819.png" alt="image-20230911215715819" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230911215834826.png" alt="image-20230911215834826" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231006094608457.png" alt="image-20231006094608457" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230911220007653.png" alt="image-20230911220007653" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230911220205173.png" alt="image-20230911220205173" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230911220858875.png" alt="image-20230911220858875" style="zoom:50%;" />

> 右图是一个运放，右图中的电流源就是左图基准电路的M~5~管，版图中M~5~管需要和基准源放在一起（M~5~与基准之间是通过电压控制的，距离太远会有寄生电容的影响）

> 下面式子中的I~1~和I~2~通过3，4管的电流镜可以设置相同，通过计算可知电流I和电源电压无关

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230911221900632.png" alt="image-20230911221900632" style="zoom:50%;" />

> 当 I~1~ = I~2~ = 0 时也符合基准电路的工作状态，故需要自启动电路，打破电流为0的状态

> 上电后，M~7~的栅极电压不断增加，随后M~7~导通，电流流至M~1~管的漏极，经过1管的寄生电容到地，随着电流不断增大，1管的漏极即2管的栅极电压不断增大至M~2~导通；I~2~ ≠ 0，随着I~2~的增大，M~4~管的栅极电压不断降低（4管是二极管连接）至4管导通，电流镜开始工作。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230911221930537.png" alt="image-20230911221930537" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230911222821161.png" alt="image-20230911222821161" style="zoom:50%;" />

>  瞬态仿真就是启动瞬间的仿真，即电源电压已经到最高点后的一瞬间的仿真，判断电流是否会振荡

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230911223103357.png" alt="image-20230911223103357" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230912100222887.png" alt="image-20230912100222887" style="zoom:50%;" />

> 3管和1管构成一个共源极放大器，3管为增益管，1管为电流源负载；
>
> 2管，4管和R共同构成一个带源极负反馈的放大器；

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230912100254207.png" alt="image-20230912100254207" style="zoom:50%;" />



### 第六节 带隙基准

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231006143139401.png" alt="image-20231006143139401" style="zoom:50%;" />

> 正温度系数和负温度系数通过综合得到与温度无关的电路

> 其中负温度系数由一个基极与集电极短接的三极管实现

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231006143358481.png" alt="image-20231006143358481" style="zoom:50%;" />

> 在CMOS工艺中温度特性最好的是三极管；
>
> 单个三极管的温度特性是负的；

> 关于二极管的电压计算公式和电阻R~1~的压差计算公式在4.6节补充

> 对两个相同的三极管通不同大小的电流，两个管子之间的压差呈正温度系数（或对不同发射结面积的三极管通相同电流）；

> 图中的运放工作时虚短，故将1管的V~BE~和2，3，4，5管的V~BE~的差值落在R~1~上，从而使得R~1~上的电压呈现正温度系数

> 上面三个MOS管的宽长比相同，栅极和源极电压都相同，故三条支路流过的电流都相同；

> <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231006150642812.png" alt="image-20231006150642812" style="zoom:50%;" />是R~2~上的电压大小，加上6管的V~BE~得到参考电压V~REF~，其中VTln(4)/R1是R1流过的电流（即三条支路的电流大小）

> <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231006151125079.png" alt="image-20231006151125079" style="zoom:50%;" />，其中的V~BE~是负温度系数，VT是正温度系数，得到的V~REF~是零温度系数，故对温度求导可得<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231006151300526.png" alt="image-20231006151300526" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231006181245534.png" alt="image-20231006181245534" style="zoom:50%;" />

> 温度直流仿真：.dc temp -20 60 1

> 下面的图是直流扫描的结果，上面的图是输出结果的峰峰值，当温度变化时输出结果的波动（即峰峰值）越小，证明基准越稳定，故可得电阻为12428Ω时输出最稳定

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231006182919522.png" alt="image-20231006182919522" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231006183901601.png" alt="image-20231006183901601" style="zoom:50%;" />

> 注意电路中的运放的极性，不要反了

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231006184647471.png" alt="image-20231006184647471" style="zoom:50%;" />

> PTAT：正温度系数；CTAT：负温度系数
>
> 两个二极管的压差是正温度系数，二极管的电压为<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231006184934141.png" alt="image-20231006184934141" style="zoom:50%;" />（其中V~t~是热电子电压，I~1~是流过二极管的电流（或集电极电流），I~S~是二极管的饱和电流）；压差为<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231006185200637.png" alt="image-20231006185200637" style="zoom:50%;" />（其中当是三极管时，A~2~/A~1~是两个发射结面积之比）

> 运放和电流镜结构相比，运放更好，原因是运放的虚短效果更好，电流镜的两个管子由于体效应的影响达不到虚短的效果

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231006191014894.png" alt="image-20231006191014894" style="zoom:50%;" />

> V~g~ = E~g~ / q，其中E~g~为硅的带隙能量，q为电子数，V~g~是带隙电压，看最下面的式子，通过计算可知零温度系数的基准电压主要由带隙电压决定，故称之为带隙基准

> 参考前面的带隙基准的参数计算部分，可知 V~REF~ = V~BE~ + k * ln(A~2~/A~1~) * V~T~，其中的k是两个电阻值的比值，由于V~REF~是零温度系数的电压，故式子两边对温度T求导可得<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231006194626292.png" alt="image-20231006194626292" style="zoom:50%;" />，算出参数后再代回原式，可以算出V~REF~的值为红圈内容

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231006194948963.png" alt="image-20231006194948963" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231006195021788.png" alt="image-20231006195021788" style="zoom:50%;" />

> 其中采用NPN管的电路基极和集电极均连接在正电压，采用N阱CMOS工艺不能实现；采用PNP管，基极和集电极均接地，采用N阱CMOS工艺可以实现

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231006195646809.png" alt="image-20231006195646809" style="zoom:50%;" />

> ==**N阱CMOS工艺只能做集电极接地的PNP三极管**==

## 第五章 CMOS放大器

### 第一节 反相器

#### 1，二极管负载

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230916095359149.png" alt="image-20230916095359149" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230917190537832.png" alt="image-20230917190537832" style="zoom:50%;" />

> 注：系统函数的分子的根为零点（此时系统函数为0，即输入零点频率的信号之后，增益为0，导致输出为0），系统函数的分母的根为极点（使得输出函数产生一个转折）
>
> 直观的来看，当输入零点频率的信号时，信号经过M~1~后又通过电容C~gd1~这条通路将信号返回至输入点，将输入信号抵消，导致输出信号为0。
>
> 故零点频率为：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230917200035293.png" alt="image-20230917200035293" style="zoom:50%;" />，其中的C~M~为C~gd~，即跨接在M~1~的栅源之间的电容。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230917192740035.png" alt="image-20230917192740035" style="zoom:50%;" />

> 为什么增益在极点处开始下降：电路中的某些电容在高频的情况下容抗变小，导致输出阻抗减小，增益下降。根据极点的式子可知与C~M~和C~out~有关。

> 在零点处增益止住了下降的趋势，根据零点的式子可知与C~M~有关，C~out~反悔了。

#### 2，电流源负载

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230917195544990.png" alt="image-20230917195544990" style="zoom:50%;" />

> 可见增益与漏极电流大小有关，想要改变增益大小，只需改变电流即可，电流大小由M~2~管决定。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230917195629790.png" alt="image-20230917195629790" style="zoom:50%;" />

> 极点计算：先找电路的独立结点，再计算结点的对地电阻和电容。
>
> 零点计算：（同二极管负载）<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230917200723222.png" alt="image-20230917200723222" style="zoom:50%;" />

#### 3，推挽放大器

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230917200821358.png" alt="image-20230917200821358" style="zoom:50%;" />

> 两个管子互为放大管和负载管，利用叠加定理分析。

> 极点：电路结点就一个，计算不变。
>
> 零点：信号可以通过两个管子的C~gd~返回至输入端，使得输出为0，故零点计算是两个跨导之和与两个栅漏电容之和的比值。

#### 4，噪声

​		噪声是没有规律的，但它的平均功率是可以预测的，这个平均功率在电学上表示为单位电阻上消耗的功率，用V^2^表示。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230917203420757.png" alt="image-20230917203420757" style="zoom:50%;" />

> 要区别噪声功率和噪声功率谱密度的概念。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230917204234779.png" alt="image-20230917204234779" style="zoom:50%;" />

> 想要减小噪声：增大宽长比（增大跨导，增大宽长之积）。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230917205627731.png" alt="image-20230917205627731" style="zoom:50%;" />

> 由于不同电路对噪声的增益不同，故直接比较输入噪声。

> 输出噪声= 输入噪声 * 系统函数^2^

- 二极管器件负载反相器的等效输入噪声

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230917211759546.png" alt="image-20230917211759546" style="zoom:50%;" />

> 先得到电路的输出噪声，**电路的输出噪声➗电路的增益＝电路等效输入噪声**。

> 通过等效输入噪声式子可知，增大g~m1~，减小g~m2~，尽量使得两跨导的比值减小可以减小电路噪声。

- 电流源负载反相器的等效输入噪声和反相器的等效输入噪声

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230917214112558.png" alt="image-20230917214112558" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230917215618442.png" alt="image-20230917215618442" style="zoom:50%;" />

> 可见在多级放大器中，噪声主要取决于第一级放大。

### 第二节 差分放大器

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230917220053895.png" alt="image-20230917220053895" style="zoom:50%;" />

#### 1，输入极性的区分

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230917220920002.png" alt="image-20230917220920002" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230917221141971.png" alt="image-20230917221141971" style="zoom:50%;" />

> 从输出端和负极输入的增益可以看出，负极输入端和输出端之间是一个共源极（Q~2~为放大管，Q~4~为负载管），增益小于0。

> 先计算V~1~和正极输入端，两者之间是一个共源极（Q~1~为放大管，Q~3~是二极管连接负载）；随后计算V~1~和输出端，两者也是一个共源极（Q~4~为放大管，Q~2~为负载管）
>
> 最后得到正向输入端和输出端之间增益大于0。

#### 2，输入什么样的信号

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230918085918586.png" alt="image-20230918085918586" style="zoom:50%;" />

> 同相端和反相端的输入均是波动很小的信号（即交流分量幅值小），不断通过负反馈（输出端与反相端做减法）缩小两个输入端之间的差值，达到“虚短”的状态（实际两个输入端之间的差值不为0）

#### 3，Q~5~的作用

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230918091010808.png" alt="image-20230918091010808" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230918091828511.png" alt="image-20230918091828511" style="zoom:50%;" />

> 可见差分对的增益主要由Q~5~电流以及Q~1,2~的宽长比决定

> 由于MOS的跨导和输出电阻的值都与其流过的电流有关，故Q~5~也决定着其他几个管子的跨导和输出电阻

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230918092431989.png" alt="image-20230918092431989" style="zoom:50%;" />

> 根据设计的目的，使用不同的方式，从不同的点入手。

#### 4，差分对设计指标一：共模输入电压

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230918095507411.png" alt="image-20230918095507411" style="zoom:50%;" />

> 由图可知共模输入电压为2.5V

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230918095812857.png" alt="image-20230918095812857" style="zoom:50%;" />

> 将输出端与反相输入端直接相连，共模电压是INPUT的电压范围。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230918100037658.png" alt="image-20230918100037658" style="zoom:50%;" />

> 共模电压作用：保证电路中的MOS管工作在饱和区。

> 输入电压超过最大共模电压时，Q~1,2~会先进入线性区

> 共源极分析：用Q~2~举例，输入栅极电压增大，导致漏极电压减小，导致Q~2~的V~DS~减小，使之进入线性区；
>
> 寄生电容分析：用Q~2~举例，由于输入电压增大，导致Q~2~电流增大，由于Q~4~电流不变，故只能通过寄生电容输出电荷补充Q~2~所需要的电流，导致V~out~电压下降，导致Q~2~的V~DS~减小，使之进入线性区。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230918102715657.png" alt="image-20230918102715657" style="zoom:50%;" />

> 当输入电压低于最小共模电压，Q~5~先进入线性区

> 当输入电压降低，Q~1,2~的电流不变，只能降低Q~5~的漏极电压导致Q~~5~的V~DS~减小，进入线性区

#### 5，差分对设计指标二：增益带宽积

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230918104303583.png" alt="image-20230918104303583" style="zoom:50%;" />

> 直流增益，即低频增益，就是图中增益为A~V~的部分

> 增益带宽积=增益✖3dB带宽=常数，数值上等于小信号的带宽（增益为1时），即GB点

> GB点和零点没关系，GB点就是0dB（放大倍数为1）的点，零点是增益分子的根（输入任意输出均为0）

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230918112220106.png" alt="image-20230918112220106" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230918112244650.png" alt="image-20230918112244650" style="zoom:50%;" />

> 两个电路的放大倍数都是25倍，但由于GB的作用，第一个电路的带宽相较于第二个电路更小，故可以通过多级放大保证高增益的同时增大带宽。

#### 6，差分对的设计指标三：摆率

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230920085545061.png" alt="image-20230920085545061" style="zoom:50%;" />

> 摆率就是输出电压的变化速率。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230918113115850.png" alt="image-20230918113115850" style="zoom:50%;" />

> 增益带宽积为A，不代表电路的带宽为A，只有小信号（即低频信号）才能无畸变的通过，当大信号（即高频信号）输入时，由于摆率的限制会使得输出产生畸变。

> 图中的SR为摆率<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230918114320313.png" alt="image-20230918114320313" style="zoom:50%;" />

#### 7，差分对设计

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230920085853956.png" alt="image-20230920085853956" style="zoom:50%;" />

> g~m~ = 2i~D~ /  V~OD~

![image-20230920091937287](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230920091937287.png)

> 功耗：V~CC~ * Q~5~的电流
>
> 摆率：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230920090145616.png" alt="image-20230920090145616" style="zoom:50%;" />，其中的C为C~L~，电流I为流入C~L~的电流
>
> 结果：通过功耗和摆率确定一个I~5~

> 1/RC要大于频响，C为C~L~已经确定，故通过调整R~out~（=r~o2~||r~o4~）的值使之满足频率响应要求，其中r~o~=1/λI~D~，当管子的沟道长度确定后λ是个定值，故只能通过调整电流
>
> 结果：R~out~确定，从而确定一个I~5~，需要在前两步得到的两个I~5~之间折中取舍

> 利用最大共模输入电压<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230920091701096.png" alt="image-20230920091701096" style="zoom:50%;" />，由于V~CC~和V~TH~相当于已知，故可以算得V~GS3~，目前已知V~GS3~和其中的电流I~5~/2，根据<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230920092251490.png" alt="image-20230920092251490" style="zoom:50%;" />可以求出3管的宽长比，4管的宽长比等于3管
>
> 结果：求出了3，4两管的宽长比

> 增益相当于已知（一般都是给最小值），<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230920092716940.png" alt="image-20230920092716940" style="zoom:50%;" />，R~out~在第2步已经确定，故可算得g~m2~的最小值，电流为I~5~/2，<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230920093500136.png" alt="image-20230920093500136" style="zoom:50%;" />，可以算出2管的宽长比，从而得到1管的宽长比
>
> 结果：求出了1，2两管的宽长比

> 利用最小共模输入电压<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230920093831210.png" alt="image-20230920093831210" style="zoom:50%;" />，其中1管的电流和宽长比已经算出，可以根据<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230920094007354.png" alt="image-20230920094007354" style="zoom:50%;" />求得v~GS1~，从而得到V~DS5~，从而得到5管的宽长比
>
> 结果：得到5管的宽长比

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230920100009029.png" alt="image-20230920100009029" style="zoom:50%;" />

> 1/（2pi*RC）≥ 100KHz，可得R ≤ 318KHz

> 由于λ未知，故在第2步无法确定I~5~的值，故只能先取一个大概值进行计算，随后根据最后得到的计算结果反过来进行调整

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230920101241950.png" alt="image-20230920101241950" style="zoom:50%;" />

> 第4步，由于R~out~无法确定，故1，2管的跨导无法计算，只能先放着

> 第5步，由于1管的宽长比未知，故V~GS1~未知，故无法求出V~DS5~，就得不到5管的宽长比

**通过例题可知，上述方法并不适用于实际。**

#### 8，==差分对设计实例==

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230920105100531.png" alt="image-20230920105100531" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230920110316795.png" alt="image-20230920110316795" style="zoom:50%;" />

> 过驱动电压一般设为200mV，让MOS管可以工作在强反型区，可以直接求出1管的宽长比（但此方法有一个前提，没有管增益的大小，只保证了MOS管可以工作在安全的区域）

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230920111221955.png" alt="image-20230920111221955" style="zoom:50%;" />

> 计算出的宽长比为23，根据工艺可以设置W和L，进行仿真

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230920111449058.png" alt="image-20230920111449058" style="zoom:50%;" />

> 根据仿真输出发现频响范围不够，应该想办法提高3dB频率，<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230920111708477.png" alt="image-20230920111708477" style="zoom:33%;" />，电容是负载电容已确定，只能改变输出电阻值，r~o~ = 1/ λI，（由于L不变，所以λ不变），只能改变电流 I~D~，将电流增大为原来的一倍

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230920112152587.png" alt="image-20230920112152587" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230920112351240.png" alt="image-20230920112351240" style="zoom:50%;" />

> V~OD~大于200mV，符合预设，要想让V~OD~减小可以通过增大宽长比的方式实现

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230920112745467.png" alt="image-20230920112745467" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230920112941603.png" alt="image-20230920112941603" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230920113358091.png" alt="image-20230920113358091" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230920113652059.png" alt="image-20230920113652059" style="zoom:50%;" />

> 可见共模输入电压范围大概符合要求

##### 差分对设计思路总结：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230920114121386.png" alt="image-20230920114121386" style="zoom:50%;" />

### 第三节 cascode差分对

#### 1，cascode差分对的优缺点

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230921205433773.png" alt="image-20230921205433773" style="zoom:50%;" />

#### 2，cascode差分对共模输入电压推导

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230921205919350.png" alt="image-20230921205919350" style="zoom:50%;" />

#### 3，cascode差分对半边增益推导

- 小信号模型推导

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230921212543451.png" alt="image-20230921212543451" style="zoom:50%;" />

> 其中的M~3~管是最上面两个管子的等效

> M~2~管的小信号等效较难理解

- 直观推导

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230921213037507.png" alt="image-20230921213037507" style="zoom:50%;" />

> 图中两个绿色的部分是共源共栅

#### 4，cascode差分对频响推导

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230921213546680.png" alt="image-20230921213546680" style="zoom:50%;" />

#### 5，cascode差分对整体增益

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230921215353120.png" alt="image-20230921215353120" style="zoom:50%;" />

> Q~6~和Q~7~的连接方式，计算输出电阻时这种结构等效为<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230921214128011.png" alt="image-20230921214128011" style="zoom:50%;" />

> 左半边等效为一个Q~1~,为增益管的共源极，上面三个管子负载最后等效为<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230921214128011.png" alt="image-20230921214128011" style="zoom:50%;" />

> 右边V~1~到V~out~部分，Q~8~为增益管的共源共栅

#### 6，公式总结

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230921215508092.png" alt="image-20230921215508092" style="zoom:50%;" />

#### 7，cascode差分对密勒效应

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230921221047368.png" alt="image-20230921221047368" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230921221126283.png" alt="image-20230921221126283" style="zoom:50%;" />

> 密勒电容经过等效后，等效到输入端是一个被放大了（1+A~V~）倍的电容，等效到输出端的电容值不变

#### 8，cascode差分对极点分析

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230921222812234.png" alt="image-20230921222812234"  />

> M~1~管的C~GD~经过密勒等效，等效到1结点为<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230921222508796.png" alt="image-20230921222508796"  />，等效到2结点为![image-20230921222707080](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230921222707080.png)

> 结点1的等效电容较大，另外两个结点的电容较小可忽略

#### 9，cascode差分对减小密勒电容

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230921223333008.png" alt="image-20230921223333008" style="zoom:50%;" />

> 可通过密勒效应利用小电容产生比较大的电容，便于集成

> 共源极增加一个M~2~管后构成一个共源共栅，在共源极时的M~1~管的增益大于共源共栅时的M~1~，故减小了等效密勒电容的放大倍数，从而减小了密勒电容

> cascode的优点：减小了密勒效应的等效电容，从而增大了极点的频率，改善频响

#### 10，cascode差分对极点仿真

[19、共源极极点计算和仿真以及米勒补偿仿真和计算_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1xf4y1i7jL/?spm_id_from=333.999.0.0&vd_source=719585e47d53d8b6dbacff76aa9b996e)

### 第四节 折叠共源共栅差分对

#### 1，共模范围

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230923174849848.png" alt="image-20230923174849848" style="zoom: 67%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230922143042718.png" alt="image-20230922143042718" style="zoom:50%;" />

> 下面右侧图是左上图的简化，只是为了分析共模输入范围

> 结论：折叠型共源共栅cascode的共模输入范围更大

#### 2，增益计算

- 引子

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230922144913380.png" alt="image-20230922144913380" style="zoom:50%;" />

> 其中1，2，6，7，5管构成一个差分对，8，9，10管用于给差分对提供直流偏置电压，3，4管进行二次输出放大

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230922145318139.png" alt="image-20230922145318139" style="zoom:50%;" />

> V~1~首先经过M~1~进行第一级放大，1，6，3管作为第一级负载；再经过M~4~进行第二级放大，2，4，7管作为第二级负载

> V~2~经过M~2~管进行放大，2，4，7管作为负载

> 此分析方式不适合对折叠型共源共栅的分析

- 换个思路

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230922150421145.png" alt="image-20230922150421145" style="zoom:50%;" />

> 右上的图为v1输入的等效电路

> 思路：先计算到达输出端的两个电流，求和后与输出电阻相乘得到输出电压，从而得到电路增益

- 电流思路求解折叠共源共栅的增益

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230922151729956.png" alt="image-20230922151729956" style="zoom:50%;" />

> 其中的RA是6，8，10管的等效电阻；RB是7，9，11管的等效电阻；RA，RB的计算可以借助小信号模型进行计算

> 此处拉扎维和艾伦的推导方式不同，结果有区别，有争议

#### 3，小信号

- 输入电阻结构一

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230923174059088.png" alt="image-20230923174059088" style="zoom:50%;" />

> 通过找直流电压（即交流地）得出输入电阻由8和10两管得到，随后画出等效电路

> 在等效小信号电路中，V~8B~= 0（接地），V~8S~= V~1~，V~8GS~= -V~1~；V~10GS~= V~X~

> 结论：8，10管构成的此结构等效于10管的二极管连接

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230923180404492.png" alt="image-20230923180404492" style="zoom:50%;" />

> 右半部分的输入电阻只于9和11有关，其中11管的基极和源极都接直流电压，故等效于一个电阻

> 结论：共源共栅的等效电阻等于负载管的输出电阻与增益管的本征增益之积

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230923181054570.png" alt="image-20230923181054570" style="zoom:50%;" />

> 负载部分可以增加管子的数量以获得更大的增益

- 输入电阻结构二（折叠共源共栅差分对）

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230923174547605.png" alt="image-20230923174547605" style="zoom:50%;" />

> 先找交流地，得出输入电阻由6，8，10管构成，随后8和10管的等效为一个阻值为1/g~m10~的电阻，画出等效小信号电路

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230923181336432.png" alt="image-20230923181336432" style="zoom:50%;" />

> 假设管子的跨导和输出电阻都相等的时候得到电路的输出结构为r~o~

- 增益

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230923182352734.png" alt="image-20230923182352734" style="zoom:50%;" />

- 拉扎维辅助定理

 <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230923191405283.png" alt="image-20230923191405283" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230923191823961.png" alt="image-20230923191823961" style="zoom:50%;" />

> 利用拉扎维辅助定理求解电路增益：
>
> 1，求I~out~：输出端对地短路（即输出端直接接地）求得
>
> 2，求R~out~：输入接地，利用小信号模型求结果
>
> 3，输出电压 = I~out~ ✖ R~out~
>
> 4，增益 = 输出电压 / 输入电压

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230923192953853.png" alt="image-20230923192953853" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230923194018842.png" alt="image-20230923194018842" style="zoom:50%;" />

> 利用拉扎维辅助定理分析右半边电路的短路电流，当输出端接地后，就不是7，9，11三管的串联，故R~B~只由7管构成，<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230923200107761.png" alt="image-20230923200107761" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230923194609020.png" alt="image-20230923194609020" style="zoom:50%;" />

> 输出电阻求解：首先求9，11管的，11管的基极和源极接直流电压，故等效为一个电阻，经过9管的本征增益的放大，故9，11管的电阻等效为<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230923200456193.png" alt="image-20230923200456193" style="zoom:50%;" />；上面由2，5，7管构成，2，5管作为负载经过7管本征增益放大，电阻等效为<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230923200706025.png" alt="image-20230923200706025" style="zoom:50%;" />

> 对比拉扎维和艾伦对于折叠型共源共栅的增益求解结果不同，拉扎维的更有理有据一些

#### 4，以共源共栅差分对为例的偏置电路设计

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230923201906336.png" alt="image-20230923201906336" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230923203114411.png" alt="image-20230923203114411" style="zoom:50%;" />

> 尾电流源偏置：直接通过电流镜将参考电流复制给M~3~即可，故无需求V~nb1~，只要设置好电流镜中两个管子的宽长比就可得到M~3~管的电流

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230923204743856.png" alt="image-20230923204743856" style="zoom:50%;" />

> 三条通路的电流一样，对应位置的管子的宽长比一样，并且M~14~管和M~13~管由于是二极管连接型，故肯定工作于饱和区，v~pb1~的大小可以保证4管和5管导通，v~pb2~的大小可以保证4管和5管在饱和区工作

> v~nb2~的偏置可以通过本身电路的结构变化自偏置得到，见下图绿框内容

> 结果：得到了一个随动的偏置

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230923210606729.png" alt="image-20230923210606729" style="zoom:50%;" />

> 偏置电路表面是产生直流电压，实质是设计直流电流，再通过电流镜的方式输入电路

#### 5，==折叠共源共栅差分对的设计与仿真==

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230924090010911.png" alt="image-20230924090010911" style="zoom:50%;" />

> 增益带宽积 = 增益A~V~ * 主极点p~out~

- 设计要求

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230924092710947.png" alt="image-20230924092710947" style="zoom:50%;" />

- 设计

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230924091545354.png" alt="image-20230924091545354" style="zoom:50%;" />

> 第二条，令10和11管的电流大于3管的（当3和10，11管的电流相等时，不需要负载管提供电流，可能会导致10或11管上面的管子没有电流，不工作），这样可以让这六个负载管一直处于导通，当电路开始工作时，可以更快进入工作状态

> 第三条，电路总电流等于10和11管的电流之和，故为2.4I~3~

> 第四条，总功耗为2.5mW,除以电压得到总电流为500，故令I~3~为200

> 第五条，增益带宽积GB = 跨导 / 负载电容

> 第六条，过驱动电压设为200mV
>
> 第七条，由于是电流镜，过驱动电压可以设的高一点，使管子工作在过饱和状态，可以更准确的镜像电流

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230924093722145.png" alt="image-20230924093722145" style="zoom:50%;" />

##### 电路设计时的过驱动电压经验：

> 经验：==差分对的过驱动电压一般为100mV左右==（管子可能工作于亚阈值区，在亚阈值区中同样的I~D~可以获得更大的跨导）；==电流镜的过驱动电压一般取高于250mV==（处于过饱和状态时电流的镜像会更准）；==剩下的管子过驱动电压一般取值为200mV左右==
>
> 设计时先a按照上述进行设计，随后进行仿真，根据结构进行对应的调整

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230924095515493.png" alt="image-20230924095515493" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230924100423815.png" alt="image-20230924100423815" style="zoom:50%;" />

> R~1~可以比计算出的值大一些，可以使M~12~的V~GS~更大些，更容易工作在饱和区

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230924102621100.png" alt="image-20230924102621100" style="zoom:50%;" />

### 第五节 轨对轨差分对



### 课后习题：

[CMOS模拟集成电路习题答案-ALLEN版(181) - 豆丁网 (docin.com)](https://www.docin.com/p-709365372.html)
