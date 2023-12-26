|   输入电压   | 2.5V  |   负载调整率@1kHz   | 30mV/A |
| :----------: | :---: | :-----------------: | :----: |
|   输出电压   | 1.8V  |  负载调整率@100kHz  | 50mV/A |
|   参考电压   | 0.9V  |   线性调整率@1kHz   | 2mV/V  |
|   负载电流   | 10mA  |  线性调整率@100kHz  | 30mV/V |
|   负载电容   |  1uF  |  输出噪声电压@1kHz  |  25nV  |
|   静态电流   | 500nA | 输出噪声电压@100kHz |  10nV  |
| 输出电压精度 |  ±1%  |      相位裕度       |  45°   |

==能量采集电路通常从环境中获取能量，如太阳能、热能、振动或射频能量。这些能量来源通常是间歇性的、功率水平低且不稳定的。因此，在能量采集电路的应用中使用LDO时，需要满足以下工作条件和特点：==

1. **低静态功耗**：
   由于能量来源可能非常有限，LDO需要有非常低的静态电流消耗，以最小化系统的整体功耗。

2. **低压差（Low Dropout）**：
   为了最大化能量的使用效率，LDO应能在非常小的输入和输出电压差下正常工作。

3. **宽输入电压范围**：
   能量采集系统的输出电压可能随着能量源的变化而波动，LDO需要能够处理这种电压的变化，维持稳定的输出。

4. **高转换效率**：
   LDO需要具备高的转换效率，尤其是在负载电流变化时，以减少能量的损失。

5. **快速瞬态响应**：
   当能量源突然变化时，LDO需要快速响应负载的变化，以保持输出稳定。

6. **低输出噪声**：
   一些能量采集应用，如传感器网络，可能对电源噪声敏感，因此LDO需要有低输出噪声特性。

7. **良好的温度稳定性**：
   能量采集设备常常暴露在变化的环境条件下，因此LDO需要在广泛的温度范围内提供稳定的输出。

8. **最小的外部组件需求**：
   为了减少设计的复杂性和成本，理想的LDO应该尽量减少对外部组件（如电容）的需求。

9. **启动特性**：
   在能量很低时，LDO应该有良好的启动特性，以便能够在能量源刚开始提供能量时迅速启动。

在设计和选择适合能量采集应用的LDO时，上述条件和特点是非常关键的考虑因素。开发者需要权衡这些特点，并选择或设计符合具体应用要求的LDO解决方案。

## FVF-LDO的核心结构：

![image-20231123143454978](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231123143454978.png)

​		MC1和MC2形成折叠共源共栅放大器，其用作误差放大器（EA）。由于FVF是单端结构，对于类似的动态响应，与传统差分EA[14]相比，基于FVF的LDO仅花费约50%的电流。因此，基于FVF的LDO优选用于物联网等低功耗应用。另一方面，应改进基于FVF的LDO的控制电压V~BIAS~调节，以获得更高的精度。

1，折叠共源共栅放大器学习：

​		[电子技术——共源共栅放大器-CSDN博客](https://blog.csdn.net/jiahonghao2002/article/details/128951923)

> 对于共源共栅的分析挺好的，通俗易懂

![image-20231123184733548](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231123184733548.png)

![image-20231124095903667](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231124095903667.png)

![image-20231128170550848](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231128170550848.png)

![image-20231126004151620](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231126004151620.png)

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231126004213102.png" alt="image-20231126004213102"  />

### 负载瞬态响应：

![image-20231128170318765](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231128170318765.png)

![image-20231128170337011](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231128170337011.png)

![image-20231128170606187](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231128170606187.png)

#### 问题：

​		（1）下冲电压幅值太大：针对此问题论文提出了LDO2电路；

​		（2）过冲电压太大（100mV左右）且恢复时间太长（50us）：我的想法在输出端增加一个辅助放电的支路，当输出电压高于820mV时可以导通放电，使输出电压更快恢复

​		（3）动态偏置电流不断的波动：由于三个管的串联匹配性不好，导致电流的波动，需要更换其他结构使用低阈值电压实现高阈值电压的效果。

### 稳定性：

输出负载电流为10mA，1mA，100uA，10uA，1uA，100nA条件下的环路增益与相位裕度曲线仿真结果：

![image-20231130164026116](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231130164026116.png)

可见当输出负载电流为10mA时的相位裕度为84.7°，当输出负载电流为100nA时的相位裕度为50.9°。

> 关于图中相位起始点不同的问题：
>
> [相位欲度曲线从0开始？ - 第2页 - Analog/RF IC 设计讨论 - EETOP 创芯网论坛 (原名：电子顶级开发网) -](https://bbs.eetop.cn/thread-870262-2-1.html)
>
> ![image-20231130182537458](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231130182537458.png)

#### 问题：

​		相位裕度足够，就是增益比较低，论文中在负载电流为100nA时最低为31dB，我的最低为20dB。

### 负载电流不同变化时间下上冲电压与下冲电压：

![image-20231130170419189](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231130170419189.png)

下冲电压为740mV，过冲电压为200mV。

![image-20231130170736459](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231130170736459.png)

下冲电压为800多mV，过冲电压为200mV。

![image-20231130170924918](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231130170924918.png)

下冲电压为760多mV，过冲电压为200mV。

#### 问题：

​		下冲电压幅度太大，论文的LDO2电路提出的结构可以改善。

### 电压降：

#### 问题：

​		由于我的动态偏置管直接连接在了Vin上，故Vin增大后动态偏置管直接导通导致偏置电流太大，功率管直接截止，导致输出异常。

为了解决这个问题，我尝试将动态偏置管直接接在参考电压之上，由于参考电压稳定不变，大大减小Vin对于动态偏置管的工作状态的影响。

![image-20231130234329614](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231130234329614.png)

> 主要改动就是将动态偏置管的源极接在0.8V的参考电压之上

得到结果：

![image-20231130234534493](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231130234534493.png)

对比改动之前：无需高阈值电压管，产生的动态偏置电流没有了波动

输入从0到3V时（负载电流为10mA）的输出曲线：

![image-20231201150452146](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231201150452146.png)

输出只有在1V至1.5V范围内为800mV左右正常输出。

输入电压范围太小，没有得到改善，原因出在自适应偏置的管子，Vin增大，自适应偏置的管子电流增大导致输出电压增大。

想法：将电流镜和自适应偏置管的尺寸减小，控制住流过的电流，从而获得一个更宽的输入范围

![image-20231201154717852](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231201154717852.png)

没有得到太大的改善。

突然发现一个问题：

![image-20231201163742753](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231201163742753.png)

上面两个是自适应偏置管和动态偏置管的电流，最下面的电流应该是两股电流之和，如下图所示：

![image-20231201163908840](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231201163908840.png)

可看出总的偏置电流不正确。

经过排查，发现是总偏置电流的测量位置错了，在正确位置测得电流

![image-20231201165140334](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231201165140334.png)

与理论值相符。





### LDO2电路复现仿真：

![image-20231208163030255](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231208163030255.png)

​		相较于LDO1电路，LDO2增加了一个IDU（基于反相器的动态单元），用于控制动态偏置管的工作，并通过M16管对Vout实现快速补偿

​		IDU结构如下：![image-20231203014850719](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231203014850719.png)

​		是一个两级反相器构成的模块，第一级反相器的输入为Vout，跳变点为Vout，第二反相器充当放大器，在VA上产生尖锐边缘。其次，在稳态下，IDU充当开关，完全关闭MD，以进一步降低静态功耗。

![image-20231203015059358](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231203015059358.png)

​		首先仿真调整第一级反相器，设置跳变点接近Vout，即当Vout低于800mV时，第一级反相器输出高电平（VDD）

> 这里只关心输出电压下冲的情况，因为只有下冲的时候会打开动态偏置管进行偏置电流的动态补偿

调整结果：

![image-20231203015346494](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231203015346494.png)

![image-20231203021903481](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231203021903481.png)

​		可看到，当输入Vout开始低于跳变点电压800mV，第一级反相器可以在0.5us内使得输出电压至1V

​		其次，调整第二级反相器，由于方向相反，故第二级反相器主要关注当输入电压大于跳变点的区域

![image-20231203022410795](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231203022410795.png)



LDO2仿真结果：

![image-20231205182451964](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231205182451964.png)

动态补偿管M~16~对于下冲电压的改善：

![image-20231208163205662](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231208163205662.png)

![image-20231208163258343](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231208163258343.png)



### 阶段总结：

目前只是对两个电路进行了直流仿真与瞬态仿真，根据仿真观察得到的结果发现：

​		论文提出的电路与方法，由于动态偏置管的作用，改善了电路的瞬态响应（特别是下冲响应），但也正是由于此动态偏置管的主要原因，电路对于输入电压的依赖程度较高，导致此电路的PSR（电源抑制）太低，工作输入电压范围太小；

​		并且为了节省功耗，就要保证动态偏置的管子在输出电压稳定的时候保持截止的状态，这就需要管子是一个高阈值电压的管子；

​		电路的动态偏置管子对下冲电压的恢复时间改善较大，对于过冲电压的改善不大；

​		LDO2电路通过在输出端连接一个动态补偿管子对下冲电压进行补偿，以此改善下冲电压幅度，对于下冲电压的摆幅确有改善，电路确实一个对于过冲电压幅度改善的部分。



阅读论文《一种无片外电容高瞬态响应LDO设计》笔记：

​		文章提出了一种电压峰值检测的动态偏置电路，但结构较复杂，功耗较大。

​		此文章中对于FVF结构的LDO的瞬态响应分析部分较好，总结记录如下：

![image-20231208150517615](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231208150517615.png)

​		综上：要改善瞬态响应的过冲电压恢复时间就要增大I~B1~，要改善瞬态响应的下冲电压恢复时间就要增大I~B2~，同时减小I~B1~；

​		利用LDO1电路直接测试，验证此结论的正确性，验证结果如下：

增大I~B1~对于过冲电压的影响：

![image-20231208161007367](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231208161007367.png)

可见增大I~B1~对于过冲电压的恢复时间确有改善，但对于下冲电压的恢复时间略有影响；

增大I~B2~对于下冲电压的影响：

![image-20231208155948895](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231208155948895.png)

![image-20231208160415774](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231208160415774.png)

可见增大I~B2~确实可以加快下冲电压的恢复时间，但对于下冲电压的幅度改善不太明显；

当我增大I~B1~后再增大I~B2~：

![image-20231208161831782](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231208161831782.png)

对比可得I~B2~在增加相同的情况下，I~B1~的减小有助于下冲电压恢复时间的减少。

根据结果验证可知要改善瞬态响应的过冲电压恢复时间就要增大I~B1~，要改善瞬态响应的下冲电压恢复时间就要增大I~B2~，同时减小I~B1~；

#### 打算从I~B1~和I~B2入手，对于瞬态响应进行改善。

​		目标：将电路中的动态偏置管进行替换

针对下冲电压：使用一级反相器和一个NMOS动态偏置管对I~B2~进行补充

![image-20231212163657075](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231212163657075.png)

输出电压（上）和一级反相器输出电压（下）对比：

![image-20231212163329639](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231212163329639.png)

电路增加I~B2~电流补充部分前（上）和后（下）：

![image-20231212162923613](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231212162923613.png)

![image-20231212163048034](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231212163048034.png)

可见，对于下冲电压恢复时间确有改善









### 理论分析计算：

#### 系统零极点计算：

![image-20231212102205703](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231212102205703.png)

​		从V~OUT~点断环：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231212102143211.png" alt="image-20231212102143211" style="zoom:80%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231212102258392.png" alt="image-20231212102258392" style="zoom: 50%;" />

![image-20231212102412231](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231212102412231.png)

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231212102432110.png" alt="image-20231212102432110" style="zoom:80%;" />

![image-20231212102500134](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231212102500134.png)

![image-20231212102525678](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231212102525678.png)

![image-20231212151642533](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231212151642533.png)

#### 电源抑制比分析：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231212150214139.png" alt="image-20231212150214139" style="zoom:80%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231212150247462.png" alt="image-20231212150247462" style="zoom:80%;" />







### 针对无片外电容的瞬态响应部分：

#### 《LDO瞬态提升技术研究与芯片设计》

​		对于缺少大电容辅助功能的 capless LDO，主要通过==提高环路带宽和压摆率来提高瞬态响应==。

​		FVF结构：这种 LDO 仅使用一个折叠式共源共栅负反馈回路，结构简单，可以快速对输出端的变化进行响应。可以有效减少恢复时间和瞬态峰值。而且简单的环路可以降低系统功耗，不需要额外设计随负载改变功耗的结构，系统在整个负载范围内都可以保持较低的静态电流。但是这种结构也存在一些缺点，==反馈回路很短导致环路增益不够，输出精度太低==，许多设计者在这种新型基础结构上做出了很多改进结构。

​		过冲电压和下冲电压幅度主要由带宽和压摆率这两个主要因素限制。其中带宽根据![image-20231215091850559](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231215091850559.png)计算结果可知在漏极电流一定的条件下，可通过增大第一级的跨导和减小米勒补偿电容的大小进行改善；而功率管==栅极压摆率的改善==有两种常用方式，一种是在**误差放大器的输出端加一级高压摆率输出**，利用第二级快速改变功率管的栅极电压；第二种方法是对误差放大器进行改进，大致结构如图所示，**放大器使用 push-pull(推挽式)共栅极输入**，输入端产生细微的电压变化，其输出端可以产生较大输出电流，快速改变功率管的栅极电压。

![image-20231215092407496](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231215092407496.png)

1. 通过提升系统的环路增益对带宽进行改善

测量系统环路增益为20dB左右，太低（一般需要60dB以上），根据环路增益公式可知可以通过增大第一级电路（折叠共源共栅）和第二级电路（功率管）的本征增益来改善环路增益。

![image-20231214214559258](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231214214559258.png)

故先选择通过增大FVF中的折叠cascode的增益来改善环路增益

折叠cascode的增益 = g~m1~g~m2~r~o1~r~o2~，故要增大增益管和负载管的本征增益

![image-20231214214810452](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231214214810452.png)

由公式可知：当漏极电流不变，增大W/L且L不变或者W/L不变且L增大都可以增大管子的本征增益

需要保持电流不变，修改管子的宽长比，经过改善，环路增益与相位裕度：

首先增大增益管的宽长比，L设为540n不变，增大W（从10u增加到50u）

![image-20231215095537406](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231215095537406.png)

随着管子的W/L增大，增益确实有所增大，但增大的不多，宽度为50u时，环路增益才29dB，带宽12.5MHz，相位裕度均在80度以上。最后选择L=540n，W=30u

增大负载管的宽长比，L设为1u不变，增大W（从10u增加到50u）

![image-20231215100415088](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231215100415088.png)

可见负载管的宽长比的增大对于环路增益的改善不大。

再通过增大功率管的宽长比进行改善：

![image-20231215101310091](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231215101310091.png)

低频环路增益为32.8dB，GBW为14MHz，相位裕度为83度

![image-20231214213518726](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231214213518726.png)

![image-20231214220300336](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231214220300336.png)

![image-20231214220327038](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231214220327038.png)

![image-20231214220407573](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231214220407573.png)

可以看到过冲电压和下冲电压的幅度和恢复时间随着环路增益的提升确实得到了改善，由于工作电流太小了（30多uA），环路增益无法达到更大的值，故单独一个折叠型cascode不太够啊。

考虑通过改善功率管压摆率改善瞬态响应

![image-20231215101758460](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231215101758460.png)

上述论文中提到的可以在 FVF 功率管前加一级 push-pull(推挽式)结构，该级可以提高增益，弥补环路简单增益不足的缺陷。Push-pull 结构配合 class-AB 结构提升栅极压摆率，改善瞬态响应。

![image-20231215182226291](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231215182226291.png)

![image-20231215182247509](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231215182247509.png)

![image-20231216114956556](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231216114956556.png)



负载调整率：

​		负载电流从1mA变化至10mA，得到的输出电压变化0.726mV，负载调整率为80.7mV/A

![image-20231218014301980](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231218014301980.png)
