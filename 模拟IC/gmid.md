[gm/Id的模拟电路设计方法（1）——基本概念 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/330778800)

[gm/Id的模拟电路设计方法（2）——电路仿真 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/330786388)

[gm/Id 设计方法_gmid设计方法-CSDN博客](https://blog.csdn.net/maxwell2ic/article/details/53374219)

[先进工艺中的集成电路设计-gm/Id设计方法 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/435397746)

[The gmid methodology, a design guideline for two stage miller OP_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1PZ4y1g7cZ/?spm_id_from=333.999.list.card_archive.click&vd_source=719585e47d53d8b6dbacff76aa9b996e)



[运用gm/id法设计二级运放教程_gmid设计方法_whisperun的博客-CSDN博客](https://blog.csdn.net/whisperun/article/details/128147835)		

[差分运放（5管OTA） Cadence电路搭建+仿真+版图设计 差分放大电路 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/597804159)

[模拟CMOS集成电路设计中的电流基准源及用Cadence Virtuoso IC617设计并仿真有关电路_基准电流源-CSDN博客](https://blog.csdn.net/weixin_44115643/article/details/119901330)

[菜鸡渣渣一个_Cadence Virtuoso IC有关,ADS（Advanced Design system）有关,HFSS（ANSYS Electronics）有关-CSDN博客](https://blog.csdn.net/weixin_44115643?type=blog)



[模拟IC设计-LDO电路设计与仿真实战-part1-原理和基本电路设计与仿真_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1sS4y1S7eb/?vd_source=719585e47d53d8b6dbacff76aa9b996e)

[闹钟不要叫醒我的个人空间-闹钟不要叫醒我个人主页-哔哩哔哩视频 (bilibili.com)](https://space.bilibili.com/381767358)



[基于virtuoso IC 618的LDO仿真实验_落枫微蔷的博客-CSDN博客](https://blog.csdn.net/qq_33599939/article/details/124857199)

[【精选】低压差线性稳压器(LDO)设计与仿真_ldo仿真_Metaa2227的博客-CSDN博客](https://blog.csdn.net/qq_50968231/article/details/126136089)

[用Cadence Virtuoso IC617设计低压降 (LDO) 线性稳压器-CSDN博客](https://blog.csdn.net/weixin_44115643/article/details/119996343)

[90分钟速成LDO电源设计实战大法_哔哩哔哩_bilibili](https://www.bilibili.com/video/BV1N7411K71M/?vd_source=719585e47d53d8b6dbacff76aa9b996e)

[先进工艺中的集成电路设计-gm/Id设计方法 - 知乎 (zhihu.com)](https://zhuanlan.zhihu.com/p/435397746)



---

# 一，gm/id设计方法

​		**V~GS~、V~DS~、W、L为目标参数；**

​		**晶体管跨导g~m~、沟道调制电阻r~o~、寄生电容C~gs~以及漏极电流i~d~为设计参数。**

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231022210620922.png" alt="image-20231022210620922" style="zoom:50%;" />

​		**g~m~r~o~：本征阻抗；g~m~/C~GG~：表征晶体管可以放大信号的最高频率**

1. 简化目标参数：

- V~DS~：一般没啥可设计的

​		举例：在电流源为负载的共源极放大器中，晶体管全部都工作在饱和区，两个管子的V~DS~均取电源电压的一半，可以使放大器有最大的输出摆幅；在套筒式共源共栅放大器中，从地到电源电压共有5个晶体管堆叠，故每个管子的V~DS~ = V~DD~ / 5。

- W：增大W，gm会成比例增大（跨导与宽长比呈正相关），寄生电容CGG会成比例增大（寄生电容与面积呈正相关），但是ro会成比例减小（g~ds~与面积呈正相关）。

​		因此，在VGS以及L不变的情况下，晶体管的W会影响gm、ro以及CGG的绝对大小，但是不会影响gmro，gm/CGG的值。

- V~GS~：**在晶体管的W、L以及VDS不变的情况下，增大VGS时，晶体管的本征增益gmro会降低，频率特性gm/CGG会上升。**

- L：**在晶体管的W、VDS以及VGS不变的情况下，增大晶体管的沟道长度L时，晶体管的本征增益gmro会上升，频率特性gm/CGG会下降。  **

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231022213253850.png" alt="image-20231022213253850" style="zoom: 50%;" /><img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231022213311275.png" alt="image-20231022213311275" style="zoom: 50%;" />

2. gm / id：

​		在实际设计中，噪声与带宽，通常是与功耗强相关的，即**功耗是噪声与带宽的主导因素**，因为这二者往往由输入级的gm直接决定，而gm主要由id影响。

​		想在固定的功耗情况下，降低噪声并提高带宽，因此如何使单管在固定的id情况下，得到较高的gm，是具有重要意义的。

![image-20231022213500182](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231022213500182.png)

​		宽度和VDS不变时，晶体管的gm/id随VGS，L的变化关系，可以看到，晶体管的**gm/id与VGS强相关，和晶体管的L呈现弱相关**。

​		**VGS与晶体管的gm/id能构成近似的一一对应的关系，VGS越大，gm/id越小，也就是说晶体管的跨导效率越小。**

- 在晶体管的静态电流Id，L保持不变的情况下，增大晶体管的W/L，会使得晶体管的VGS减小，则根据上述三组曲线，晶体管的本征增益gmro会增加，频率特性gm/CGG会下降，晶体管的功耗效率提升，即能够获得更大的跨导gm；
- 在晶体管的静态电流Id，W/L保持不变的情况下，增大晶体管的L，根据上述三组曲线，晶体管的VGS基本保持不变，功耗效率保持不变，即获得的跨导gm不变，晶体管的本征增益gmro会增加，频率特性gm/CGG会下降。

![image-20231022220132008](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231022220132008.png)

# 二，单管gmid设计实例

设计指标如下：

​		漏极电流id = 100uA

​		本征增益gmro > 100

​		截止频率gm/CGG > 30GHz

​		跨导gm > 0.8mS

![image-20231022220412302](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231022220412302.png)

1. 先根据电路进行仿真，得到三个曲线图

![image-20231022220843761](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231022220843761.png)

2. 先看gm/id-vgs图：

​		根据指标（漏极电流id = 100uA和跨导gm > 0.8mS）确定gm/id的范围；

​		从而确定vgs的范围；

​		再结合指标（本征增益gmro > 100和截止频率gm/CGG > 30GHz）确定L的范围

![image-20231022221946816](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231022221946816.png)

​		综上，最后确定L范围在540nm左右（即图中绿色曲线），且650mV<vgs<675mV之间。

> 此时可以确定参数：L = 540n，vgs = 660m

3. 为了确定W的值（vgs、id、L均确定时，W也已经确定），进行参数W扫描，找到符合指标（id = 100μA）的W

![image-20231022222912258](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231022222912258.png)

> 此时可确定W = 7.5u

4. 进行单点的仿真，验证所选参数结果是否符合指标

![image-20231022223346859](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231022223346859.png)

# 三，单端共源极放大器设计实例

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231022223537399.png" alt="image-20231022223537399" style="zoom:50%;" />

设计指标：（暂时忽略输出摆幅这一指标）

​		电源电压VDD = 1.2V

​		输出直流电压 ≈ 0.6V

​		漏极电流id = 100uA

​		负载电容CL = 1pF

​		直流电压增益 Av > 42dB

​		单位增益带宽GBW > 100MHz

​		等效输入噪声电压（积分1KHz ~ 1MHz） < 8uV

1. M1初值选取

> 注：此次设计不考虑ft——gm/gcc的作用，原因是指标中的GBW对频率要求太低，通常在设计GHz以上的放大器时才会考虑
>
> 注：此次设计不考虑寄生电容的影响；
>
> **真正可以忽略寄生电容的原因有二**：
>
> 第一，合理的设计中，放大器的带宽，应该取决于输入管的gm与负载电容CL（二级运放中为密勒补偿电容）。
>
> 第二，本次设计为单级放大器，只存在一个输出极点，无需考虑稳定性问题，即无需考虑寄生电容引入的次极点。

- 选取放大管M1的初值

​		对放大管的要求：

​		其一，**需要有足够的跨导gm1**，因为在忽略寄生电容时，GBW = gm1/CL，同时输入管的跨导也会显著影响放大器的噪声性能。（放大管跨导影响输出极点的频率）

​		其二，**需要有足够的本征增益**，因为在合理的设计中，负载管M2的输出阻抗应该大于M1。

​		根据第一个要求，通过GBW=100MHz与CL=1pF，可以计算出此时的gm1=0.628mS，噪声对gm1的要求由于与工艺相关，无法直接计算，需要仿真确认（对噪声的设计，建议通过仿真调参数，因为噪声与工艺参数强相关，且同时存在热噪声与闪烁噪声，前者与gm强相关，后者与尺寸强相关）。这里保险起见，取gm1>0.7mS，即gm/id>7。==参考单管的gm/id曲线==，我们可以得到：**VGS1<0.7V**

​		而根据第二个要求，要求M1的本征增益gm1ro1>42dB，==参考单管的gmro曲线==，结合上述的VGS1<0.7V，我们可以在这范围内任意选取一组参数，这里初值选取为**VGS1=0.65V，L1=720nm**。

​		通过扫描参数得到id = 100uA所对应的W，**W1此时为10.35um**。

2. 放大管初值仿真&调整

- 先进行单管仿真如下

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231022225248838.png" alt="image-20231022225248838" style="zoom:50%;" /><img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231022225308186.png" alt="image-20231022225308186" style="zoom:50%;" />

​		判断单管的性能达标，随后进行电路仿真。

- 进行放大管电路的仿真

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231022225545574.png" alt="image-20231022225545574" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231022225701339.png" alt="image-20231022225701339" style="zoom:67%;" />

​		得到ac仿真的增益结果：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231022225822887.png" alt="image-20231022225822887" style="zoom:67%;" />

​		符合指标。

​		进行噪声仿真：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231022230255118.png" alt="image-20231022230255118" style="zoom:67%;" />

​		噪声电压为9.46uV，不符合指标。

​		对于单管来说，噪声来源为热噪声（增大gm改善）和1/f噪声（增大面积改善），选择通过增大gm进行改善。通过单管的三个曲线可知，增大gm，就是减小vgs，令L和vgs不变，W会增大（面积增大，1/f噪声也降低）。

​		将vgs减小至0.6V，随后进行W的参数扫描，找到id = 100uA对应的W为17.4u。

​		仿真如下：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231022231502730.png" alt="image-20231022231502730" style="zoom:67%;" />

> 将M1的参数调整为L1=720nm，VGS1=0.6V，W1=17.4um

3. 负载管M2初值选取

​		负载管要求：

​		其一，**需要有足够大的输出阻抗ro2**，至少大于ro1，以保证直流增益接近于M1的本征增益。

​		其二，**我们希望gm2足够小**，这样可以减小负载管的噪声电流。

​		对于第一点，我们知道，在固定的漏极电流情况下，**增大输出阻抗最主要的方式是增大管子的L**，在这里我们先认为至少L2 > 3*L1时，对直流增益影响较小。

​		而对于第二点，根据gm/id曲线可知，增大VGS可以降低跨导效率，即固定id情况下减小gm。

​		结合以上两点，**我们对负载管M2的参数要求是：较大的L，以及较大的VGS**。

> 并不是L以及VGS越大越好：
>
> 第一，**固定的VGS情况下，增大L会同比增大W，在面积显著增加的同时，会导致寄生电容显著增大**，过大的L会有破坏前文“忽略寄生电容”这一前提的风险，在这里我们**限定L2 < 10*L1**
>
> 第二，**固定的L情况下，增大VGS，事实上会降低运放的上摆幅，恶化线性度**，尽管在本次设计中没有考虑线性度，但同学们应该知道负载管的VGS也并非越大越好，在这里我们**限定VGS2<0.9V**。

​		负载管M2的初值选取为：**L2 =2.2um，VGS2=0.8V，再通过扫描W得到其宽度W2=56.5um**。

4. 负载管电路仿真&调整

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231022232056144.png" alt="image-20231022232056144" style="zoom: 50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231022232243533.png" alt="image-20231022232243533" style="zoom:67%;" />

​		可见直流增益41.81不符合指标，原因负载管的输出阻抗不够大，增大L（增大L后要重新进行W参数扫描确定W）。

​		通过对负载管PMOS进行单管仿真确定相应参数。

> PMOS单管仿真电路：
>
> <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231022232625017.png" alt="image-20231022232625017" style="zoom: 50%;" />
>
> <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231022232657655.png" alt="image-20231022232657655" style="zoom:50%;" />

​		调整后结果如下：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231022232931440.png" alt="image-20231022232931440" style="zoom:67%;" />

​		符合指标。

> M2的参数调整为L2=4um，VGS2=0.8V，W2=100um

> ==固定id的情况下，提升性能手段：==
>
> <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231022233112011.png" alt="image-20231022233112011" style="zoom:67%;" />

# 四，二级运放

设计指标：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231024095633179.png" alt="image-20231024095633179" style="zoom: 80%;" />

1. DC工作点

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231023222805286.png" alt="image-20231023222805286" style="zoom: 80%;" />

​		M0、M1：第一级PMOS放大管，其尺寸（W、L）应完全相同，且在DC工作点处，栅极电压（两个输入电压）也完全相同。

​		M2：第二级NMOS放大管。

​		M5、M6、M7：PMOS电流镜，三者的L应完全相同。M5为第一级的尾电流，M6为第二级的负载管，而M7为电流镜的自偏置管。

​		电容Cc：密勒补偿电容。在这里起到“极点分离”的作用。

- 简单分析一下各个管子如何饱和：首先**M7和M3两个管子导通后肯定饱和**（二极管器件连接），设M3与M7的Vgs为Vgs3与Vgs7，那么第一级的输入管M0的漏极电压与M5的栅极电压就被确定了。

​		**输入共模电平V~CM~应当：V~CM~ ≥ V~gs3~ - |V~TH0~| ;且 V~CM~ + V~gs0~ ≤ V~DD~ - V~gs7~ + |V~TH5~|**

​		根据共模电压输入范围可以保证M0，M3，M5处于饱和，此时M1和M4一定处于饱和。

> M1和M4一定处于饱和，因为**图中A与B两点的电压一定是相等的**
>
> 证明：假设B点电压大于A点，由于M0和M1的V~gs~相等，M3和M4的V~gs~也相同，且存在沟道长度调制效应，由于B点电压大于A点，导致V~ds4~ > V~ds3~，V~ds0~ > V~ds1~，故M1的电流会小于M0，而M4的电流则大于M3。即<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231023225118359.png" alt="image-20231023225118359" style="zoom: 80%;" />，矛盾。同理可证B点电压小于A点电压也是矛盾的，即B点电压等于A点电压，所以只要M0、M3饱和，M1、M4就一定饱和。。

​		因为Vgs6已经被Vgs7确定，同时Vgs2由Vgs3确定（因为A、B两点电压相等），在管子选定尺寸后，会代表两个确定的饱和区电流，而这两个电流很难恰好一致，因此M2与M6的电流只能等于其中较小的一个饱和电流，而另一个管子只能处于线性区。

> 最简单的说，假设M6饱和且尺寸确定，由于Vgs6确定，则M6的饱和电流确定，相当于确定了M2的饱和电流，而Vgs2也被Vgs3确定，那么M2的宽长比就被确定了，只有在考虑沟长调制效应时，这一宽长比才可以在一个很小的范围内变化，超出范围则无法同时饱和！

​		运放的第二级，**M2与M6选择通过反馈的方式来保证运放共模点稳定**。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231023225829365.png" alt="image-20231023225829365" style="zoom: 67%;" />

​		因此Vout的DC电压不再由M2、M6的电流相等的方程得到，而是直接由Vin+的DC电压，即输入共模电压VCM确定。

​		**M6的饱和**条件：V~in+,dc~ ≤ V~DD~ - V~gs6~ + |v~th6~|。

​		在负反馈的存在下，运放可以自动调节V~gs2~，即B点电压，使M2电流恒等于M6的饱和电流，只要保证 V~gs2~ ≤ V~in+,dc~ + V~TH2~ ，即可保证**M2饱和**。

​		保证M2与M6同时饱和的边界条件：V~gs2~ -  V~TH2~ ≤ V~in+,dc~ ≤ V~DD~ - V~gs6~ + |v~th6~|

​		引入反馈后，A、B两点的电压可能存在不一致，其中A点的电压几乎不受M2尺寸的影响，B点的电压被反馈确定为V~gs2~。故为保证与B点关联的两个管子M1和M4均饱和，V~gs2~应满足： V~gs4~ - V~TH4~ ≤ V~gs2~ ≤ V~in+,dc~ + |V~TH1~|，综合第一级饱和对于M2尺寸的约束，最终V~gs2~范围为：

​		V~gs4~ - V~TH4~ ≤ V~gs2~ ≤ V~in+,dc~ + |V~TH1~| ≈ V~in+,dc~ + V~TH2~

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231023232050277.png" alt="image-20231023232050277" style="zoom: 80%;" />

2. GBW与PM：

> 如何通过GBW和PM得到合适的小信号参数（第一级跨导gm1、第二级跨导gm2以及密勒补偿电容Cc）

- ==指标分析与转化==

​		引入的为单位增益负反馈，故环路增益为LG = - A~open~ * F = - A~open~

​		GBW，增益带宽积（或叫单位增益带宽），直接与运放传输函数中的极零点相关联。

​		相位裕度，GX的相位与PX相位（-180°）的差。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231024095128999.png" alt="image-20231024095128999" style="zoom:67%;" />

​		其中A点处引入的一对极零点对，寄生电容引入的零点位于它引入的极点的二倍处，且该零点为负零点，可以很大程度上补偿自身引入的极点，因此我们认为这一极零点对频率响应影响较小。

​		但由于极点在零点之前，因此我们这里给这一因素留有设计裕量，认为**这一极零点对“吃掉”了5°的PM**，而忽略这一对极零点对频率响应的其他影响。

​		对于PM这一指标的分析与转化：

![image-20231024110444186](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231024110444186.png)

​		经过分析，将相位裕度PM这一指标转化成了次极点、零点的频率与GBW的关系。

- ==零极点计算==

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231026103629266.png" alt="image-20231026103629266" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231026103657407.png" alt="image-20231026103657407" style="zoom:67%;" />

其中：

​		Rn1为第一级的输出阻抗，由M1与M4的输出阻抗并联构成；

​		Cn1为第一级输出节点对地的寄生电容（不包含补偿电容的密勒效应），由M1、M4的漏极电容以及M2的栅极电容构成；

​		RL为第二级的输出阻抗，由第二级的两个管子——M2、M6的输出电阻并联组成；

​		CL为二级运放的负载电容，由指标决定为1pF，会被M2、M6的漏极电容略微影响。

![image-20231026141544898](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231026141544898.png)

> 零极点以及GBW式子简化说明：
>
> - <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231026142539654.png" alt="image-20231026142539654" style="zoom:80%;" />
>
> - 由于Cc与CL通常为同一量级，而Av2较大，因此<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231026141758306.png" alt="image-20231026141758306" style="zoom:67%;" />，故<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231026141822621.png" alt="image-20231026141822621" style="zoom:80%;" />，<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231026141841557.png" alt="image-20231026141841557" style="zoom: 80%;" />。
> - 由于Cc通常与CL在同一数量级但小于CL，同时Cc通常大于Cn1的三倍，故![image-20231026142133360](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231026142133360.png)≈ C~n1~C~L~ + C~c~C~L~ ，更甚者可直接 ≈ C~c~C~L~ 。

- ==计算小信号参数==

![image-20231026145042760](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231026145042760.png)

- ==小信号模型仿真验证==

​		基于前几步所得的公式

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231026145624212.png" alt="image-20231026145624212" style="zoom:50%;" />

​		得到下表，用于对管子和电容进行调整优化：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231026145409202.png" alt="image-20231026145409202" style="zoom: 80%;" />

> 注：
>
> 1，增大gm1时ωnd略微减小是因为，增大gm1通常会导致寄生电容增大，即Cn1增大。
>
> 2，增大Cc时ωnd略微增大，也是因为考虑了Cn1。

- ==利用gm/id方法，得到放大管参数==

![image-20231027091637437](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231027091637437.png)

- ==放大管参数验证==

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231027091758134.png" alt="image-20231027091758134" style="zoom:67%;" />

- ==利用gm/id得到负载管参数==

![image-20231027100832446](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231027100832446.png)

> 其中对于负载管的gm/id方法选择gds/id和Cdd/id曲线的原因：
>
> 我们保持一个MOS管的Vgs、W、L不变（当然Vds也不变），将它完全复制一份，进行“并联”，显然此时的W相当于翻倍。显然，Id会翻倍，gm翻倍，gds翻倍，Cgg同样也是翻倍！
>
> 即gds/id和Cdd/id曲线与W，本质上是无关的！

随后进行gm/id的方式进行仿真，得到参数如下：

![image-20231027100922468](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231027100922468.png)

- ==负载管参数仿真==

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231027101318131.png" alt="image-20231027101318131" style="zoom: 67%;" />

- ==运放验证==

​		将电路中的电流源与M6的Vb用MOS管替换，构成电流镜。

​		尺寸与M6尺寸相同，只需要根据电流的数量关系改变MOS管的m值即可。

​		如果尺寸设置之后没有饱和或没有达到设计的电流值，需要通过对管子的长度和宽度进行进一步的调整，以符合设计指标。

==**步骤总结：**==

​		第一步，我们将PM的指标要求，转化为了对极零点位置的要求；

​		第二步，通过对二级运放进行小信号建模，得到了它的传输函数，以及GBW、零极点的简化表达式；

​		第三步，根据GBW、极零点表达式与其要求，计算得到表达式中的小信号参数；

​		第四步，仿真验证第三步中得到的小信号参数；

​		第五步，使用gm/Id方法，将放大管的小信号参数，转化为实际参数；

​		第六步，仿真验证第五步中得到的放大管参数；

​		第七步，使用针对负载管的gm/Id方法，将负载管的小信号参数，转化为实际参数；

​		第八步，仿真验证第七步中得到的负载管参数；

​		第九步，对二级运放做最后的调整、改进。