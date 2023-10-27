# 低压差线性（LDO）稳压器设计

低压差线性（Low Dropout，LDO）稳压器

> 性能优势：低静态电流和较大的带宽，较大的带宽会产生快速的瞬态响应
>
> 缺陷：电源转换效率较低（输出电压与输入电压的比值较小）

## 一，LDO基本结构

​                                 <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231014192158818.png" alt="image-20231014192158818" style="zoom: 33%;" /><img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231014192226069.png" alt="image-20231014192226069" style="zoom:50%;" />

- 使用蓄水池和水盆解释LDO系统

​				蓄水池——输入电压V~IN~；水盆——输出电容；

​				水龙头——功率晶体管；水龙头管口——功率晶体管的驱动能力；

​				水盆中水的高度——输出电压 V~OUT~ 的大小；水盆流出的水流——负载电流；

​		在动态平衡机制下，流入和流出水盆的水保持动态平衡。（保持输出电压不变，稳压）

​		水龙头可以快速或缓慢的旋转，以确定在输出负载电流变化的情况下，水位能多快的到达期望的水位。（反馈的调节控制速率）

​		水龙头的大管口可以向水盆内输送高电流，但水龙头会受到误差放大器驱动能力的限制，故对于水龙头的控制需要误差放大器具有良好的驱动能力。（误差放大器需要良好的驱动能力（驱动能力即输出电流的能力））

​		如果输出负载电流由高到低变化，由于没有多余的水流出水盆的额外途径，水位将在短时间内保持较高水平；如果直接增加一个额外途径将水流出，会造成资源的浪费。可见水盆并不是一个合适的设计。（输出电容对于负载电流变化的应对方式不太好）

​		总结两个问题：误差放大器的驱动能力与水龙头的尺寸有关，会影响到蓄水池到水盆的快速电流传输；水盆的尺寸精度其中存储水的容量，在输出负载电流突然变化时，会影响到水位的保持。

​		针对两个问题考虑在输出节点处和误差放大器的输出处增加两个大电容。

## 二，补偿技术

### 2.1 极点分布

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231015095325054.png" alt="image-20231015095325054" style="zoom: 33%;" />

​		极点P~0~和P~1~分别是LDO的输出和第一级误差放大器的输出。

​		在误差放大器的输出端和传输晶体管的栅极存在**大的寄生电容C~par~和大的输出电阻r~OUT~**（需要静态电流较小，故r~OUT~值较大）,使得**P~1~小于P~0~**。

​		为了提高PMOS的驱动能力，增大其尺寸，导致**米勒电容C~GD~**足够大，**使得两个极点被分裂开来**，系统更稳定，此时P~1~^‘^ 为系统主极点。

> 米勒电容的作用使得极点P~0~ 和P~1~ 分裂开来，得到P~0~^'^ 和P~1~^'^ 

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231015103258276.png" alt="image-20231015103258276" style="zoom: 33%;" />

​		为了**应对负载电流突变**的情况，**在输出端连接一个大的输出电容**以维持输出电压。但因为输出电容的接入，**导致输出极点频率减小**，输出极点向原点移动，两个极点靠近，系统稳定性降低。由于输出电容很大，**输出极点P~0~成为系统主极点**。

​		两个低频极点会引起相位裕度的恶化，为了系统的稳定性，此时应该要将P~1~^’^ 极点向高频方向移动，将两个极点拉开，或者增加零点抵消此极点的影响。

​		**P~1~^’^ 极点频率低**主要是因为需要低静态电流而使得**误差放大器的输出电阻非常大造成**，功率PMOS栅极的电阻/电容时间（RC常数）会非常大，**静态电流的大小和误差放大器对于PMOS管的驱动能力互斥**。

> 输出电容的作用，将P~0~^'^ 的频率降低得到极点p~0~^*^

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231015110435948.png" alt="image-20231015110435948" style="zoom: 50%;" />

​		为了解决静态电流的大小和误差放大器对于PMOS管的驱动能力互斥的问题，可在误差放大器的输出和功率PMOS栅极之间**插入一个缓冲级**，可**同时提高驱动能力和相位裕度**。

​		缓冲级将低频极点P~1~^'^ 分裂为两个高频极点 P~1~^*^ 和P~1~^**^，其中缓冲器的输出极点P~1~^**^ 的RC时间常数为C~IN(buf)~r~OUT~（缓冲器的特性，C~IN(buf)~和r~OUT~都小），故P~1~^*^ 成为第一非主极点。

> 缓冲器的作用，低频极点P~1~^'^ 分裂为两个高频极点 P~1~^*^ 和P~1~^**^，且P~1~^*^频率小于P~1~^**^

​         <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231015153731069.png" alt="image-20231015153731069" style="zoom: 50%;" />             <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231015153754403.png" alt="image-20231015153754403" style="zoom: 50%;" />   

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231015153847108.png" alt="image-20231015153847108" style="zoom:50%;" />

​		缓冲级的存在可将一个低频极点分裂得到两个高频极点，为了将两个高频极点推向更高频，可以通过设计使缓冲器的**等效输出电阻减小**，从而**使两个高频极点被推向更高频**。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231015160026294.png" alt="image-20231015160026294" style="zoom:50%;" />

​		**使用缓冲级后**，可以使得非主极点的频率推向更高频率，故主极点（即输出极点）的频率范围可以增大一些，即输出电容的值可以减小一些，即**输出电容的尺寸可以减小**。然而片上电容的范围在几皮法，输出电容的范围为几微法，故使用了缓冲级后虽然可以减小输出电容的尺寸，也**无法直接通过片上电容取代外部输出电容**。

​		LDO稳压器小型化的办法：（1）主极点补偿：使用大输出电容，可以应对负载电流突变的问题；如果大电容被移走，就可以使LDO尺寸减小，但此时就**需要系统带宽很大**，功率晶体管可以迅速开断，**以应对负载电流突变的问题**。（2）米勒补偿：无需加入外部输出电容，**增加米勒电容C~m~，获得一个大带宽**。

​		图中增加了米勒电容，去掉了输出大电容，输出极点P~0~^'^ 向高频率移动成为P~0~^'''^，同时误差放大器的输出极点P~1~'向低频方向移动成为P~1~''，此时P~1~''成为新的主极点。通过米勒补偿的好处在于米勒电容相比原来的输出电容很小。此外，另一个米勒电容C~GD~ 可以将P~2~和P~0~'' 向高频率分离。

> 米勒电容的作用，误差放大器的输出极点P~1~'向低频方向移动成为P~1~''，P~1~''成为新的主极点

### 2.2 零点分布和右半平面零点

​		在SoC应用中，LDO稳压器面临**很大的负载变化**，故**需要有一个良好的瞬态负载响应**，LDO的**带宽需要很大**。

​		**为了拓展带宽**，**左半平面（LHP）零点被用来消除第一非主极点的影响**。

![image-20231015172608182](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231015172608182.png)

产生LHP零点的方法：

1. 在输出电容处等效串联电阻来产生左半平面零点：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231015193523990.png" alt="image-20231015193523990" style="zoom: 33%;" />

> 电阻的阻值受温度影响较大，此外，负载电流变化时会在电阻上有一个较大的压降，导致功率晶体管电压变化很大

2. 米勒电容会产生一个右半平面的零点（由v~i~到v~o~，再通过C~m~的回路造成），明显的影响了系统稳定性（带来了20dB/十倍频和-90°的相位变化）。可通过调零电阻R~Z~和C~m~串联将右半平面的零点移动至左半平面。

> <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231015201708297.png" alt="image-20231015201708297" style="zoom: 33%;" />

​		当电阻值大于管子的跨导时，即可将零点移至左半平面。

3. 通过一个源极跟随器和米勒电容的串联去除右半平面的零点：

> [【模拟IC学习】多个角度理解零极点以及与电容充放电的联系 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/266926681)

​		C~m~两端的压差保持为v~i~ - v~o~，从输入端看进去输入电容等于C~m~和C~gs~ 的串联等效，比原始电容更小，即右半平面零点会向无穷远的方向移动，最终生成一个左半平面零点。<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231015220325609.png" alt="image-20231015220325609" style="zoom: 33%;" />，但此结构的缺点是输出摆幅的限制。

4. 利用共栅结构消除右半平面的零点：输出电压以电流的形式通过电容C~m~和M~2~流至输入端。

## 三， LDO稳压器设计考虑

#### 3.1 电压差

​		功率晶体管两端的电压被定义为V~dropout~，<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231016084435364.png" alt="image-20231016084435364" style="zoom: 50%;" />，其中R~on~是功率晶体管的等效阻抗。

​		LDO稳压器主要有两个用途：（1）作为电压转换器提供步降供应电压，牺牲电源效率换取大压差；（2）作为后级稳压，减小低噪声电压的噪声。

#### 3.2 效率

#### 3.3 线性/负载调整率

​		输入电压和输出负载电流分别出现扰动的时候，输出电压变化的百分率。

- 线性调整率：因输入电压线性变化导致的输出电压变化

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231016094310253.png" alt="image-20231016094310253" style="zoom:33%;" />

> 其中L~O~是稳压器的环路增益；

- 负载调整率：负载电流变化导致输出电压变化

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231016095537057.png" alt="image-20231016095537057" style="zoom:33%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231016095515608.png" alt="image-20231016095515608" style="zoom: 33%;" />

#### 3.4 负载电流突变引起的瞬态输出电压变化

​		LDO的动态特性通过负载瞬态响应和线性瞬态响应检测。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231016101505458.png" alt="image-20231016101505458" style="zoom: 33%;" />

​		负载电流突变增大，输出的瞬态电压可以分为四个部分：（1）输出电容的等效串联电感引起的电压差V~1~（2）输出电容的等效串联电感引起的电压差V~2~（3）当负载电流已经变为I~LOAD(heavy)~，等效串联电感展现了上升效果

​		假定负载电流变化，传输器件不能马上提供足够的负载电流，需要一定的时间打开以获得大电流。其中Δt1取决于闭环带宽和功率晶体管的栅极转换速率。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231016132340378.png" alt="image-20231016132340378" style="zoom:33%;" />

> 其中C~par~是功率晶体管栅极的寄生电容，I~sr~是误差放大器的偏置电压，BW~cl~ 是轻负载时的带宽

​		类似的，<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231016132715836.png" alt="image-20231016132715836" style="zoom:33%;" />，两者值不同，因为带宽在轻负载和重负载时不同。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231016134810554.png" alt="image-20231016134810554" style="zoom: 33%;" />

​		当负载由重变轻或由轻变重时，输出电容作为缓冲器，通过电流流入或电流流出的方式应对负载电流的变化；同时电流流经串联电阻R~ESR~ 时引起输出瞬态电压的明显变化，故等效串联电阻越小越好。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231016135304773.png" alt="image-20231016135304773" style="zoom:33%;" />

​		当负载由重变轻时，负载电流会突然减小，输出瞬态电压增大变为过冲电压，此过冲电压可通过反馈分压电阻的漏电流来耗散，故输出电压下降的斜率取决于分压电阻的值。

​		线性瞬态响应于与负载瞬态响应类似。

- 改善动态和瞬态响应的方式：采用宽带宽的闭环电路、在功率MOS管的栅极处实现快速压摆率、使用大输出电容并降低等效串联电阻。

## 四，模拟LDO稳压器

​		模拟LDO稳压器的设计策略根据补偿技能可分为两个基本类别。

​		第一类，使用大输出电容，主极点位于输出端；第二类，称为无电容或少电容LDO稳压器，主极点由米勒电容产生，而不需要使用大的输出电容。

### 4.1 主极点补偿的特性

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231016180316232.png" alt="image-20231016180316232" style="zoom: 33%;" />

​		大输出电容C~OUT~ 可以保证**主极点位于输出节点**；在PMOS的栅漏处存在米勒电容C~gd~，此米勒电容和（1 + A~V(Mp)~）的乘积确定了栅极的总寄生电容C~par~（其中的A~V(Mp)~是PMOS的增益），**PMOS栅极处的极点称为第一非主极点**<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231016183612593.png" alt="image-20231016183612593" style="zoom:33%;" />；

​		主极点补偿技术将合适的输出阻抗网络连接到输出节点。输出阻抗网络包括两个电容大输出电容C~OUT~和旁路电容C~b~，其中C~b~ < C~OUT~。

​		C~OUT~和C~b~贡献两个极点：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231018194042211.png" alt="image-20231018194042211" style="zoom:33%;" />，<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231018194101606.png" alt="image-20231018194101606" style="zoom:33%;" />（<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231018194115242.png" alt="image-20231018194115242" style="zoom:33%;" />)；R~ESR~贡献一个零点：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231018194216129.png" alt="image-20231018194216129" style="zoom:33%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231018194241723.png" alt="image-20231018194241723" style="zoom: 33%;" />



