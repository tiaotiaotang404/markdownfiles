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

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230911215715819.png" alt="image-20230911215715819" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230911215834826.png" alt="image-20230911215834826" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230911220007653.png" alt="image-20230911220007653" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230911220205173.png" alt="image-20230911220205173" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230911220858875.png" alt="image-20230911220858875" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230911221900632.png" alt="image-20230911221900632" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230911221930537.png" alt="image-20230911221930537" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230911222821161.png" alt="image-20230911222821161" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230911223103357.png" alt="image-20230911223103357" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230912100222887.png" alt="image-20230912100222887" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230912100254207.png" alt="image-20230912100254207" style="zoom:50%;" />

### 第六节 带隙基准



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

> 为社么增益在极点处开始下降：电路中的某些电容在高频的情况下容抗变小，导致输出阻抗减小，增益下降。根据极点的式子可知与C~M~和C~out~有关。

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

> 共源极分析：用Q~2~举例，输入栅极电压增大，导致漏极电压减小，导致Q~2~的V~DS~减小，使之进入饱和区；
>
> 寄生电容分析：用Q~2~举例，由于输入电压增大，导致Q~2~电流增大，由于Q~4~电流不变，故只能通过寄生电容输出电荷补充Q~2~所需要的电流，导致V~out~电压下降，导致Q~2~的V~DS~减小，使之进入饱和区。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230918102715657.png" alt="image-20230918102715657" style="zoom:50%;" />

> 当输入电压低于最小共模电压，Q~5~先进入线性区

> 当输入电压降低，Q~1,2~的电流不变，只能降低Q~5~的漏极电压导致Q~~5~的V~DS~减小，进入线性区

#### 5，差分对设计指标二：增益带宽积

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230918104303583.png" alt="image-20230918104303583" style="zoom:50%;" />

> 直流增益，即低频增益，就是图中增益为A~V~的部分

> 增益带宽积=增益✖3dB带宽=常数，数值上等于小信号的带宽（增益为1时），即GB点

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230918112220106.png" alt="image-20230918112220106" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230918112244650.png" alt="image-20230918112244650" style="zoom:50%;" />

> 两个电路的放大倍数都是25倍，但由于GB的作用，第一个电路的带宽相较于第二个电路更小，故可以通过多级放大保证高增益的同时增大带宽。

#### 6，差分对的设计指标三：摆率

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230918112613414.png" alt="image-20230918112613414" style="zoom:50%;" />

> 摆率就是输出电压的变化速率。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230918113115850.png" alt="image-20230918113115850" style="zoom:50%;" />

> 增益带宽积为A，不代表电路的带宽为A，只有小信号（即低频信号）才能无畸变的通过，当大信号（即高频信号）输入时，由于摆率的限制会使得输出产生畸变。

> 图中的SR为摆率<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230918114320313.png" alt="image-20230918114320313" style="zoom:50%;" />









### 课gongyuan后习题：

[CMOS模拟集成电路习题答案-ALLEN版(181) - 豆丁网 (docin.com)](https://www.docin.com/p-709365372.html)
