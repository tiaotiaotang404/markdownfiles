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

​		在实际设计中，噪声与带宽，通常是与功耗强度相关的，即**功耗是噪声与带宽的主导因素**，因为这二者往往由输入级的gm直接决定，而gm主要由id影响。

​		想在固定的功耗情况下，降低噪声并提高带宽，因此如何使单管在固定的id情况下，得到较高的gm，是具有重要意义的。

![image-20231022213500182](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231022213500182.png)

​		宽度和VDS不变时，晶体管的gm/id随VGS，L的变化关系，可以看到，晶体管的**gm/id与VGS强相关，和晶体管的L呈现弱相关**。

​		**VGS与晶体管的gm/id能构成近似的一一对应的关系，VGS越大，gm/id越小，也就是说晶体管的跨导效率越小。**

![image-20231027150337422](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231027150337422.png)

- 在晶体管的静态电流Id，L保持不变的情况下，增大晶体管的W/L，会使得晶体管的VGS减小，则根据上述三组曲线，晶体管的本征增益gmro会增加，频率特性gm/CGG会下降，晶体管的功耗效率提升，即能够获得更大的跨导gm；
- 在晶体管的静态电流Id，W/L保持不变的情况下，增大晶体管的L，根据上述三组曲线，晶体管的VGS基本保持不变，功耗效率保持不变，即获得的跨导gm不变，晶体管的本征增益gmro会增加，频率特性gm/CGG会下降。

![image-20231027150404691](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231027150404691.png)

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

##### 使用HG_V0P4库实操：

1. nmos管

![image-20231028110727728](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231028110727728.png)

![image-20231028105345772](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231028105345772.png)

![image-20231028105500527](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231028105500527.png)

![image-20231028105520685](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231028105520685.png)

得到L = 540n , vgs = 660m；

![image-20231028105856706](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231028105856706.png)

得到W = 7.3u。

![image-20231028142605500](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231028142605500.png)

​		符合指标。

2. pmos管

![image-20231028112210561](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231028112210561.png)

![image-20231028112308377](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231028112308377.png)

![image-20231028113230885](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231028113230885.png)

![image-20231028112958737](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231028112958737.png)

> 由于NMOS通常具有更高的迁移率，这使得NMOS可以更快地切换；
>
> 故在近似尺寸下NMOS具有更高的切换速度和更大的带宽。

![image-20231028115207351](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231028115207351.png)

![image-20231028135245871](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231028135245871.png)

​		可见带宽满足要求，但增益不够

​		选择增大L，重新进行对W扫描（保证id大小不变）

![image-20231028141916272](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231028141916272.png)

​		可见gm/id偏小，增益增大，带宽减小了，但增益还是不够

​		选择增大W/L（即减小Vgs），重新进行对W扫描（保证id大小不变）

![image-20231028141749214](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231028141749214.png)

​		综上，经过调试，无法实现增益 > 90 且带宽 > 4.5GHz

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

​		对于第一点，我们知道，在固定的漏极电流情况下，**增大输出阻抗最主要的方式是增大管子的L**，在这里我们先认为至少**L2 > 3*L1**时，对直流增益影响较小。

​		而对于第二点，根据gm/id曲线可知，增大VGS可以降低跨导效率，即固定id情况下减小gm。

​		结合以上两点，**我们对负载管M2的参数要求是：较大的L，以及较大的VGS**。

> 并不是L以及VGS越大越好：
>
> 第一，**固定的VGS情况下，增大L会同比增大W，在面积显著增加的同时，会导致寄生电容显著增大**，过大的L会有破坏前文“忽略寄生电容”这一前提的风险，在这里我们**限定L2 < 10*L1**
>
> 第二，**固定的L情况下，增大VGS，事实上会降低运放的上摆幅，恶化线性度**，尽管在本次设计中没有考虑线性度，但同学们应该知道负载管的VGS也并非越大越好，在这里我们**限定VGS2<0.9V**。

​		负载管M2的初值选取为：**L2 =2.2um，VGS2=0.8V，再通过扫描W得到其宽度W2=56.5um**。

4. 负载管电路仿真&调整

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231022232056144.png" alt="image-20231022232056144" style="zoom: 80%;" />

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

###### 经验总结：

![image-20231029202127109](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231029202127109.png)

##### 使用HG_V0P4库实操：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231028150750129.png" alt="image-20231028150750129" style="zoom:50%;" />

1. 通过GBW=100MHz与CL=1pF，可以计算出此时的gm1=0.628mS，还有噪声的存在，这里保险起见，取gm1>0.7mS，即gm/id>7。参考单管的gm/id曲线，我们可以得到：VGS1<0.7V
2. 本征增益gm1ro1>42dB，参考单管的gmro曲线，结合上述的VGS1<0.7V，我们可以在这范围内任意选取一组参数（带宽要求太低，很容易满足，不用考虑），这里初值选取为VGS1=0.65V，L1=720nm。

![image-20231028151247684](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231028151247684.png)

​		通过扫描参数得到id = 100uA所对应的W，W1此时为9.95um。

![image-20231028151601557](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231028151601557.png)

![image-20231028151739506](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231028151739506.png)

​		图中显示，增益为145.9倍（=43.28dB），带宽符合设计指标。

3. 放大管电路的仿真：

![image-20231028154343136](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231028154343136.png)

![image-20231028154401513](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231028154401513.png)

​		得到的波特图：

![image-20231028154528918](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231028154528918.png)

通过对输入噪声的积分得到：

![image-20231028155056811](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231028155056811.png)

​		输入噪声功率为11.188uV，不符合指标。

​		噪声共包括热噪声（通过增大gm改善）和1/f噪声（增大面积改善），这里先选择增大gm改善，在id不变的条件下，增大gm等效于减小vgs

![image-20231028182434636](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231028182434636.png)

![image-20231028182457499](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231028182457499.png)

​		符合指标要求。

​		认为至少**L2 > 3*L1**时，对直流增益影响较小，故取L2 =2.2um，VGS2=0.8V，扫描后得W = 54.28u

![image-20231029184135747](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231029184135747.png)

![image-20231028195127747](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231028195127747.png)

![image-20231028195157367](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231028195157367.png)

​		此时的增益和带宽均符合指标要求，噪声功率大于指标要求。

​		选择增大gm改善，在id不变的条件下，增大gm等效于减小vgs。

![image-20231028204849200](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231028204849200.png)

​		只调整负载管，发现噪声功率一直降不下来，故返回去重新调整增益管

![image-20231028210416010](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231028210416010.png)

![image-20231028210439006](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231028210439006.png)

​		最终增益，带宽，噪声功耗均达到要求。

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

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231031155231827.png" alt="image-20231031155231827" style="zoom: 50%;" />

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

##### 使用HG_V0P4库实操：

- 先对第一级的几个管子进行仿真

![image-20231031135326257](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231031135326257.png)

参数如下：

|      |  L   |  W   | finger | mul  |
| :--: | :--: | :--: | :----: | :--: |
|  M0  |  1u  |  2u  |   1    |  4   |
|  M1  |  1u  |  2u  |   1    |  4   |
|  M3  | 360n |  2u  |   1    |  4   |
|  M4  | 360n |  2u  |   1    |  4   |
|  M5  |  1u  |  2u  |   1    |  50  |
|  M6  |  1u  |  2u  |   1    |  1   |

直流仿真结果如下：

![image-20231031151912729](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231031151912729.png)

​		通过参数对比，可见第一级中只有M5管没有饱和，要想管子饱和 V~ds~ > V~dsat~（可以选择增大 V~ds~或减小V~dsat~），先选择增大V~ds~，5管的V~s~已经确定为V~DD~，故只能降低V~d~，而5管的V~d~由输入管的V~gs~和输入决定，输入无法改变，只能减小输入管的V~gs~，输入管的电流不变，可以通过增大管子的尺寸来减小V~GS~（相同的输入V~GS~下，管子尺寸越大，可流过的电流越大），3、4管的mul增大一倍，结果如下

![image-20231031152009910](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231031152009910.png)

​		可见5管的V~DS~增大了，但还是不够饱和，导致电流Id还没有到达理论值。再选择减小5管的V~sdat~，即减小5管的V~GS~，同样的，电流不变增大尺寸即可。将5、6的宽度增大一倍（电流镜的管子尺寸变换要一起改变）

![image-20231031152047375](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231031152047375.png)

​		管子均饱和。

- 第二级的管子工作状态不好确定，很难达到两个管子的电流相等且两者均饱和的状态，故采用反馈的方式使之饱和。

![image-20231031152258801](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231031152258801.png)

![image-20231031152238110](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231031152238110.png)

​		管子均达到饱和。

- 使用gmid方法进行仿真

​		放大管参数：      <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231031171434892.png" alt="image-20231031171434892" style="zoom:67%;" />

​		mul = 4；

​		得到gds2 = 92u，gds1 = 3.14u；id1 = 85.7u，id2 = 719.4u

​		负载管参数：

# 五，LDO

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231029104825439.png" alt="image-20231029104825439" style="zoom: 67%;" />

#### 1，各个元件的作用：

- M0、M1：误差放大器的输入对管，用于将误差电压信号转换为电流；

- M3、M4：电流镜负载对，用于将上述的电流信号，转换为单端输出电压V1；

- M5：误差放大器的尾电流源；

- M2：功率管，用于输出负载电流，同时也是“二级运放的第二级放大管”；

- R1、R2：分压电阻，用于确定反馈系数，同时也是“二级运放的第二级负载”；
- Cc：密勒电容，用于分离极点，以补偿相位裕度；

- Rz：调零电阻，用于调整零点，以补偿相位裕度。

> 结构与二级运放类似：
>
> - 它不再是差分输入，而是只有一个输入端Vref，另一个输入端接了反馈电压Vfb；
> - 第二级本身的负载不再是一个MOS管，而是换为了R1与R2的电阻串联，同时它们也作为负反馈网络的电阻分压出现；
> - 整个放大器的负载不再是我们通常讨论的单纯电容，而是多出了一个负载电阻RL。
>
> 如果这个负反馈的环路增益足够高，那么我们就可以由类似于“虚短”的概念，得到：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231029105053417.png" alt="image-20231029105053417" style="zoom:67%;" />，<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231029105409002.png" alt="image-20231029105409002" style="zoom:67%;" />
>
> 可见输出电压只与Vref、R1、R2的值相关，而与输入电源电压VIN、负载阻抗以及任意其他设计参数均无关

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231029105604176.png" alt="image-20231029105604176" style="zoom:67%;" />

#### 2，LDO的指标

- 常态输入、输出电压

- 负载调整率（稳压器对输出负载有多么不敏感）

  ​	对于一个理想的电压源来说，无论其负载电流是多大、什么频率，其输出电压都应该为一个恒定值，即要求理想电压源的输出阻抗为0（理想电压源大小信号输出阻抗均为0）。

​		输出阻抗为0不现实，对于实际的LDO，输出负载电流变化，输出电压会变化。

​		负载调整率：                 <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231029110539698.png" alt="image-20231029110539698"  />

​		在小信号情况下，![image-20231029110812792](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231029110812792.png)，其中R~out~为小信号输出阻抗

​		所以事实上，LDO的小信号负载调整率直接等于其本身的输出阻抗

​		**通常使用tran仿真来确定跳变的负载，引入的Vout变化峰值，进而计算负载调整率。**

- 线性调整率（对输入电压Vin的敏感程度）

  ​	线性调整率：        ![image-20231029111706865](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231029111706865.png)

  ​	在小信号情况下，![image-20231029111748498](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231029111748498.png)，其中PSRR为电源抑制比

  ​	**通常使用tran仿真来确定跳变的输入，引入的Vout变化峰值，进而计算线性调整率。**

- 相位裕度

- 输出噪声电压

  ​	运放关注的是等效输入噪声，而LDO直接关注输出噪声电压。

- 输出电压精度

  ​	理想情况输出电压：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231029105409002.png" alt="image-20231029105409002" style="zoom:67%;" />

  ​	输出电压精度用实际输出电压与理想输出电压的差值表示。

目标指标：

![image-20231029112915396](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231029112915396.png)

> **如果忽略R1、R2的电流，也忽略EA本身的电流，那么流过PMOS功率管的电流与输出电流是一致的（即输入输出电流近似相等）；**
>
> 故LDO的效率 = Vout/Vin；
>
> 故LDO的功耗、效率，几乎只取决于输入输出电压，与输出电流的要求；
>
> 当然，LDO本身运放与分压电阻的功耗也不可以很大，至少不可以与输出电流的大小相比拟，故**要求运放电流+分压电阻电流<3mA**

静态电流仿真：跑个瞬态仿真，calculator里有VT，选中电源就好啦，记得是average函数

#### 3，功能实现

- 确定负载阻抗和反馈电阻大小

![image-20231029182643260](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231029182643260.png)

- DC工作点建立

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231029104825439.png" alt="image-20231029104825439" style="zoom: 67%;" />

###### 经验总结：

![image-20231029200830386](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231029200830386.png)

##### 使用HG_V0P4实操——DC工作点建立：

![image-20231101230356585](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231101230356585.png)

![image-20231101230423136](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231101230423136.png)

#### 4，LDO——负载调整率

​		在小信号的情况下，![image-20231029110812792](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231029110812792.png)，其中R~out~为小信号输出阻抗，故我们通过对输出阻抗的分析来调整LDO的负载调整率。

​		设计指标——低频负载调整率<30mV/A，100kHz处的负载调整率<50mV/A，且负载电流100mA，可得：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231029220208067.png" alt="image-20231029220208067" style="zoom: 80%;" />

输出阻抗示意图：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231029220635121.png" alt="image-20231029220635121" style="zoom: 67%;" />

> 虽然输出阻抗不包括负载，但由于负载会影响环路增益，而环路增益会影响输出阻抗，故在分析时不能直接丢掉负载，只分析LDO内部。

​		**LDO是一个电压-电压反馈的系统**，因为我们采样的是输出电压Vout，而反馈回的量为电压Vfb，故**LDO的输出阻抗应该约为开环输出阻抗/(1+环路增益LG)**，其中开环输出阻抗为M2的输出阻抗ro2并联R1+R2（其中ro2远小于R1+R2，故两者并联约等于ro2）

- 低频输出阻抗计算

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231029222643751.png" alt="image-20231029222643751" style="zoom: 50%;" />

![image-20231029230138756](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231029230138756.png)

- 高频输出阻抗计算

​		由于LDO的负载调整率越小越好（即输出阻抗越小越好），故环路增益在工作频率下需要很大（输出阻抗=开环输出阻抗/(1+环路增益LG)），即工作频率 << GBW（单位增益），在进行输出阻抗分析时可将其看作一个单极点的系统，故影响次极点的C~L~和用于零点补偿的R~Z~在分析时可忽略，大小为0。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231029230049851.png" alt="image-20231029230049851" style="zoom:50%;" />

![image-20231029230208988](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231029230208988.png)

![image-20231029230443131](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231029230443131.png)

- 输出阻抗仿真

##### 使用HG_V0P4实操——输出阻抗仿真（负载调整率）：

![image-20231102205430596](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231102205430596.png)

![image-20231102205504189](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231102205504189.png)

![image-20231102205547187](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231102205547187.png)

#### 5，LDO——线性调整率

- 定性分析：误差放大器的输入管选择为NMOS，负载管选择为PMOS是为了降低线性负载率

![image-20231102144126130](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231102144126130.png)

EA的输入管采用NMOS，是为了降低开环增益A，证明：

​		首先分析开环增益，将LDO开环：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231102144402806.png" alt="image-20231102144402806" style="zoom: 67%;" />

> 由于误差放大器的两个输入信号本身差距很小，为了便于分析，直接接入相同的电压Vref

对于**忽略沟长调制效应**的**低频**：![image-20231102144849555](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231102144849555.png)，为了得到更低的ΔVout，需要ΔVgs2越小越好，由于M2的源极接在输入电压上，故希望栅极电压可以与输入电压随动，来得到最小的ΔVgs2，**当EA的负载管为PMOS（即输入管为NMOS）时，其输出电压（也就是M2的栅电压)，正好与输入电压Vin随动，增益为1**，即ΔVgs2 = 0。

​		即在忽略沟长调制效应的低频情况下，ΔVout = 0，即输出电压不会因为输入电压的变化而变化，即线性调整率为0。

> 误差放大器因为在输入管栅电压相等时，M3与M4的电流必然相等，而**忽略沟长调制效应时**，M3与M4的Vgs必须为恒定值，才能保持其电流之和与尾电流大小一致，故误差放大器的输出电压（即M2的栅极电压）与Vin随动，进而在开环时，M2的Vgs恰好不随电源电压Vin变化

- 低频分析

  ​		实际上，由于沟长调制效应的存在，线性调整率不为0。

  导致LDO输出随着输入抖动的因素，在低频处有两个：

  ​		其一是，由于**ro2的存在**，输入电源可以直接通过ro2对Vout充电，导致Vout上升；

  ​		其二是，由于**M1、M5的cascode结构的输出阻抗不为无穷大**，因此当电源电压Vin变化时，EA的输出Vo1不会完全随动，进而导致M2的Vgs不为0，导致Vout变化。

  利用叠加定理将两个因素分开考虑：

  - 由ro2引入的PSRR降低

    在分析ro2引入的G时，我们认为M1、M5的输出阻抗为无穷大。

    <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231102151845830.png" alt="image-20231102151845830" style="zoom:80%;" />

    Vin1不会引入Vout的变化（上一小结分析结果），可将Vin1置零，此时的Vout来源于ro2与输出阻抗的分压，故线性调整率 = G1 = ![image-20231102152236606](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231102152236606.png)，其中![image-20231102152305173](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231102152305173.png)

  - 由ro1、ro5引入的PSRR降低

    此时认为ro2对PSRR的直接影响不存在

    <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231102152705989.png" alt="image-20231102152705989" style="zoom:67%;" />

    <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231102153108500.png" alt="image-20231102153108500" style="zoom:80%;" />，其中K与E分别为Vin与Vfb两个输入端口到输出的增益。

    E就是EA的低频增益Av1，而K则可以通过M3、M4的并联二极管连接，与M0、M1、M5的cascode结构分压，进行电阻分压得到，即<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231102153740280.png" alt="image-20231102153740280" style="zoom: 80%;" />（近似为1）

    ![image-20231102154859428](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231102154859428.png)

    显然，G2 远远小于 G1，即LDO的低频PSRR，完全取决于ro2的影响，故

    低频线性调整率 = <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231102155128483.png" alt="image-20231102155128483" style="zoom: 80%;" />

- 高频分析

> 注：（1）由于K近似为1，且对于输出的影响远远小于ro2，可忽略；（2）**忽略Rz、CL与其他寄生电容的影响**，工作频率远小于环路增益的GBW，因此，在我们关心PSRR的频率以内，我们可以将LDO的环路视为一个单极点系统，而决定各个次极点的电容，如CL与其他寄生电容，又或者是决定零点的电阻，如Rz，在本小节的分析中都会被忽略，即电容、电阻值为0；（3）将K与E关于频率的表达式，都视为**单极点传输函数**。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231102163733078.png" alt="image-20231102163733078" style="zoom: 33%;" />

![image-20231102172759981](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231102172759981.png)

> 1，两个式子是误差放大器的输入输出关系与R1节点的电流关系
>
> 2，高频处的E和K与低频时的不同，由于极点的存在，导致有（1+s/w）的倍数
>
> 3，其中w0就是极点A处的频率，由于此情况下的米勒电容Cc不符合米勒定理的使用情况，故极点A处的电容直接找对地电容，由于Vout保持不变，为交流地，故A点的对地电容直接为Cc即可
>
> 4，得到的高频G，将s = 0代入，即可得到低频G

​		当频率较高时，分子的实部可以被忽略，则可以写为：![image-20231102193803327](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231102193803327.png)，由于环路增益的GBW<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231102193831006.png" alt="image-20231102193831006" style="zoom:80%;" />，故![image-20231102193903494](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231102193903494.png)，可见高频处的线性调整率只取决于环路GBW的大小。

##### 使用HG_V0P4实操——线性调整率仿真：

![image-20231102213648278](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231102213648278.png)

![image-20231102213714646](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231102213714646.png)



#### 6，LDO——稳定性

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231105150241616.png" alt="image-20231105150241616" style="zoom:80%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231105150817390.png" alt="image-20231105150817390" style="zoom: 80%;" />

> 其中的![image-20231105150925536](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231105150925536.png)是给此极点留了25度的相位裕度

​		抛开主极点不谈，分析两个次极点与零点：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231105151027759.png" alt="image-20231105151027759" style="zoom:67%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231105151054004.png" alt="image-20231105151054004" style="zoom:80%;" />

##### 使用HG_V0P4实操——稳定性仿真：

![image-20231102221632833](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231102221632833.png)

​		相位裕度只有18°左右，太低。

提升相位裕度方式一：增大调零电阻（500Ω增大到2kΩ）

![image-20231102222023521](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231102222023521.png)

​		相位裕度达到了24°左右，从波特图中观察零点已经在GBW附近，再继续增大调零电阻的值改善效果不大，要想改善相位裕度，换一种方式。

提升相位裕度方式二：增大米勒电容Cc，减小GBW，从而改善相位裕度

![image-20231102223250982](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231102223250982.png)

​		相位裕度达到了48°，符合要求。

​		由于修改了米勒电容的大小，会对负载调整率和线性调整率有一定影响，需要再次仿真进行验证

![image-20231102224757007](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231102224757007.png)

​		负载调整率不符合要求（30m、50m），通过分析，可以选择增大gm1或gm2改善

![image-20231102225631117](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231102225631117.png)

​		有一些改善，还是不符合要求，只能选择再次增大gm1和gm2

![image-20231102230512194](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231102230512194.png)

​		负载调整率符合要求。

![image-20231102230742404](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231102230742404.png)

​		线性调整率符合要求。

![image-20231102230908427](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231102230908427.png)

​		此时的相位裕度大于45°，符合要求。

#### 7，完整仿真

1. 关于调零电阻的大小与零点位置：

   Rz = 50Ω时，负载电流为100mA

   ![image-20231104105204754](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231104105204754.png)

   Rz = 500Ω时，负载电流为100mA

   ![image-20231104105623162](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231104105623162.png)

   Rz = 600Ω时，负载电流为100mA

   ![image-20231104105947951](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231104105947951.png)

   Rz = 2000Ω时，负载电流为100mA

   ![image-20231104110500393](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231104110500393.png)

2. 不同负载条件下的频率响应比较：

   负载电流为1mA与100mA时的频率响应：

   ![image-20231104115158589](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231104115158589.png)

   ![image-20231104115643589](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231104115643589.png)

   **可见轻负载对应高增益、低频极点和更小的单位增益频率。**

3. 电压降

   Vin从2V到4.5V的电压降

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231104154025118.png" alt="image-20231104154025118"  />

​		Vin = 2V：电压差为180mV

![image-20231104161811019](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231104161811019.png)

​		Vin = 2.5V：电压差为110mV

![image-20231104161349131](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231104161349131.png)

​		Vin = 3V：电压差为200mV

![image-20231104161227557](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231104161227557.png)

​		Vin = 3.5V：电压差为110mV

![image-20231104160915877](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231104160915877.png)

4. 负载调整率

   负载电流从1mA变化至100mA，得到的输出电压变化6mV，负载调整率为60mV/A

![image-20231104170552068](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231104170552068.png)

5. 线性调整率

   Vin从2V增大至4.5V，负载电流为100mA时，线性调整率为0.48mV/V

![image-20231104180303256](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231104180303256.png)

6. 瞬态响应

   Vin在50us内从0增大到2.3V，负载从轻负载（1800Ω——1mA）切换至重负载（18Ω——100mA）再反向切换。

![image-20231105151335646](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231105151335646.png)

![image-20231105140817073](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231105140817073.png)

![image-20231105141854347](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231105141854347.png)

​		Vin从0突变到2V，再从2V突变到4V，随后又突变降低

![image-20231108093205914](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231108093205914.png)

![image-20231108093811529](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231108093811529.png)

![image-20231108093856960](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231108093856960.png)

#### 8，LDO发展趋势

> [LDO专利技术现状及其发展趋势 - 道客巴巴 (doc88.com)](https://www.doc88.com/p-7794493377358.html)

1. 无片外电容

   传统的LDO芯片中，在芯片输出端需要添加片外电容来抑制输出过冲电压，并起到稳定LDO的输出电压具有低噪声、低纹波、无电磁干扰的特性，在大量芯片中都用作一个内部模块为后续噪声敏感电路提供稳定而低噪的工作电压。

   片外电容浪费芯片面积，增加额外开销，系统成本显著上升。

   无片外电容LDO中，**环路稳定性成为设计的一个重点**。此外，传统LDO中，片外电容是一个重要的电荷储存和提供器件，可以有效的减小由于负载电流瞬态变化引起的输出电压的跌落和过冲，对于无电容型LDO，负载的瞬态变化必须依靠调整管的快速响应。由于调整管的栅极寄生电容巨大，导致环路的压摆率不够，无电容LDO比传统LDO 的瞬态响应特性差，故**提高LDO瞬态响应速度是LDO设计的另一重点**。

2. 高电源噪声抑制

   电源上的杂波作为噪声的一种,影响着模数/数模转换器的性能，因此如何在更高频段内抑制电源噪声,成为为模数/数模转换器供电的LDO芯片一个主要研究热点。

   在提高LDO电路的电源噪声抑制比的方法中,通过**增加低压差线性稳压器在高频时的环路增益以提高LDO的电源抑制比属于常见的方法之一**，同时,近年来,通过改变电路参数设置从而**使得到达驱动管栅极的电源干扰信号更好地跟随电源电压变化而变化从而提高LDO的电源抑制比**属于主流趋势。

3. 新型频率补偿

   无片外负载电容和高电源噪声抑制成为目前DO研究的两个热点,它们显著改变了LDO芯片的外部电路和零极点分布因此运用传统LDO设计的频率补偿方案,例如米勒电容补偿、片外负载电容寄生串联电阻(ESR)补偿都不再适用于目前的热点LDO结构。因此**需要新型的频率补偿方案以满足在无片外负载电容和高电源噪声抑制前提下LDO环路的稳定性。**

   频率补偿方案的本质是控制LDO环路中零一极点的分布,从而达到闭环系统稳定的目的。传统的LDO的整个回路中主要存在两个极点第一个极点是由误差放大器与传输元件间寄生电容和误差放大器的输出阻抗所形成第二个极点则是由输出电容及LDO的输出阻抗所造成,可见第二极点的频率会随着负载电流变化而变化然而极点频率漂移会大幅地改变LDO的频率响应,在某些情况下可能发生回路不稳定。

   为了消除LDO电路中第二极点的位置随着负载变化所带来的影响,传统的做法是在误差放大器的输出端与传输元件之间使用缓冲器以提高第一极点,从而使得作为次极点的第一极点远离作为主极点的第二极点然而这样做需要很大的电流来驱动缓冲器,引起高功耗针对上述问题,目前提出了在低压差线性稳压器引人**自适应频率补偿技术,即次极点位置根据主极点的变化而相应变化在主极点位置较低时,只需要较低的电流便可以实现保证次极点大于单位增益频率,而在输出大电流即负载较低时对缓冲器注入额外电流使得次极点与主极点以相同的速度增加,继续保证环路的稳定性。**

   除了对LDO的极点进行追踪在本技术分支的核心专利中还提出了在电路中引入附加零点以抵消电路中的非主极点频率,从而获得在单位增益中只存在主极点的情况,从而获得系统稳定性。

4. 优化瞬态响应

   当LDO负载电流或供电电压跳变时，会造成LDO输出电压的变化，随后LDO芯片通过自身的线性负反馈系统使得输出电压重新回到稳定值，这一响应过程称为瞬态响应。在LDO瞬变响应中有两个重要指标，过冲电压和恢复时间。前者决定了LDO输出电压的最大变化，对于某些数字电路而言,当供电电压大于标准电压的10%时会造成MOS管的击穿，从而使得芯片失效；后者决定了LDO输出电压重新恢复到稳定值所需要的时间。LDO的瞬态响应不仅由LDO环路的小信号特性决定，还涉及LDO环路中各级放大器对其负载电容进行充放电所造成的大信号响应。因此**如何协调误差放大器中带宽摆率以及功耗之间的关系，添加辅助电路以改善大信号响应都成为目前LDO研究的一个热点**。基于传统的低压差线性稳压器依靠电阻按比例采样输出电压,采用电压型反馈与运算限制了环路的瞬态响应性能与控制精度的问题，在现有技术中，已经提出了在电流控制型的低压降稳压电路的电流型环路控制技术，使用有源电压缓冲器直接采用输出电压,利用跨导放大器产生控制电流,并经过积分滤波器产生功率晶体管的控制电压信号,从而有效提高环路的响应速度和控制精度；在现有技术中还通过提高调整管驱动级的摆率的方法改善低压差线性稳压器的瞬态性能。

   

# 底部

