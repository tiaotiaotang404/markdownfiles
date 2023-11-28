## 第2章 MOS器件物理基础

​		本章目的：通过对器件工作状态的解析描述来为每个器件建立电路模型

### 2.1 MOS晶体管的结构

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230728152238973.png" alt="image-20230728152238973" style="zoom: 50%;" />

​		栅沿源漏通道的横向尺寸叫**栅长L**，与之垂直方向的栅的尺寸叫做**栅宽W**，L<sub>eff</sub>为**有效栅长**。

​		L<sub>eff</sub>和氧化层厚度t<sub>OX</sub>对MOS电路的性能起着重要作用，MOS技术发展主要推动力就是不使器件的其他参数退化而一代一代地减小这两个尺寸。

​		实质上，MOSFET是一个四端器件。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230728153218741.png" alt="image-20230728153218741" style="zoom: 33%;" />

 		 MOS符号如下：

![image-20230728153337603](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230728153337603.png)

​		其中（b）更常用。

### 2.2 I/V特性

![image-20230729095014968](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230729095014968.png)

​		V<sub>G</sub>从0开始增大，p衬底的空穴被赶离栅区，只留下了负电荷形成**耗尽层**；随着V<sub>G</sub>继续增大，负电荷不够了，吸引了电子到源漏之间的栅氧下，形成了载流子“沟道”，称为**“反型”**。

​		开始形成载流子“沟道”所对应的V<sub>G</sub>称为**“阈值电压”，V<sub>TH</sub>**。

​		在器件制造过程中通过向沟道区注入杂质来调整阈值电压，实质是改变氧化层界面附近衬底的掺杂浓度。

> [(29条消息) 集成电路基础知识-器件-MOS结构&VI特性_耗尽层和反型层的区别_powerwaves的博客-CSDN博客](https://blog.csdn.net/qq_38588825/article/details/105903385)

- 线性区

​		漏极电流大小：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230729102919271.png" alt="image-20230729102919271" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230729102952269.png" alt="image-20230729102952269" style="zoom:50%;" />

​		可得每条抛物线的极值发生在V<sub>DS </sub>= V<sub>GS</sub>-V<sub>TH</sub>,且峰值电流为

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230729103313003.png" alt="image-20230729103313003" style="zoom:33%;" />

​		其中V<sub>GS</sub>-V<sub>TH</sub>称为**“过驱动电压”**

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230807230002387.png" alt="image-20230807230002387" style="zoom:50%;" />

​		当**V<sub>DS</sub> << 2(V<sub>GS</sub>-V<sub>TH</sub>)**，可得

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230729103804082.png" alt="image-20230729103804082" style="zoom: 33%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230729104152613.png" alt="image-20230729104152613" style="zoom:33%;" />

​		此时器件工作在**深三极管区**，MOSFET可看作一个**线性压控可变电阻**，电阻值为

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230729104049857.png" alt="image-20230729104049857" style="zoom:33%;" />

- 饱和区

​		当**V<sub>DS </sub> > V<sub>GS</sub>-V<sub>TH</sub>**时，I<sub>D</sub>相对恒定。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230729144551892.png" alt="image-20230729144551892" style="zoom:50%;" />

​		如果**V<sub>DS</sub> 略大于V<sub>GS</sub>-V<sub>TH</sub>**，则反型层将在x ≤ L处终止，称为沟道被夹断。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230729144841457.png" alt="image-20230729144841457" style="zoom: 50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230729144948228.png" alt="image-20230729144948228" style="zoom:50%;" />

#### I/V特性总结

> ==总结：==
>
> 1，对于MOS管，由于是对称结构，故源极和漏极可以互换；对于NMOS来说谁的电压低谁就是源极，对于PMOS来说谁的电压高谁就是源极。
>
> 2，三个工作区的条件：
>
> <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230729145809520.png" alt="image-20230729145809520" style="zoom: 33%;" />
>
> V<sub>GS</sub> < V<sub>TH</sub>时：工作于截止区，I<sub>D</sub> = 0；
>
> V<sub>GS</sub> > V<sub>TH</sub>时：V<sub>DS </sub> < V<sub>GS</sub>-V<sub>TH</sub>对应线性区，I<sub>D</sub> = <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230801170125780.png" alt="image-20230801170125780" style="zoom: 67%;" /> ；
>
> ​						V<sub>DS </sub> > V<sub>GS</sub>-V<sub>TH</sub>对应饱和区，I<sub>D</sub> = <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230801084632573.png" alt="image-20230801084632573" style="zoom: 50%;" />；
>
> 工作在饱和区所需的最小的V<sub>DS</sub>也称为V<sub>D,sat</sub>，V<sub>D,sat</sub> = V<sub>GS</sub>-V<sub>TH</sub>
>
> 3，对于NMOS：固定V<sub>DS</sub>的值，随着V<sub>G</sub>的增大，管子先进入饱和区，随后进入线性区；
>
> ​							 固定V<sub>G</sub>的值，随着V<sub>DS</sub>的增大，管子先进入线性区，随后进入饱和区；
>
> <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230828105406424.png" alt="image-20230828105406424" style="zoom:50%;" />
>
> <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230919214542780.png" alt="image-20230919214542780" style="zoom: 80%;" />

- MOSFET的跨导

​		跨导 = 漏电流的变化量 ➗ 栅源电压的变化量（通常定义在饱和区）

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230729152206131.png" alt="image-20230729152206131" style="zoom: 33%;" />

​		g<sub>m</sub>单位是1/Ω 或西门子（S）。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230809194440094.png" alt="image-20230809194440094" style="zoom:50%;" />

​		饱和区的g<sub>m</sub>值等于深三极管区R<sub>on</sub>的倒数。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230729152440090.png" alt="image-20230729152440090" style="zoom:33%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230809194402906.png" alt="image-20230809194402906" style="zoom: 50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230809194503256.png" alt="image-20230809194503256" style="zoom:50%;" />

#### 跨导总结

> ==总结：==跨导记住这三个公式和图

### 2.3 二级效应

- 体效应：MOS管的阈值电压将随其源极和衬底之间电位的不同而发生变化

​		**随着V<sub>B</sub>的下降，Q<sub>d</sub>增加，V<sub>TH</sub>也增加**。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230729155436343.png" alt="image-20230729155436343" style="zoom:50%;" />

​		在考虑体效应后，

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230729155617269.png" alt="image-20230729155617269" style="zoom: 33%;" />

​		其中<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230729155741035.png" alt="image-20230729155741035" style="zoom:25%;" />称为体效应系数，V<sub>SB</sub>是源衬电势差。γ的典型值在0.3V<sup>1/2</sup>到0.4V<sup>1/2</sup>之间。

​		产生体效应，并不需要改变衬底电势V<sub>sub</sub>：源电压相对于V<sub>sub</sub>发生改变，会产生同样的现象（即**V~BS~改变就会导致V~TH~变化**）。

例如：

​		图中电路V<sub>out</sub> = V<sub>in</sub> - V<sub>GS</sub>

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230729161245558.png" alt="image-20230729161245558" style="zoom: 33%;" />

> 体效应的存在会导致阈值电压的改变

- 沟道长度调制

​		沟道长度调制效应是指MOS晶体管中，栅下沟道预夹断后、若继续增大Vds，夹断点会略向源极方向移动。导致夹断点到源极之间的沟道长度略有减小，有效沟道电阻也就略有减小，从而使更多电子自源极漂移到夹断点，导致在耗尽区漂移电子增多，使Id增大的效应。

​		**此效应发生在饱和区**，沟道长度L`是V<sub>DS</sub>的函数（从式2.13可得）。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230729161328814.png" alt="image-20230729161328814" style="zoom:33%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230902095044695.png" alt="image-20230902095044695" style="zoom:50%;" />

​		其中：  <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230809200907639.png" alt="image-20230809200907639" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230902095132901.png" alt="image-20230902095132901" style="zoom:50%;" />

> 沟道长度调制的存在导致I<sub>DS</sub>/V<sub>DS</sub>特性曲线在饱和区出现非零斜率，使D和S之间的电流源非理想

> 沟道长度加倍，会使I<sub>D</sub>~V<sub>DS</sub>曲线的斜率减为原来的1/2
>
> 即沟道长度越长，沟道长度调制效应越好，输出越理想

- 亚阈值导电性

​		V<sub>GS</sub> ≈ V<sub>TH</sub>时，器件不会突然关断，一个“弱”的反型层仍然存在，甚至当V<sub>GS</sub> < V<sub>TH</sub>时，I<sub>D</sub>也并非无限小，而是与V<sub>GS</sub>呈指数关系。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730090545296.png" alt="image-20230730090545296" style="zoom:50%;" />

##### 二级效应总结：

> ==二级效应总结：当MOS管的V~DS~变化时，需要考虑沟道长度调制效应；当MOS管的V~BS~变化时，需要考虑体效应。==

### 2.4 小信号模型

​		小信号模型就是MOS管的线性模型。

#### 2.4.1 MOS器件版图

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730091400780.png" alt="image-20230730091400780" style="zoom:50%;" />

例如：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730091509154.png" alt="image-20230730091509154" style="zoom:50%;" />

#### 2.4.2 MOS器件电容

​		考虑器件电容以便于预测器件的高频特性。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730091757956.png" alt="image-20230730091757956" style="zoom: 33%;" />

- 四个电容值计算：

![image-20230730092026998](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730092026998.png)

​		（1）栅和沟道之间的氧化层电容C<sub>1</sub> = WLC<sub>OX</sub>

​		（2）衬底和沟道之间的耗尽层电容C<sub>2</sub> = <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730092311801.png" alt="image-20230730092311801" style="zoom: 50%;" />

​		（3）多晶硅栅与源和漏的覆盖而产生的电容C<sub>3</sub>和C<sub>4</sub>。每单位宽度的覆盖电容用C<sub>OV</sub>表示，单位F/m。栅源和栅漏覆盖电容等于C<sub>OV</sub>W。

​		（4）源/漏区与衬底之间的结电容。**用C<sub>j</sub>和C<sub>jsw</sub>分别表示单位面积的电容（F/m<sup>2</sup>）和单位长度的电容（F/m）**。<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730093026401.png" alt="image-20230730093026401" style="zoom: 33%;" /><img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730093051779.png" alt="image-20230730093051779" style="zoom:33%;" />，式中V<sub>R</sub>是结的反向电压，Φ<sub>B</sub>是结的内建电势，幂指数m的值一般在0.3到0.4之间。

- 不同工作区域的MOSFET的各端子之间的电容：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730102839441.png" alt="image-20230730102839441" style="zoom: 33%;" />

#### 2.4.3 MOS小信号模型

​		得到小信号模型的步骤：

1. 给器件的各个端子施加一个偏置电压
2. 在两个端子之间产生一个电压增量而其他端子的电压保持不变
3. 测量所有端子电流的变化

​                                         <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730110228509.png" alt="image-20230730110228509" style="zoom: 50%;" />                                                       

​		输出电阻r~o~：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230902101028695.png" alt="image-20230902101028695" style="zoom: 67%;" /><img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230902101040958.png" alt="image-20230902101040958" style="zoom: 80%;" />

​		体跨导：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230902101414744.png" alt="image-20230902101414744" style="zoom:50%;" />

![image-20230913102559319](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230913102559319.png)

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730111126083.png" alt="image-20230730111126083" style="zoom:33%;" />

> ![image-20231120205705567](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231120205705567.png)
>
> ①管源级电压高于栅极电压，MOS管才导通，②源级电压高于漏极电压，③电流从源级流向漏极。

### 2.5 SPICE模型

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230801085344954.png" alt="image-20230801085344954" style="zoom:50%;" />

​		一级MOS SPICE模型参数定义：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730111906638.png" alt="image-20230730111906638" style="zoom: 50%;" />

## 第3章 单极放大器

​		本章目的：研究CMOS单极放大器的低频特性

> ​	三步曲：（1）DC偏置（2）小信号增益（3）输入输出电阻

### 3.3 共源极

#### 3.3.1 采用电阻作负载的共源极

![image-20230906100624223](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230906100624223.png)

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230811140633928.png" alt="image-20230811140633928" style="zoom: 33%;" />

​		M1将输入电压的变化△V<sub>in</sub>转换为漏极电流的变化g<sub>m</sub>△V<sub>in</sub>，进一步转换为输出电压的变化 -g<sub>m</sub>R<sub>D</sub>△V<sub>in</sub>。

​		为了使电压增益达到最大，我们必须使（小信号）负载阻抗最大。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230811142114517.png" alt="image-20230811142114517" style="zoom:50%;" />

​		随着输入电压的不断增大，MOS管先进入饱和区，再进入线性区；输出的漏极电流I<sub>D</sub>不断增大，而跨导在饱和区时不断线性增大至最大值<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230811142531443.png" alt="image-20230811142531443" style="zoom:25%;" />，随后进入线性区后开始减小<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230811142601530.png" alt="image-20230811142601530" style="zoom:25%;" />，即**在线性区随着输入电压的增大管子对于电流的控制能力是越来越弱的**。

#### 3.3.2 采用二极管连接型器件作负载的共源极

​		将晶体管的栅极和漏极短接，得到的器件称为“二极管连接型器件”。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230811095737966.png" alt="image-20230811095737966" style="zoom:50%;" />

​		**该晶体管总是工作在饱和区**。（注意NMOS的衬底连接方式，直接接地或接正电压（考虑体效应））



<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230812084234506.png" alt="image-20230812084234506" style="zoom:50%;" />

​		随着I<sub>1</sub>突变为0，V<sub>out</sub>首先提升至V<sub>DD</sub> - V<sub>TH2</sub>（此段的斜率是由于电容的存在），随后缓慢的提升至V<sub>DD</sub>（由于阈值电压的作用）。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230812085522672.png" alt="image-20230812085522672" style="zoom:50%;" />

- **大信号分析：**利用电流电压关系

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230812092354546.png" alt="image-20230812092354546" style="zoom:50%;" />

​		两边对V<sub>in</sub>微分得小信号增益：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230812092513088.png" alt="image-20230812092513088" style="zoom:50%;" />，其中η = g<sub>mb2</sub>/g<sub>m2</sub>（![image-20230812090547722](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230812090547722.png)为跨导，![image-20230812090619952](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230812090619952.png)为体跨导)

- **二极管连接型器件作负载的共源极输入输出关系：**

​                                                                            <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230812085433755.png" alt="image-20230812085433755" style="zoom:50%;" />

- **小信号分析：**利用小信号等效模型

​		先分析M<sub>2</sub>管：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230812093056101.png" alt="image-20230812093056101" style="zoom:50%;" />

其中：![image-20230913102651249](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230913102651249.png)

​		得出结论：二极管连接型器件等效为1/g<sub>m</sub>的电阻（不考虑体效应）（1/g<sub>m</sub>一般为几十kΩ，r<sub>o</sub>一般小于1kΩ，故两者并联时r<sub>o</sub>可忽略）

​		随后分析两管：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230812092828254.png" alt="image-20230812092828254" style="zoom:50%;" />

- 小信号增益：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230812085759897.png" alt="image-20230812085759897" style="zoom:50%;" />，其中η = g<sub>mb2</sub>/g<sub>m2</sub>（![image-20230812090547722](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230812090547722.png)为跨导，![image-20230812090619952](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230812090619952.png)为体跨导)

- 输入输出电阻：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230812100617232.png" alt="image-20230812100617232" style="zoom:50%;" /><img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230812100654009.png" alt="image-20230812100654009" style="zoom:50%;" />

​		**两个NMOS连接时，电路的增益和输出电阻大小会受到体效应的影响，PMOS二极管负载时体效应消失（PMOS的源极直接接在了V~DD~上，故V~BS~不变，体效应影响消失）**

#### 3.3.3 采用电流源作负载的共源极

​		单级需要很大增益的时候，可以增大共源极的负载电阻，但是对于电阻或者二极管连接的负载而言，增大阻值会消耗直流压降，从而限制输出电压摆幅。可以使用电流源替代负载。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230812103802914.png" alt="image-20230812103802914" style="zoom:50%;" />

注1：M<sub>1</sub>和M<sub>2</sub>的类型不同，如果两者都是NMOS管，会受到体效应的影响。

注2：M<sub>2</sub>的栅极输入为直流电压V<sub>B</sub>，源极输入为直流电压V<sub>DD</sub>，对于小信号来说均为“地”，故M<sub>2</sub>小信号等效模型为一个电阻（v<sub>gs</sub> = 0，压控电流源为0）

​		两个管子都是电流源，当两个管子饱和区的工作电流大小不同的时候，整体电路由电流小的管子决定（电流小的管子工作于饱和区的时候，由于两者的电流需要相等，故另一个管子工作于线性区）；电路的输入偏置点不稳定，较难确定下来；

#### 总结：

##### 分析方法：三部曲

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230813163732167.png" alt="image-20230813163732167" style="zoom:50%;" />

##### 输出负载总结：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230813163926872.png" alt="image-20230813163926872" style="zoom: 33%;" />

##### 输出电压与电流的关系图：（大信号直流偏置点以及小信号波动）

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230813210333876.png" alt="image-20230813210333876" style="zoom: 33%;" />

结论：相同的V<sub>in</sub>在负载引起的电流波动，二极管连接型器件波动最小，电流源负载波动最大。

#### 3.3.4 有源负载的共源极

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230813172214375.png" alt="image-20230813172214375" style="zoom:50%;" />

电路增益：                                                           <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230813172240308.png" alt="image-20230813172240308" style="zoom: 67%;" />

​		此电路增大了增益，还可以降低噪声，缺点偏置点太容易波动。

#### 3.3.6 带源极负反馈的共源极

​		前面讨论的几种共源放大电路存在一个共同的问题：增益非线性（跨导g<sub>m</sub>都是关于输入电压V<sub>gs</sub>的函数），为了改善（“软化”器件的非线性）可以作如下改进：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230813174034233.png" alt="image-20230813174034233" style="zoom:50%;" />

​		先忽略体效应和沟道调制效应进行分析，将R<sub>s</sub>和M<sub>1</sub>看作整体，计算可得其增益为：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230813174133931.png" alt="image-20230813174133931" style="zoom: 50%;" />

​		电路整体小信号电压增益为：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230813174230701.png" alt="image-20230813174230701" style="zoom:50%;" /><img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230813174251000.png" alt="image-20230813174251000" style="zoom:50%;" />

​		当R<sub>s</sub>足够大时，G<sub>m</sub> ≈ 1/R<sub>s</sub>，A<sub>v</sub> = R<sub>D</sub>/R<sub>s</sub>，软化了非线性，但增益变小。

- **输出电阻：**

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230814112851912.png" alt="image-20230814112851912" style="zoom:50%;" />

> 共源极总结：
>
> <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230906111223841.png" alt="image-20230906111223841" style="zoom:50%;" />



### 3.4 源跟随器

> 共源极放大器的缺点：输出电阻太大，不能驱动很小的电阻
>
> 理想源跟随器要求：输入电阻无穷大，增益为1，输出电阻为0。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230814114601206.png" alt="image-20230814114601206" style="zoom:50%;" />

​		缺点：电阻R<sub>s</sub>会导致管子的电流I<sub>D</sub>变化（随着输入电压的增大，输出电压也增大，欧姆定律计算可得电流不断增大），会导致非线性严重。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230814114645758.png" alt="image-20230814114645758" style="zoom:50%;" />

- 根据小信号模型计算可得：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230814114801620.png" alt="image-20230814114801620" style="zoom: 33%;" />，小于1。

​		注：V~bs~就是 -V~out~，V~in~ - V~1~ = V~out~

​		为了解决电流变化的问题，选择使用电流源替换电阻R<sub>S</sub>（电流源内阻无穷大）。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230814115708089.png" alt="image-20230814115708089" style="zoom: 33%;" />

​		由于M<sub>2</sub>的沟道长度调制效应，V<sub>out</sub>变化的时候会导致管子电流发生变化，从而导致V<sub>GS</sub>发生变化，输入输出非线性。

​		增益为：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230814121121208.png" alt="image-20230814121121208" style="zoom:33%;" />，即R<sub>s</sub> = ∞。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230814121424329.png" alt="image-20230814121424329" style="zoom: 50%;" />

- 根据小信号模型计算可得输出电阻为：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230814121607387.png" alt="image-20230814121607387" style="zoom: 33%;" />

### 3.5 共栅极

> 最大优点：小输入电阻，输入信号可以是电流

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230814134842944.png" alt="image-20230814134842944" style="zoom: 33%;" />

注：

1. 共栅极，即栅极接地，图中的V<sub>b</sub>是直流电压，对于小信号来说等效于地。
2. （a）中的直流偏置由V<sub>B</sub>和V<sub>in</sub>共同决定（V<sub>GS</sub> = V<sub>B</sub> - V<sub>in</sub>）；（b）中的直流偏置由电流源 I<sub>1</sub> 决定（电流确定，管子会根据输入电压V<sub>B</sub>的变化自适应产生源极电压V<sub>s</sub>），再通过电容将输入V<sub>in</sub>耦合进电路。

- 共栅极的输入输出关系如下：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230814143057059.png" alt="image-20230814143057059" style="zoom:33%;" />

> 和共源极不同，共栅极的输出电压随输入电压的增大而增大。		

- 计算电压增益：                                                    <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230814144206705.png" alt="image-20230814144206705" style="zoom:33%;" />

得到结果：                         <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230814144306728.png" alt="image-20230814144306728" style="zoom: 33%;" />

- 计算输入电阻：                              <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230814144414315.png" alt="image-20230814144414315" style="zoom:33%;" />

**得到共栅极输入电阻结果**：                        <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230814144624356.png" alt="image-20230814144624356" style="zoom:33%;" />

- 计算输出电阻：                                 <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230814150734979.png" alt="image-20230814150734979" style="zoom:33%;" />

得到输出电阻：              <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230814150824375.png" alt="image-20230814150824375" style="zoom:33%;" />

### 3.6 共源共栅级

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230814151534106.png" alt="image-20230814151534106" style="zoom:50%;" />

- 输入输出关系：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230814194439577.png" alt="image-20230814194439577" style="zoom:33%;" />  输出阻抗：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230814194539483.png" alt="image-20230814194539483" style="zoom: 50%;" />

注：求输出阻抗时，M<sub>1</sub>的输入V<sub>in</sub>对于小信号来说等效于地，故M<sub>1</sub>小信号等效于电阻r<sub>o1</sub>（此时的输出电阻与带源极负反馈的共源极电路相同）

求得输出阻抗为：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230814194944773.png" alt="image-20230814194944773" style="zoom: 25%;" />，

![image-20230814195840934](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230814195840934.png)

​		结论：共源共栅电路的输出阻抗等于M<sub>2</sub>管（即共栅管）的本征增益乘以共源管的等效电阻；可以以此类推增加共栅管的数量进行级联增大输出电阻的值，最终得到很大的输出电阻，使得输出电流恒定。缺点：对于输入电压的要求更高。

- 小信号增益：         <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230814201456623.png" alt="image-20230814201456623" style="zoom:33%;" />                    <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230814201530594.png" alt="image-20230814201530594" style="zoom:33%;" />               

得到增益：             <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230814201644787.png" alt="image-20230814201644787" style="zoom:33%;" />

- 本征增益：（输出负载阻抗无穷大时的增益）<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230814201743313.png" alt="image-20230814201743313" style="zoom:33%;" />，负载为电流源，阻抗无穷大。

得到本征增益：         <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230814201950952.png" alt="image-20230814201950952" style="zoom:33%;" />

结论：共源共栅级电路的本征增益是共源放大器的平方；**共源共栅是实现高增益的基础**。

> 共源共栅可以实现高增益的原因：r~o1~与M~2~之间的负反馈

## 第4章 差动放大器

​		本章目的：CMOS差动放大器的分析和设计

### 4.1 差动

​		差动信号定义为两个结点电位之差，且这两个结点电位相对于某一固定**电位大小相等，相位相反**。

​		差动信号的好处：1，共模噪声抑制 2，共模干扰抑制 3，得到最大的输出电压摆幅

​						   缺点：1，芯片面积和供电几乎双倍 2， 噪声功率增加（两边噪声的产生是没有相关性的，不能完全抵消）

![image-20230815103701540](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230815103701540.png)                得到共模电压：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230815103427433.png" alt="image-20230815103427433" style="zoom:33%;" />，实际应用时希望共模电平固定。

​		得到差模信号：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230815103823389.png" alt="image-20230815103823389" style="zoom:33%;" />	

注：两信号相减后得到差模信号，**共模信号被减去，但不代表共模信号不存在**，且对电路工作点至关重要。

### 4.2 分析

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230815134138091.png" alt="image-20230815134138091" style="zoom:33%;" />

- 差模部分输入输出特性：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230815134338782.png" alt="image-20230815134338782" style="zoom:33%;" />

- 共模部分输入输出特性：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230815141435420.png" alt="image-20230815141435420" style="zoom: 50%;" />

​		输入共模电压V<sub>in,COM</sub>从0增大到V<sub>DD</sub>：（1）V<sub>in,CM</sub> = 0，两个管子均未导通，I<sub>D1,2</sub> = 0，V<sub>out1,2</sub> = 0，V<sub>p</sub> = 0；（2）V<sub>in,COM</sub> > V<sub>TH</sub>，两个管子导通，M<sub>3</sub>工作于线性区等效于一个电阻；（3）V<sub>in,CM</sub> ≥ V<sub>GS1</sub> + (V<sub>GS3</sub> - V<sub>TH3</sub>)，随着V<sub>in,CM</sub>继续增加，I<sub>D1,2</sub>和V<sub>out1,2</sub>趋于常数；（4）V<sub>in,CM</sub> ≤ V<sub>out1,2</sub> + V<sub>TH</sub> = V<sub>DD</sub> - R<sub>D</sub>I<sub>SS</sub>/2 + V<sub>TH</sub>，否则两个管子会工作于线性区。 

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230815143200225.png" alt="image-20230815143200225" style="zoom: 33%;" />

- 大信号分析：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230816074128065.png" alt="image-20230816074128065" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230816074218113.png" alt="image-20230816074218113" style="zoom: 50%;" />

跨导：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230816074253852.png" alt="image-20230816074253852" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230816074831754.png" alt="image-20230816074831754" style="zoom:50%;" />

当V<sub>in,diff</sub> = 0时（即V<sub>in1</sub> = V<sub>in2</sub>，输入共模信号），跨导：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230816074618285.png" alt="image-20230816074618285" style="zoom: 33%;" />

此时的小信号增益为：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230816074734260.png" alt="image-20230816074734260" style="zoom:33%;" />

令G<sub>m</sub> = 0，得到：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230816075512704.png" alt="image-20230816075512704" style="zoom:50%;" />                        <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230816080054223.png" alt="image-20230816080054223" style="zoom:33%;" />

​		物理意义：当输入的差模信号 -V<sub>in,diff1</sub> ≤ V<sub>in,diff</sub> ≤ V<sub>in,diff1</sub>时，跨导不为零，而当V<sub>in,diff</sub> > |V<sub>in,diff1</sub>|时，只有一个管子导通，电路失去控制作用。

结论：**有效差模信号的输入范围为**

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230816080610528.png" alt="image-20230816080610528" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230816080819911.png" alt="image-20230816080819911" style="zoom:50%;" />

 注：其中的<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230816081122764.png" alt="image-20230816081122764" style="zoom:33%;" />就是平衡状态（I<sub>D1</sub> = I<sub>D2</sub>=I<sub>ss</sub>/2）下管子的过驱动电压。

- 小信号分析方法一

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230816111653200.png" alt="image-20230816111653200" style="zoom: 33%;" />

先考虑V<sub>in1</sub>的作用：               <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230816111924389.png" alt="image-20230816111924389" style="zoom:33%;" />

注：只考虑V<sub>in1</sub>的作用，故M<sub>2</sub>的栅极接地，电流源I<sub>SS</sub>等效于一个无穷大的电阻，故直接去掉。

计算V<sub>in1</sub>对V<sub>x</sub>的影响：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230816112410386.png" alt="image-20230816112410386" style="zoom:33%;" />，此时R<sub>D2</sub>和M<sub>2</sub>一起等效于一个电阻R<sub>s</sub>（不考虑体效应和沟道长度调制效应，<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230816112701635.png" alt="image-20230816112701635" style="zoom:33%;" />)。

等效于一个带源极负反馈的共源极，增益为：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230816112734463.png" alt="image-20230816112734463" style="zoom:33%;" />

计算V<sub>in1</sub>对V<sub>y</sub>的影响：左边等效于一个源跟随器，通过戴维南等效可得：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230816141514437.png" alt="image-20230816141514437" style="zoom: 33%;" />

其中R<sub>T</sub>为源跟随器的输出电阻，不考虑体效应和沟道长度调制效应时，<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230816141737384.png" alt="image-20230816141737384" style="zoom:33%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230816141821689.png" alt="image-20230816141821689" style="zoom:33%;" />

由叠加原理可得：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230816142326888.png" alt="image-20230816142326888" style="zoom:33%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230816142352436.png" alt="image-20230816142352436" style="zoom:33%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230816142409948.png" alt="image-20230816142409948" style="zoom:33%;" />

- 小信号分析方法二：半边电路法

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230816143122747.png" alt="image-20230816143122747" style="zoom:33%;" />

​		电路中对于P点来说M<sub>1</sub>和M<sub>2</sub>均相当于源跟随器，当两边的输入变化是对称时，最后的结果是V<sub>p</sub>是一个常数，即对于小信号来说等效于“地”。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230816143614294.png" alt="image-20230816143614294" style="zoom:33%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230816144019041.png" alt="image-20230816144019041" style="zoom:33%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230816144035946.png" alt="image-20230816144035946" style="zoom:33%;" />

> 对于小信号差动电路的分析，只需要对电路进行半边电路等效，找到交流地的点，随后只用分析半边电路即可。

> 值得注意的是：
>
> <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230816145318447.png" alt="image-20230816145318447" style="zoom:33%;" />
>
> 电路的输出特性曲线如图所示，是一个曲线，故当V<sub>GS</sub>左右波动相同电压时，输出的电流左右波动大小不同，电流I<sub>D1</sub>或I<sub>D2</sub>增加的量大于减小的量，故导致P点的电压会产生波动，且波动频率是V<sub>in1,2</sub>频率的2倍。
>
> <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230816145947176.png" alt="image-20230816145947176" style="zoom:33%;" />
>
> 结论：**P点并不是理想的交流小信号“地”**，只有当输入信号较小时，P点的电压波动较小，才可以忽略；当输入信号较大时，P点的波动也较大，不可忽略，此时电路可以当作一个倍频器使用，**P点波形的频率等于输入信号频率的2倍**。

### 4.3 共模响应

​		电路将两个管子栅极相连，只输入V<sub>in,CM</sub>共模信号，理想情况下电路输出只有共模信号，差模信号输出为0。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230816222614460.png" alt="image-20230816222614460" style="zoom:33%;" />

​		在实际非理想的情况下：

1. **M<sub>3</sub>管并不是理想的电流源（有限的非电流源阻抗）**，内阻小于无穷大且由于沟道调制作用的影响，会导致偏置电流产生波动；
2. **M<sub>1</sub>和M<sub>2</sub>两个管子并不是完全一样的（失配）**，会导致电流源的电流分配后流过该两个管子的电流并不是I<sub>SS</sub>/2，两个管子的电流不同，最后导致V<sub>out1</sub>和V<sub>out2</sub>电压值不同，即电路最后会产生差模输出信号，将一个共模变化转化成了差模变化。

​		理想情况下，进行分析，可得等效电路：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230816223819745.png" alt="image-20230816223819745" style="zoom:33%;" />

​		可得共模增益为：         <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230816223926522.png" alt="image-20230816223926522" style="zoom:33%;" />，**共模增益越小越好**（让R<sub>SS</sub>越大越好）。

​		实际情况下：                                                        <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230817094520752.png" alt="image-20230817094520752" style="zoom:33%;" />

可得：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230817094645820.png" alt="image-20230817094645820" style="zoom:33%;" />         <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230817094709216.png" alt="image-20230817094709216" style="zoom:33%;" />       <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230817094746148.png" alt="image-20230817094746148" style="zoom:33%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230817094819113.png" alt="image-20230817094819113" style="zoom:33%;" />

得到实际情况中共模输入时差模增益为：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230817094916417.png" alt="image-20230817094916417" style="zoom:33%;" />，越小越好，希望为0。

共模抑制比**CMRR**：![image-20230817095939535](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230817095939535.png)



如何提高共模抑制比：（1）减小Δg<sub>m</sub>的值，即两个管子尽量一样；（2）R<sub>SS</sub>尽量大，增加尾管的尺寸。

### 4.4 吉尔伯特单元

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230817165217197.png" alt="image-20230817165217197" style="zoom:50%;" />

​		图（a）中的电路，控制电压确定了尾电流的大小，从而决定了增益的大小；此电路的缺点是增益是单向的，增益不能反向变化。图（b）中的两个电路增益一正一负，如果可以将两个电路输出信号相加，即可得到双向增益。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230817164815476.png" alt="image-20230817164815476" style="zoom: 67%;" />

​		图（a）中将两个放大器的输出电压进行相加可以得到，最简单的方式是将两个输出直接相连，但直接相连后的电路的输出电阻会被改变，故想实现两个电压相加较为困难。转变思想，直接将两个电路的输出信号以电流的形式进行相加较为容易，如图（b）所示，其中V<sub>cont1,2</sub>分别控制两个差动对的电流从而控制增益大小，可得：

​                                                  <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230817202639012.png" alt="image-20230817202639012" style="zoom:33%;" />                <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230817202721033.png" alt="image-20230817202721033" style="zoom:33%;" />

这种连接方式可以实现放大器电路的增益从负到正的变化。为了提高增益控制效率，再增加一对差动对，两个差动管共用电流源I<sub>SS</sub>，用来进行电流源I<sub>SS</sub>的第一次分配，M<sub>5,6</sub>两个管子其中一个管子的电路增大，另一个管子电流会自动减小（总和为I<sub>SS</sub>不变），电路结构改进如图（d）可以实现一个可变增益放大器，V<sub>cont</sub>同时控制两个差动对的电流大小，实现宽范围的调节，缺点是输出范围会减小一个V<sub>OD</sub>（因为多了一对MOS管）。

> 吉尔伯特单元应用：1，可变增益放大器，如上所述
>
> ​								  2，混频器，上图（d）中的V<sub>in</sub>和V<sub>cont</sub>两个输入信号为频率不同的正弦交流信号时，V<sub>out</sub>输出信号是两个输入信号乘积的函数，经过积化和差公式的推导，得到频率相加减的效果。

## 第5章 电流镜与偏置技术

​		本章目的：电流镜和偏置电路的设计

### 5.1 基本电流镜

​		电流源是模拟IC中的一个基础模块，如何获得一个稳定的电流源是一个重要的问题。

​		**影响模拟电路性能的几个主要因素：P（工艺），V（电源电压），T（温度），L（负载波动）**

​		如何获得一个稳定的电流源呢？

​		解决方式：通过**将一个稳定的电流基准“复制”过来即可**（基准电流的产生后面章节内容，本章只用将参考电流基准复制即可）。

- 复制电路原理：

​                                          <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230818115001877.png" alt="image-20230818115001877" style="zoom: 33%;" />		<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230818115025445.png" alt="image-20230818115025445" style="zoom: 33%;" />              <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230818115106767.png" alt="image-20230818115106767" style="zoom: 33%;" />

- 基本电流镜电路：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230818115314204.png" alt="image-20230818115314204" style="zoom:33%;" />

- 电流镜产生n*I<sub>REF</sub>：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230818115607335.png" alt="image-20230818115607335" style="zoom: 33%;" />，电流放大倍数由两个该管子的器件尺寸比值决定。

​		注：电路中M<sub>1</sub>肯定工作于饱和区，M<sub>2</sub>的不一定，它的工作状态由其漏极连接的外电路决定。

举个例子：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230818120941520.png" alt="image-20230818120941520" style="zoom: 67%;" />

图中M<sub>0</sub>构成的电流镜由于尺寸比为1：2，得到流入M<sub>5</sub>电流镜的电流为2I<sub>REF</sub>，由于尺寸比为1：5，故流入M<sub>1</sub>管的电流为2.5I<sub>REF</sub>，故可得M<sub>3</sub>中的电流为0.5I<sub>REF</sub>，故M<sub>5</sub>和M<sub>3</sub>的电流大小比为4：1。此电路中的电流大小完全与电压等因素无关，电流的大小关系只由管子的尺寸比决定。

- 电流镜作为电流放大器

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230818121812448.png" alt="image-20230818121812448" style="zoom: 50%;" /><img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230818121852755.png" alt="image-20230818121852755" style="zoom:33%;" /><img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230818121918230.png" alt="image-20230818121918230" style="zoom:33%;" />

### 5.2 共源共栅电流镜

​		上述基本电流镜电流分析均忽略了沟道长度调制效应，当考虑此效应时，会发现由于M<sub>2</sub>管的漏极电压不确定导致V<sub>DS</sub>不确定，最后导致“复制”的电流结果不对。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230818151057853.png" alt="image-20230818151057853" style="zoom:33%;" />

- 为了抑制沟道长度调制效应的影响，采用共源共栅结构（此结构输出电阻很大，可以有效抑制沟道长度调制效应带来的电流波动）

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230818151813415.png" alt="image-20230818151813415" style="zoom: 33%;" />电路改进：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230818151903669.png" alt="image-20230818151903669" style="zoom: 33%;" />

​		在M<sub>2</sub>的漏极增加一个NMOS，M<sub>3</sub>作为保护管（或屏蔽管），由于M<sub>3</sub>的输出电阻值很大，故当P点输入电流产生波动时产生的电压波动很小，传至M<sub>2</sub>的漏极电压波动很小，故达到抑制沟道长度调制效应的效果。（**实质是M<sub>2</sub>和M<sub>3</sub>之间的负反馈产生了很大的输出电阻**，导致整个结构对电流电压的波动不那么敏感）

- 如果可以保证V<sub>Y</sub> = V<sub>X</sub>，就可以使得I<sub>out</sub> = I<sub>REF</sub>，故要求：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230818152731097.png" alt="image-20230818152731097" style="zoom:33%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230818190033828.png" alt="image-20230818190033828" style="zoom:50%;" /><img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230818190301221.png" alt="image-20230818190301221" style="zoom:33%;" /><img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230818190332636.png" alt="image-20230818190332636" style="zoom:33%;" />

输出电压V<sub>P</sub>的最小值：![image-20230818190938730](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230818190938730.png)，对于低压电路来说输出最低工作电压损失太大了。

​		如果不要求V<sub>Y</sub> = V<sub>X</sub>，就可以降低V<sub>b</sub>的电压值，就可以得到一个更低的V<sub>P</sub>。

在P点处连接一个电压源，电压从0不断增大：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230818205943276.png" alt="image-20230818205943276" style="zoom:50%;" />

可以得到：

1. 当V<sub>X</sub> > V<sub>N</sub> - V<sub>TH3</sub> 时，M<sub>3</sub>和M<sub>2</sub>两个管子都工作于饱和区
2. 当V<sub>X</sub> < V<sub>N</sub> - V<sub>TH3</sub> 时，M<sub>3</sub>工作于线性区，M<sub>2</sub>工作于饱和区
3. 共源共栅电流镜的优点：可以精确的复制电流，且偏置不复杂；缺点：多消耗了一个V<sub>TH</sub>。

- 低压共源共栅电流镜

​                                             <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230818214928420.png" alt="image-20230818214928420" style="zoom: 50%;" />，M<sub>2</sub>的漏极直接连接至M<sub>1</sub>的栅极，V<sub>X</sub> = V<sub>GS1</sub>。

注：上电后，M~2~导通，但由于M~1~截止，所以M~2~电流为零。由于M<sub>1</sub>截止，故电流无法流通，只能通过导线流至M<sub>1</sub>的栅极，由于栅极对地有一个电容，随着栅极流入的电流越来越多，不断给电容进行充电，导致M<sub>1</sub>的栅极电压不断增大，最后使得M<sub>1</sub>导通。

如何设置V<sub>b</sub>：          <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230818215340957.png" alt="image-20230818215340957" style="zoom:50%;" />

得到V<sub>b</sub>范围：           <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230818215434577.png" alt="image-20230818215434577" style="zoom:33%;" />

​                        <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230818215810711.png" alt="image-20230818215810711" style="zoom: 50%;" />              <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230818215844936.png" alt="image-20230818215844936" style="zoom:33%;" />         

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230818215932595.png" alt="image-20230818215932595" style="zoom:33%;" /><img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230818215946262.png" alt="image-20230818215946262" style="zoom:33%;" />

​		结论：此电路可以准确复制电流，且V<sub>P</sub>的电压最小值较低，具备低压特性。

​		但其中的偏置电压V<sub>b</sub>还需要另外的电路产生符合条件（<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230818220531920.png" alt="image-20230818220531920" style="zoom: 33%;" /> = 2V<sub>OD</sub> + V<sub>TH</sub> )的电压。

**产生V<sub>b</sub>的方式：**

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230818221317241.png" alt="image-20230818221317241" style="zoom: 50%;" />

​		采用图示电路产生V<sub>b</sub>，其中M<sub>5,6</sub>两个管子的要求：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230818221608092.png" alt="image-20230818221608092" style="zoom:33%;" />，利用电阻R<sub>b</sub>的压降替代M<sub>1</sub>管导通电压V<sub>TH1</sub>，使得<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230818221817580.png" alt="image-20230818221817580" style="zoom:33%;" />，得到<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230818221837268.png" alt="image-20230818221837268" style="zoom:33%;" />。

​		缺点：由于使用电阻替代导通电压V<sub>TH1</sub>，电阻的工艺问题导致生成的电压会上下浮动，不准确；由于想让M<sub>5</sub>

管替代M<sub>2</sub>管，让M<sub>6</sub>管替代M<sub>1</sub>管，但管子之间的体效应不同，故导致最后电压有所不同。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230818222353139.png" alt="image-20230818222353139" style="zoom:50%;" />

​		由于上面电路使用电阻导致不好的结果，故使用MOS管替代电阻，利用M<sub>7</sub>管替代M<sub>1</sub>管导通电压V<sub>TH1</sub>，<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230818222554042.png" alt="image-20230818222554042" style="zoom:33%;" />（M<sub>7</sub>需要有特别长的沟道才可以实现两个电压相等），得到<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230818222815561.png" alt="image-20230818222815561" style="zoom:33%;" />。

​		缺点：仍然存在体效应的影响。

​		**上述的两种电路了解即可，均存在问题，不适合实际应用。**

- 自偏置的共源共栅电流镜：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230819092800398.png" alt="image-20230819092800398" style="zoom:50%;" />

优点：结构简单，开销小；缺点：由于电阻工艺会导致输出产生波动。

- 使用另一个管子产生V<sub>b</sub>（stacked MOS）：（简单实用）

​                  <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230819094719964.png" alt="image-20230819094719964" style="zoom:50%;" />        其中M<sub>5</sub>也可以用两个管子串联的形式表示：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230819093314965.png" alt="image-20230819093314965" style="zoom:50%;" />

优点：由于输出电压由管子的尺寸比决定，故准确度高。

##### 电流镜总结：

> ![image-20230911191242031](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230911191242031.png)

### 5.3 有源电流镜（五管单元）

​		将电流镜作为差动对的负载得到有源电流镜，**是一个放大器**。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230819103524137.png" alt="image-20230819103524137" style="zoom: 33%;" />

​		**输入是差动信号，输出是单端。**当输入V<sub>in</sub>增大，导致V<sub>GS1</sub>增大，故 I<sub>D1</sub>增大，I<sub>D2</sub>减小（ I<sub>D1</sub> +  I<sub>D2</sub> =  I<sub>SS</sub>），同时由于电流镜的作用I<sub>D4</sub>增大（M<sub>2</sub>和M<sub>4</sub>串联，一个电流要增大，一个电流要减小，此时由电流小的管子决定）故M<sub>4</sub>进入线性区，导致V<sub>out</sub>急剧增大。故此电路由于电流镜的作用成为一个放大器，将输入的电压放大。

- 大信号分析

​		差模输出偏置点：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230819105837588.png" alt="image-20230819105837588" style="zoom: 33%;" />

当V<sub>in1</sub> = V<sub>in2</sub>时，<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230819110332924.png" alt="image-20230819110332924" style="zoom:33%;" />，由于结构的对称性，M<sub>1，2</sub>的电流相同，又由于电流镜的作用，M<sub>3,4</sub>的电流相同，<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230819110258798.png" alt="image-20230819110258798" style="zoom:33%;" /><img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230819110317001.png" alt="image-20230819110317001" style="zoom:33%;" />。

结论：**当V<sub>in1</sub> = V<sub>in2</sub>时，V<sub>out</sub> = V<sub>F</sub>**，电路的直流大信号偏置点是确定的唯一解。

​		输入的共模信号范围：（考虑共模，即让所有的管子都工作在饱和状态）

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230819110718693.png" alt="image-20230819110718693" style="zoom:33%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230819110852964.png" alt="image-20230819110852964" style="zoom:33%;" />

​		V<sub>in,CM</sub>最小值保证M<sub>5</sub>饱和，V<sub>out</sub>的范围与V<sub>in,CM</sub>有关。	

-  差模小信号分析

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230819112451578.png" alt="image-20230819112451578" style="zoom:33%;" />由于电路结构不对称，故半边电路等效方法不能用，<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230819112615345.png" alt="image-20230819112615345" style="zoom:33%;" />

​		计算等效跨导和负载电阻的值：

​                             <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230819112859810.png" alt="image-20230819112859810" style="zoom:33%;" />                 <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230819112931780.png" alt="image-20230819112931780" style="zoom:33%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230819113319900.png" alt="image-20230819113319900" style="zoom:33%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230819113336530.png" alt="image-20230819113336530" style="zoom:33%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230819113351874.png" alt="image-20230819113351874" style="zoom:33%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230819113408828.png" alt="image-20230819113408828" style="zoom:33%;" />

​                                               <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230819113446823.png" alt="image-20230819113446823" style="zoom:33%;" />          <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230819114107549.png" alt="image-20230819114107549" style="zoom: 33%;" />

小信号增益：     <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230819114142400.png" alt="image-20230819114142400" style="zoom:33%;" />

- 总结：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230819201027020.png" alt="image-20230819201027020" style="zoom: 33%;" />

​		当V<sub>in1</sub>和V<sub>in2</sub>一个增大一个减小时，假设V<sub>in1</sub>增大V<sub>in2</sub>减小，此时M<sub>1</sub>管的电流增大，M<sub>2</sub>管的电流减小，导致M<sub>3</sub>管的电流也增大，故M<sub>3</sub>管的|V<sub>GS</sub>|增加，从而使得V<sub>F</sub>减小为V<sub>F</sub>‘，M<sub>4</sub>管电流增大为I<sub>M4</sub>’，导致V<sub>out</sub>电压增大。

​		结论：当差动电压变化时，引起的M<sub>1</sub>管和M<sub>2</sub>管电流变化几乎相等，但引起的V<sub>F</sub>和V<sub>out</sub>的变化完全不对称（F点是小阻抗≈1/g<sub>m3</sub>，out点是大阻抗 = R<sub>o2</sub>|| R<sub>o4</sub>），见图中的ΔV<sub>F</sub>和ΔV<sub>out</sub>。

- 共模响应：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230819203134385.png" alt="image-20230819203134385" style="zoom:33%;" />

1，考虑尾管电流源的有限阻抗

​		对于单端输出的电路，和差动对不同（差动对还需要两个管子失配才会受到共模的影响），直接会受到共模的影响，<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230819203456537.png" alt="image-20230819203456537" style="zoom: 33%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230819203609444.png" alt="image-20230819203609444" style="zoom:33%;" />

​		注：由于对称性，V<sub>out</sub>和V<sub>F</sub>一直相同，故可以将两点直接连接。得到的等效信号模型实质为带源极负反馈的共源极。

得到共模增益为：       <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230819203856588.png" alt="image-20230819203856588" style="zoom:33%;" />

得到共模抑制比**CMRR**（Commom-mode rejection ratio）：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230819204155176.png" alt="image-20230819204155176" style="zoom:33%;" />

注：这里的CMRR定义和全差动对的定义不同。

- 五管单元（有源电流镜）与全差动对的比较：

1. 共模特性（CMRR）比较：           <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230819204506615.png" alt="image-20230819204506615" style="zoom: 33%;" />

​		五管单元的共模抑制特性比全差动对差。

2. 电源波动抑制特性（PSRR）比较：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230819204852467.png" alt="image-20230819204852467" style="zoom:33%;" />

​		五管单元对于电源波动的抑制能力非常差。

### 5.4 偏置技术

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230819213948907.png" alt="image-20230819213948907" style="zoom: 50%;" />

​		图（a）中V<sub>B</sub>提供偏置点，V<sub>in</sub>输入交流信号，但两个信号会相互干扰；图（b）所示，使用一个大电阻将V<sub>B</sub>接入，使用大电容实现交流耦合将V<sub>in</sub>输入（要想输入信号损失越小，就要求电阻和隔直电容值越大越好）；

## 第6章 放大器的频率特性

​		本章目的：研究单级放大器和差动放大器在频域中的响应

### 6.1 概述

​		简单回顾：零点是系统传输函数中分子的根，极点是系统函数中分母的根；对于一阶系统（即单极点系统），ω通过一个极点频率时以20dB/dec下降（频率每增加十倍，对应的幅值减小20dB）；当ω通过一个零点频率时以20dB/dec上升；一个零点可以和一个极点作用抵消。

- 极点与结点的关联

​		==**电路存在的每一个结点均会贡献一个极点**==。

**结点分析法**：

例1：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230821171610801.png" alt="image-20230821171610801" style="zoom:33%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230821171814202.png" alt="image-20230821171814202" style="zoom:33%;" />

其中的![image-20230821171836347](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230821171836347.png)为电路的直流响应（即频率为0的增益)，后面的每一个结点均贡献一个极点，**每个极点的频率 *ω*<sub>pM</sub> = 1/R<sub>M</sub> * C<sub>M</sub>**，其中**R<sub>M</sub>是指每个结点处对地的电阻值，而C<sub>M</sub>是指每个结点的总电容值**。

例2：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230821172833093.png" alt="image-20230821172833093" style="zoom:33%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230821172943667.png" alt="image-20230821172943667" style="zoom: 33%;" />

其中R<sub>S</sub>是电路的输入电阻。

例3：忽视沟道调制效应

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230821182402029.png" alt="image-20230821182402029" style="zoom: 33%;" />

​                                              <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230821182508894.png" alt="image-20230821182508894" style="zoom:33%;" />               <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230821182530715.png" alt="image-20230821182530715" style="zoom:33%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230821182606679.png" alt="image-20230821182606679" style="zoom:33%;" />

### 6.2 共源极

- 密勒定理

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230821183140048.png" alt="image-20230821183140048" style="zoom:33%;" />

==**使用条件：电路要有信号的主通路和辅助通路，主通路提供增益，辅助通路提供阻抗。**==

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230821211507461.png" alt="image-20230821211507461" style="zoom:50%;" />

**等效的输入电容被放大（1+A）倍，等效输出电容不变**。可以做一个电容放大器。

- 共源极的高频等效模型如下：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230822101654704.png" alt="image-20230822101654704" style="zoom: 50%;" />

1. 情况一：**R<sub>S</sub>很小的情况**（如第一级中的电压源驱动，此时R<sub>S</sub>为电压源内阻很小）

​		采用米勒近似的简化电路如下：                   <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230822102314026.png" alt="image-20230822102314026" style="zoom:50%;" />

在X结点的总电容为C<sub>GS</sub> + （1 + g<sub>m</sub>R<sub>D</sub>）C<sub>GD</sub>，X结点的对地电阻为R<sub>S</sub>，X结点的频率<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230822102705411.png" alt="image-20230822102705411" style="zoom:33%;" />（ω*<sub>pM</sub> = 1/R<sub>M</sub> * C<sub>M</sub>）；

在输出结点总电容为C<sub>GD</sub> + C<sub>GD</sub>，输出结点的电阻为R<sub>D</sub>，输出结点的频率<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230822103008449.png" alt="image-20230822103008449" style="zoom: 33%;" />；

2. 情况二：**R<sub>S</sub>很大的情况**（如中间级电路前一级的输出电阻很大，即此中间级电路的输入电阻R<sub>S</sub>很大）

   <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230822103322824.png" alt="image-20230822103322824" style="zoom: 33%;" />

此时输入节点的频率ω<sub>in</sub>不变，依然可以通过米勒等效表达，总电容为C<sub>GS</sub> + （1 + g<sub>m</sub>R<sub>D</sub>）C<sub>GD</sub>，X结点的对地电阻为R<sub>S</sub>，X结点的频率<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230822102705411.png" alt="image-20230822102705411" style="zoom:33%;" />（ω*<sub>pM</sub> = 1/R<sub>M</sub> * C<sub>M</sub>）；但是输出电阻改变，<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230822104134796.png" alt="image-20230822104134796" style="zoom:33%;" />，总电阻为<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230822104209614.png" alt="image-20230822104209614" style="zoom:50%;" />，等效电容<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230822104251873.png" alt="image-20230822104251873" style="zoom:33%;" />（即C<sub>GD</sub>和C<sub>GS</sub>串联），故总电容为C<sub>eq</sub> + C<sub>DB</sub>，结点频率为：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230822104505356.png" alt="image-20230822104505356" style="zoom:50%;" />，**其中当C<sub>GD</sub> >> C<sub>GS</sub>时，ω<sub>p,out</sub> = g<sub>m</sub>/（C<sub>GS</sub> + C<sub>DB</sub>)**。

> ==总结：==
>
> 输入结点频率：               <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230822104951166.png" alt="image-20230822104951166" style="zoom:50%;" />
>
> 输出结点频率：            <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230822105017480.png" alt="image-20230822105017480" style="zoom:50%;" />
>
> ![image-20230822105159894](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230822105159894.png)，<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230822110103418.png" alt="image-20230822110103418"  />
>
> 增益：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230822110256717.png" alt="image-20230822110256717" style="zoom:50%;" />
>
> 米勒等效忽略了电路的零点，此被忽略的零点的频率为![image-20230822142010425](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230822142010425.png)，其中的“ + ”表示零点位于右半平面，对于系统的稳定性有害。
>
> 关于零点的经验：**电路中含有两条以上的通路就会产生零点**。例如<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230822112730017.png" alt="image-20230822112730017" style="zoom: 67%;" />![image-20230822113238613](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230822113238613.png)
>
> 如何计算此零点：在此零点的复频率S<sub>Z</sub>下，V<sub>out</sub> = 0；输出端没有电流，可得<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230822141820180.png" alt="image-20230822141820180" style="zoom:33%;" /><img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230822141910233.png" alt="image-20230822141910233" style="zoom:33%;" />

- 共源极的输入阻抗（由于米勒等效的作用）

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230822142153621.png" alt="image-20230822142153621" style="zoom:50%;" />

注：共源极的输入电阻是无穷大的，输入阻抗与电阻的不同是要考虑虚部，**在高频的情况下输入阻抗并不是无穷大，随着频率的增大输入阻抗不断减小**。

### 6.3 源跟随器

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230822203000681.png" alt="image-20230822203000681" style="zoom:50%;" />

1. 传输函数包含一个在左平面的零点：高频时由C~GS~传导的信号与本征晶体管产生的信号以相同的极性相加。
2. <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230822203146742.png" alt="image-20230822203146742" style="zoom:50%;" />
3. 若源跟随器前一级输出阻抗很大，则源跟随器的输出阻抗表现出电感特性（随频率增加）。

### 6.4 共栅极

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230822203853626.png" alt="image-20230822203853626" style="zoom:50%;" />

1. 因为输入和输出的两个结点是“独立”的，没有密勒电容耦合，所以共栅级可以达到宽带。
2. <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230822204059280.png" alt="image-20230822204059280" style="zoom:50%;" />

3. 如果与栅串联的是大阻抗，则降低了极点频率。

## 第7章 噪声

​		本章目的：将随机噪声进行量化，可以在模拟电路的设计中更直观方便的考虑噪声。

### 7.1 噪声的统计特性

​		噪声限制了一个电路能够正确处理的最小信号电平。

​		噪声的幅值是不可预测的，但平均功率是可预测的，功率P = u^2^/R，通常令R = 1，故功率P = U^2^

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230823105339134.png" alt="image-20230823105339134" style="zoom:50%;" />

​		噪声功率谱：将噪声功率放至在频域观察；PSD（power spectrum density）噪声功率密度：使用一个1Hz的带通滤波器去测量每个频率的功率。PED单位为<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230823105958874.png" alt="image-20230823105958874" style="zoom:50%;" />，或者使用VSD（幅值功率密度），单位为<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230823110052999.png" alt="image-20230823110052999" style="zoom:50%;" />

​		在统计域中，噪声的平均功率可以用方差<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230823111113659.png" alt="image-20230823111113659" style="zoom:50%;" />表示。

噪声功率在统计域和频域中的表示与联系：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230823111220365.png" alt="image-20230823111220365" style="zoom:50%;" />（统计域中）= <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230823111410701.png" alt="image-20230823111410701" style="zoom:50%;" />（频域中）

​		噪声之间如果不相关，两个噪声的功率和为<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230823111939281.png" alt="image-20230823111939281" style="zoom:50%;" />，直接相加即可；噪声之间如果相关，噪声可以被增强或抵消，<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230823112127668.png" alt="image-20230823112127668" style="zoom: 50%;" />。

信噪比（SNR）：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230823112411033.png" alt="image-20230823112411033" style="zoom:50%;" />，<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230823112429625.png" alt="image-20230823112429625" style="zoom:50%;" />。

​		**放大器只能降低SNR，不能提升SNR**，（放大器对于信号和噪声的放大能力相同，但电路本身会提供噪声，故使得SNR下降）

### 7.2 噪声类型

> ==只有电阻和MOS管贡献噪声，电容电感不会产生噪声==

1. 电阻热噪声：

​		建模：一个噪声电压源串联一个电阻，使用单边谱表达。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230823145422786.png" alt="image-20230823145422786" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230823145505663.png" alt="image-20230823145505663" style="zoom: 50%;" />

其中K为玻尔兹曼常数，T为绝对温度

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230823145631598.png" alt="image-20230823145631598" style="zoom:50%;" />

诺顿等效：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230823145717326.png" alt="image-20230823145717326" style="zoom:50%;" />

例子：计算RC低通滤波器的噪声

![image-20230823150506656](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230823150506656.png)

结论一阶RC电路中的**噪声是由电阻R产生，但噪声大小是由电容C决定的**。

2. MOS管热噪声：针对工作于饱和区的长沟道MOS管

​		建模：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230823150910205.png" alt="image-20230823150910205" style="zoom:50%;" />

注：随着沟道长度减小，<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230823150945647.png" alt="image-20230823150945647" style="zoom:50%;" />不断增大，最大至2.5。

3. MOS管的欧姆区的热噪声：管子的栅，源，漏上的寄生电阻产生的热噪声

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230823151606888.png" alt="image-20230823151606888" style="zoom: 50%;" />

4. MOS管的闪烁噪声（又名1/f 噪声）

![image-20230824212705431](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230824212705431.png)

注：（1）此类噪声的建模是在栅极的电压，影响要转换为电流，故等效在栅极串联的一个电阻，和前面噪声的建模中的电阻（实际存在的寄生电阻）含义不同；（2）**此类噪声功率谱与频率成反比**，故被称为1/f 噪声，此类噪声与温度，跨导都无关。

### 7.3 电路中的噪声表示

1. 输出噪声：将输入端短接，在输出端看噪声

​		例：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230824214422922.png" alt="image-20230824214422922" style="zoom:50%;" />

​		由于在输出端看噪声不太方便（想知道最小的有效输入信号的大小还需要根据输出端的信噪比和噪声功率算得输出端的信号功率，再通过放大电路的增益才可以得到输入信号的大小），故将输出端的噪声返回输入端（将输出端的噪声在输入端等效为一个输入噪声源）。

2. 输入参考噪声：

![image-20230824215140663](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230824215140663.png)

​		将电路中的噪声等效为一个无噪声电路的输入端连接一个噪声源。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230824215301436.png" alt="image-20230824215301436" style="zoom:50%;" />

​		例：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230824215439957.png" alt="image-20230824215439957" style="zoom:50%;" />

​		注：在上一个例的输出噪声中观察可得输出噪声大小与跨导成正比，而在此例中得到的输入噪声与跨导成反比，故将噪声等效到输入端后更加直观，也更准确。

​		此时新的问题出现，当我们将等效到输入端的噪声源再输出到输出端时发现噪声被衰减了，原因是等效的输入噪声源再输入时被驱动信号的电阻和放大电路的输入电阻分压导致输入噪声被衰减，故**只是简单的将输出噪声等效为输入噪声电压源是错误的**。

3. 输入噪声的另一种等效方式：等效为一个输入噪声电压源加一个电流源

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230824220824227.png" alt="image-20230824220824227" style="zoom: 67%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230824220918434.png" alt="image-20230824220918434" style="zoom:50%;" />

​		如果驱动信号的是理想电压源（内阻为0），此时噪声电压源起作用；如果驱动信号的是一个很大的电阻，此时噪声电流源起作用。

电压源和电流源大小的计算：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230824221521174.png" alt="image-20230824221521174" style="zoom:50%;" />

​		先将输入短路，计算V~n,in~；再将输入开路，计算 I~n,in~。

电路等效模型：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230824221836983.png" alt="image-20230824221836983" style="zoom:50%;" />

其中Z~S~是驱动电阻，Z~in~是输入电阻。

注：如果<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230824222117133.png" alt="image-20230824222117133" style="zoom:50%;" />，电流源可以忽略；

### 7.4 单级放大器中的噪声

- 一个有用的辅助定理

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230824222915925.png" alt="image-20230824222915925" style="zoom:50%;" />

​		在满足条件时，可以将漏源之间的电流等效为栅极的一个电压源。

1. 共源极：由于输入内阻很大，故不用考虑噪声电流源

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230824223152993.png" alt="image-20230824223152993" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230824223410578.png" alt="image-20230824223410578" style="zoom: 67%;" />

​		只能通过增大跨导g~m~或者增大面积来减小噪声。

> 反相器（或class--AB）:<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230824223717446.png" alt="image-20230824223717446" style="zoom:67%;" /><img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230824223806658.png" alt="image-20230824223806658" style="zoom:67%;" />
>
> 是一个==非常有用的低噪声等效结构==。

2. 共栅极：输入端电阻较小，故噪声电压源和电流源都要考虑

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230824224135966.png" alt="image-20230824224135966" style="zoom:50%;" />

​		先短路输入，计算V~n,in~：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230824224335047.png" alt="image-20230824224335047" style="zoom:67%;" />

​		再输入开路：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230824224509063.png" alt="image-20230824224509063" style="zoom: 50%;" />

​		输入开路后，相当于电路没有“地”，故输入电流为0，电流只能经过M~1~流入V~DD~，

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230824224751644.png" alt="image-20230824224751644" style="zoom:50%;" />

> 共栅极电路中，电阻的中的噪声电流直接流入输入端，故==共栅极电路不适合用于做低噪声放大器==

3. 电流偏置的共栅极：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230825083713679.png" alt="image-20230825083713679" style="zoom:50%;" />

4. 源跟随器：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230825083815916.png" alt="image-20230825083815916" style="zoom:50%;" />

5. 共源共栅极：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230825083940382.png" alt="image-20230825083940382" style="zoom:50%;" />

​		注：M~2~中的噪声可以忽略不计。

6. 电流镜：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230825084207583.png" alt="image-20230825084207583" style="zoom:50%;" />

7. 差动对：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230825084354162.png" alt="image-20230825084354162" style="zoom:50%;" />

​		注：由于使用了两个MOS管，每一个管子都贡献了噪声，故噪声的功率是单端电路的两倍，噪声的电压是单端噪声的<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230825084753754.png" alt="image-20230825084753754" style="zoom:50%;" />倍。

​		尾电流源的噪声：只贡献共模噪声，对于差模噪声没有影响。

### 7.5 噪声-功率的折中

​		**噪声功率减半 <=> 电路的功耗和面积加倍**

### 7.6 噪声带宽

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230825085320590.png" alt="image-20230825085320590" style="zoom: 50%;" />

## 第8章 反馈

> 反馈能干啥？
>
> （1）对放大器的增益有所改善，使得增益对于环境、工艺等因素敏感度降低；
>
> （2）改变放大器的输入输出电阻；
>
> （3）改变放大器的带宽；（增益带宽积 = 增益 * 带宽 = 常数，故增益和带宽一个增大另一个只能减小）；
>
> （4）改善放大器的非线性，“虚短”；
>
> 其中各个量的改善程度由环路增益影响决定。

### 8.1 概述

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230825144948770.png" alt="image-20230825144948770" style="zoom:50%;" />

注：（1）闭环增益：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230825145112542.png" alt="image-20230825145112542" style="zoom:50%;" />= <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230921163658105.png" alt="image-20230921163658105" style="zoom:50%;" />，代表放大器增益的大小

​		（2）开环增益：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230825145147509.png" alt="image-20230825145147509" style="zoom:50%;" /> = A~0~

​		（3）**环路增益：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230825145224947.png" alt="image-20230825145224947" style="zoom:50%;" /> = A~0~ * β**，==**决定增益的精度**==

​		（4）H(S) 处理的信号依然是小信号（由于整个电路的输入信号和反馈回来的信号均为大信号，两者做差输入放大器时依然为小信号）

> 开环增益求解：将电路的反馈通路打断，将断点接固定电位（一般为地），再求V~out~/V~in~即为开环增益

> 环路增益求解：**输入端接地**，将电路的反馈通路打断得到两个断点，在断点处接电压源V~t~，另一个断点处为V~f~，再求V~t~/V~f~即为环路增益

> 闭环增益求解：将计算得到的开环增益和环路增益代入<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230921163658105.png" alt="image-20230921163658105" style="zoom:50%;" />，即可得到

- 反馈电路的特性：

1. 增益灵敏度降低：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230825150839707.png" alt="image-20230825150839707" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230825150905117.png" alt="image-20230825150905117" style="zoom:50%;" />

注：A 很大但对于环境因素比较敏感；A~CL~（即闭环增益）对于环境不太敏感。

> ==如何求环路增益==：
>
> <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230825151815578.png" alt="image-20230825151815578" style="zoom:50%;" />
>
> （1）输入接小信号地
>
> （2）对于理想模型，在任意一点断开，并接入一个电压源V~t~，此时的环路增益 = V~f~/V~t~<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230825151715767.png" alt="image-20230825151715767" style="zoom:50%;" /><img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230825151736678.png" alt="image-20230825151736678" style="zoom:50%;" />
>
> 主要难点：找到实际电路中的放大电路（A）和反馈电路（β）

2. 终端阻抗的变化：

例：  （输入电阻）                          <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230825163633689.png" alt="image-20230825163633689" style="zoom:50%;" />

求开环输入电阻：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230825163711023.png" alt="image-20230825163711023" style="zoom:50%;" /><img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230825163734247.png" alt="image-20230825163734247" style="zoom:50%;" />

求闭环输入电阻：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230825163803616.png" alt="image-20230825163803616" style="zoom:50%;" /><img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230825164846369.png" alt="image-20230825164846369" style="zoom:50%;" />

例：（输出电阻）<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230825164336612.png" alt="image-20230825164336612" style="zoom:50%;" /><img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230825164444085.png" alt="image-20230825164444085" style="zoom:50%;" />

![image-20230825164738261](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230825164738261.png)

> 结论：==闭环 = 开环 /（1 + 环路）==

3. 带宽改变：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230825165603702.png" alt="image-20230825165603702" style="zoom:50%;" />

结论：**利用反馈可以增大信号带宽，但同时会减小增益，最终增益带宽积不变。**

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230825165831636.png" alt="image-20230825165831636" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230825165855230.png" alt="image-20230825165855230" style="zoom:50%;" />

反馈改变速度

例：将一个20MHz的矩形波增益100倍

​		方法一：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230825170857926.png" alt="image-20230825170857926" style="zoom: 50%;" />

注：当输入的矩形脉冲变形为上述形状时，表明通路带宽不够，故需要增大带宽；如何计算通路带宽，以及带宽和时间常数的关系如上图所示。

> 时间常数*τ* = RC = 1/*ω*(角频率) = 1/2*π*f

​		方法二：使用两级放大器级联

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230825171559647.png" alt="image-20230825171559647" style="zoom:50%;" />

4. 抑制非线性：开环放大器的非线性很严重，闭环后改善非线性，并有“虚短”的现象（可以通过检测放大器输入端两个电压的大小是否相等（即虚短）来判断放大器是否正常工作）。

- 放大器的种类：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230825190417130.png" alt="image-20230825190417130" style="zoom:50%;" />

> 电压入：输入端阻抗很高；电流入：输入端阻抗很低；
>
> 电压出：输出端内阻很低；电流出：输出端内阻很高；

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230825190257741.png" alt="image-20230825190257741" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230825214249502.png" alt="image-20230825214249502" style="zoom:50%;" />

> 电压相加：差动对（两个输入信号相减）；利用V~GS~（V~GS~ = V~G~ - V~S~）

### 8.2 反馈结构

1. VVF：（放大电路的输出为电压，反馈电路的输出为电压）

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230825214825509.png" alt="image-20230825214825509" style="zoom: 50%;" />

对于反馈网络的要求：在电路输出端并联接入；在输入端串联接入；大输入电阻，小输出电阻；

> 此类型的前路放大器的输入输出信号均为电压，故增益为无量纲的常数；反馈网络的输入输出均为电压，故增益为无量纲的常数。

- 闭环增益：

​                                  <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230825215134813.png" alt="image-20230825215134813" style="zoom: 33%;" />                      <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230825215158503.png" alt="image-20230825215158503" style="zoom:33%;" />                                   

- 输出电阻计算：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230825220131450.png" alt="image-20230825220131450" style="zoom: 33%;" />

- 输入电阻计算：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230825220432855.png" alt="image-20230825220432855" style="zoom:33%;" />

>结论：对于VVF，对输入电阻是增加，对输出电阻是减小（增加或减小的倍数都是（![image-20230826102919514](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230826102919514.png)）倍数)；判断反馈类型，求解环路增益。

> 对于VVF的闭环输入输出电阻的变化：==**好上加好**==（闭环输入电阻更大，闭环输出电阻更小）

2. CVF：（放大电路的输出为电流，反馈电路的输出为电压）

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230826103107481.png" alt="image-20230826103107481" style="zoom:50%;" />

​		其中的反馈网络是一个跨导放大器，对于反馈网络的要求：在电路输出端串联接入；在输入端串联接入；小输出电阻；小输入电阻。

> 此类型的前路放大器中输入信号是电压，输出是电流，故增益为跨导；而反馈网络的输入信号是电流，输出是电压，故增益为电阻。

- 闭环增益：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230826104118286.png" alt="image-20230826104118286" style="zoom: 33%;" />

- 环路增益：将输入短路，环路断开，接入一个电流源

​                                                       <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230826104623508.png" alt="image-20230826104623508" style="zoom:33%;" /><img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230826104754992.png" alt="image-20230826104754992" style="zoom:50%;" />

​		注：环路增益 = 电导 * 电阻 = 无量纲的常数

- 输入输出电阻计算：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230826105032423.png" alt="image-20230826105032423" style="zoom: 33%;" />

> 实际中参考电流的产生电路：参考电压接一个运放再接一个MOS管得到参考电流![image-20230826112107012](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230826112107012.png)

3. VCF：（输出电压，反馈电流）

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230826112446519.png" alt="image-20230826112446519" style="zoom:33%;" />

​		对于反馈网络的要求：在电路输出端并联接入；在输入端并联接入；小输出电阻；大输入电阻。

- 闭环增益：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230826112741942.png" alt="image-20230826112741942" style="zoom: 33%;" />

- 输入电阻和输出电阻计算：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230826112900778.png" alt="image-20230826112900778" style="zoom: 33%;" />

4. CCF：（输出电流，反馈电流）

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230826112953484.png" alt="image-20230826112953484" style="zoom:50%;" />

​		对于反馈网络的要求：在电路输出端串联接入；在输入端并联接入；大输出电阻；小输入电阻。

- 闭环增益：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230826113108271.png" alt="image-20230826113108271" style="zoom:33%;" />

- 输出输出电阻：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230826113129130.png" alt="image-20230826113129130" style="zoom:33%;" />

5. **==总结：==**

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230826113233217.png" alt="image-20230826113233217" style="zoom:50%;" />

### 8.3 反馈对噪声的影响

​		反馈对噪声的改善不大。

### 8.4 反馈分析的困难

- 通用分析步骤：

​		（1）识别反馈类型

​		（2）打断环路：计算开路增益，输入输出电阻

​		（3）计算环路增益

​		（4）得到闭环参数

​		（5）使用环路增益判断电路稳定性

​		困难一：加载效应（负载效应）

​		由于反馈网络的非理想输入输出阻抗导致的“负载效应”，（当输入输出阻抗是理想的时候，打破环路的断点随意取即可），当“负载效应”存在时，断点的选取就有所不同，选错断点，分析就错。

​		困难二：无法将电路清晰的分解为前馈放大器和反馈网络

​		困难三：有的电路很难归类为标准类型

​		困难四：环路不止一个

​		困难五：多重反馈机制

- 二端口网络方法解决加载效应

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230826145648331.png" alt="image-20230826145648331" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230826150153442.png" alt="image-20230826150153442" style="zoom:50%;" />

例：使用G模型进行二端口网络分析解决加载效应的影响

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230826195537611.png" alt="image-20230826195537611" style="zoom:50%;" />

​		选定反馈网络，打断环路：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230826195231449.png" alt="image-20230826195231449" style="zoom: 67%;" />

> 将反馈网络断开，并将反馈网络完整copy一份，
>
> 计算g~11~：将反馈网络输出端悬空；
>
> 计算g~22~：将反馈网络的输入端接地；
>
> <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230826195818237.png" alt="image-20230826195818237" style="zoom:50%;" />

​		根据电流电压关系可得开环增益为：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230826200454274.png" alt="image-20230826200454274" style="zoom:50%;" />

​		计算闭环增益：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230826200651253.png" alt="image-20230826200651253" style="zoom:50%;" />

​		其中g~21~计算：将I~2~ = 0（即输出开路），随后  <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230826200807149.png" alt="image-20230826200807149" style="zoom:50%;" />

​		得到：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230826200838594.png" alt="image-20230826200838594" style="zoom: 50%;" />

## 第9章 运算放大器

​		本章目的：讨论CMOS运放的分析与设计

### 9.1 概述

​		对于电压输入的放大器主要有两种：运算放大器（Opamp）和运算跨导放大器（OTA）

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230827182553935.png" alt="image-20230827182553935" style="zoom: 50%;" />

​		注：其中OTA输出电阻大，适合用作电流输出型放大器，但实际应用也有将其作为电压输出型，只用接一个比内阻大的多的负载即可实现（例如OTA常作为电压输出型驱动MOS管的栅极，栅极的输入阻抗理论上是无穷大的）。

> Opamp，运算放大器，电压输出型，输出电阻为0；
>
> OTA，跨导放大器，电流输出型，输出电阻为∞。

> **放大器电压输出型和电流输出型的区别与联系：**当放大器的内阻r~o~较小时（即外接的R~L~ >> r~O~）适合使用电压输出型（电阻串联分压），当放大器的内阻r~o~较 大时（即外接的R~L~ << r~O~）适合使用电流输出型（电阻并联分流）
>
> ![image-20230827191534266](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230827191534266.png)

- 性能参数：

  增益；

  小信号带宽；

  <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230827193802274.png" alt="image-20230827193802274" style="zoom:50%;" />

  其中单位增益频率点 f~u~ = A~0~（= 1） * f~-3dB~ = 增益带宽积（GBW）。

  注：A~0~决定了放大器的精度，A~0~ * ω 决定了放大器的速度。

  大信号带宽；

  输出信号摆幅；

  线性度；

  噪声；偏置；

  电源抑制。

### 9.2 单极放大器

​		差动放大器均称为运放。

1. 差动对

- 有源电流镜驱动的差动放大器

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230827202003403.png" alt="image-20230827202003403" style="zoom:50%;" />

 <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230827204851507.png" alt="image-20230827204851507" style="zoom:50%;" />

> ==**单极点近似**==：一个放大器系统含有多个极点，当只有一个极点位于单位增益频率点的左边（即只有一个极点频率小于单位增益频率），其他的极点均位于单位增益频率点的右边。
>
> 优点：（1）单位增益频率 ω~u~ 可以尽可能的大；（因为ω通过一个极点频率时以20dB/dec下降（频率每增加十倍，对应的幅值减小20dB））（2）系统更加稳定。

- 电流源负载的全差动对

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230827203229796.png" alt="image-20230827203229796" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230827204924830.png" alt="image-20230827204924830" style="zoom:50%;" />

- 设计步骤：

**（0）根据运放的速度以及负载的大小，计算出GBW的值，GBW = g~m~/C~L~，计算出输入管的g~m~；g~m~ = 2I~D~ / V~OD~**

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230827204447112.png" alt="image-20230827204447112" style="zoom:50%;" />

​		注：设计步骤是从运放的速度和范围开始。

> 差动对的增益太低，故引出了共源共栅

2. 共源共栅极OTA

- 单端输出cascode OTA

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230828103849440.png" alt="image-20230828103849440" style="zoom:50%;" />

​		缺点：V~out,DC~太小了，限制了电路的输出摆幅。

- 宽摆幅单端输出cascode OTA

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230828111224855.png" alt="image-20230828111224855" style="zoom:50%;" />

​		结论：采用低压共源共栅的电路虽然偏置更加复杂一点（需要单独对M~5~和M~6~进行偏置）但可以获得更大的输出摆幅。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230828111956907.png" alt="image-20230828111956907" style="zoom:50%;" />

- 全差动cascode OTA

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230828112510645.png" alt="image-20230828112510645" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230828112545798.png" alt="image-20230828112545798" style="zoom: 50%;" />

###### 例：==运放整个设计流程==

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230828145140680.png" alt="image-20230828145140680" style="zoom:50%;" />

> 1，总电流 = 总功耗 / 供电电压；随后将电流进行分配，分配给每个支路（需要经验）
>
> 2，根据输出摆幅分配V~OD~，题中V~OD9~设为0.5V，原因是M~9~是尾电流管，需要流过的电流较大，通过增大V~OD~可以增大流过其中的电流（否则只能通过增大宽长比的方式，但增大宽长比后会花费更多的面积）（需要经验）

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230828145310882.png" alt="image-20230828145310882" style="zoom:50%;" />

> 3，每个管子的过驱动电压V~OD~和电流I~D~均已知，可以直接计算出每个管子的宽长比；如何确定宽和长的具体值呢？原则是可以先将管子的长L设为工艺的最小值（减小管子的尺寸，同时管子的寄生电容也越小，会使小信号带宽更大）

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230828145520938.png" alt="image-20230828145520938" style="zoom:50%;" />

> 4，计算增益，将结果与要求比较，进行相应的调整（不一定需要对所有的管子进行修改，找到短板进行相应的修改即可）

- 单位增益共源共栅

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230828150821035.png" alt="image-20230828150821035" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230828150844684.png" alt="image-20230828150844684" style="zoom:50%;" />

- 线性缩放：当其他参数需要保持不变，只有功率预算不同时：

  例：需要功耗加倍，所有MOS管的宽度加倍，长度不变

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230828151420438.png" alt="image-20230828151420438" style="zoom:50%;" />

> 共源共栅极由于输入输出相互限制，导致了输出摆幅不够大

3. 折叠型的cascode OTA

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230828183504960.png" alt="image-20230828183504960" style="zoom: 33%;" /><img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230828183528767.png" alt="image-20230828183528767" style="zoom:33%;" />

> ==折叠：将输入MOS管的类型变换一下，类型转换之后没有了对地的通路，此时需要添加一个电流源。==
>
> ==优点：将输入V~in~和输出V~out~隔离开，解决共源共栅由于输入输出相互限制导致输出摆幅太小的问题。==
>
> [4. 折叠cascode运算放大器-CSDN博客](https://blog.csdn.net/qq_41424881/article/details/132890037)
>
> ![image-20231120193421376](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231120193421376.png)
>
> 折叠结构中晶体管M1和M2获得相当的性能，就要满足I2=|ID1|+|ID2|。所以折叠结构的代价就是增加了功耗。

- 差动折叠cascode OTA

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230828184243913.png" alt="image-20230828184243913" style="zoom:50%;" />

- 全差动折叠cascode OTA

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230828184441098.png" alt="image-20230828184441098" style="zoom:50%;" />

​		注：输出摆幅增大

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230828184559399.png" alt="image-20230828184559399" style="zoom:50%;" />

​		注：输出增益减小

### 9.3 两级运放

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230828185443966.png" alt="image-20230828185443966" style="zoom:50%;" />

例：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230828190255732.png" alt="image-20230828190255732" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230828190446850.png" alt="image-20230828190446850" style="zoom:50%;" />

​		优点：非常大的增益，中等功耗；缺点：稳定性问题；第二级的静态工作点不容易设置

> 对于稳定性问题的说明：对于一级放大器来说，高阻抗极点只有一个（在输出端节点，由于输出电阻很大，导致输出极点频率较小），所以很容易实现单极点近似；而对于二级运放系统来说，高阻抗极点有两个（每一级放大器各一个），不利于稳定。

通过对第一级电路进行优化可以获得更大的增益：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230828192226746.png" alt="image-20230828192226746" style="zoom:50%;" />

​		注：在运放设计时，当输出摆幅范围是V~DD~ - V~OD~ 到 V~OD~ 时，此类运放可以被称作轨对轨运放。

### 9.4 增益的提高

​		A~V~ = g~m~ * r~out~ ；想要提高增益，最好方式就是增大输出电阻r~out~。

​		通过哪种方式增大输出电阻呢？可以采用**电流反馈**的方式实现输出电阻的增大。

- 调节型共源共栅

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230828204139757.png" alt="image-20230828204139757" style="zoom:50%;" />

​		注：电路中的r~o1~是一个共源极MOS管的小信号等效。

> 其中M~2~和r~o1~两者构成一个负反馈，得到共源共栅的高增益，在X点接入一个运放相当于在共源共栅的反馈环路中增加一个放大单元，使得闭环路增益更大

​		环路增益：其中M~2~管和r~o1~构成的共源共栅等效于一个源极跟随器增益≈ 1，故整体电路的环路增益<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230828204537625.png" alt="image-20230828204537625" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230828204606352.png" alt="image-20230828204606352" style="zoom:50%;" /> ，由于A~1~ 远大于1，故<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230828204724866.png" alt="image-20230828204724866" style="zoom:50%;" />

> 介绍两个电路的不同：直流工作点不同。
>
> ​               <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230828210549970.png" alt="image-20230828210549970" style="zoom:50%;" />               <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230828210609800.png" alt="image-20230828210609800" style="zoom:50%;" />    
>
> 电路一：计算M~1~中的电流时不需要知道M~1~的栅极电压，它是一个被动管，其中的电流由R~S~决定，其中R~s~用于产生直流电流，<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230828210858403.png" alt="image-20230828210858403" style="zoom: 50%;" />
>
> 电路二：此结构中的电流大小由偏置管中的电流I~D~决定，M~2~与M~1~共同构成放大器

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231005101534390.png" alt="image-20231005101534390" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230828212543669.png" alt="image-20230828212543669" style="zoom:50%;" />

> 将左图中的r~o1~使用M~1~替换，与M~2~构成共源共栅，由于M~2~与A~1~一起后的等效电阻远远小于M~1~的输出电阻r~o1~，故V~in~输入后的电流几乎全部向上流过M~2~管，故右边的电路就是一个以M~~2~和A~1~共同构成的负载的共源极放大电路。

实际电路实现上述“超级晶体管”：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230829154354536.png" alt="image-20230829154354536" style="zoom: 50%;" />

​		注：可见增益确实增大了，但输出范围减小了（V~X~ = V~OD~ 时不影响输出摆幅）。

​		可以使用PMOS管来增大输出摆幅（增大增益，并且不影响输出摆幅）：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230829160151926.png" alt="image-20230829160151926" style="zoom:50%;" />

> 直接使用PMOS管后，由于V~DD~和P点的压差很大，所以消耗的电流I~1~很大。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230830085203255.png" alt="image-20230830085203255" style="zoom:50%;" />

### 9.5 共模反馈（CMFB）

> CMFB的两种类型：
>
> 连续时间CMFB（CT-CMFB）：两个电阻即可
>
> 开关电容（ST-CMFB）：用时钟信号控制开关开断

- 全差动运放的优缺点：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230830092605125.png" alt="image-20230830092605125" style="zoom: 50%;" />

> <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231005110345934.png" alt="image-20231005110345934" style="zoom:50%;" />
>
> 单端输出的共模电平是固定的<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231005110429889.png" alt="image-20231005110429889" style="zoom:50%;" />
>
> 全差动中由于上面两个管子的源极和栅极都接直流电源，故等效为电流源，在工作的时候会与尾电流源产生冲突，导致输出的共模电平无法确定

其中对于差动放大器的共模电平的问题，**只有“一山不容二虎”的情况（电路中有两个电流源导致电流冲突，如负载是电流源）下才会需要共模电平和共模反馈**。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230830094225626.png" alt="image-20230830094225626" style="zoom:50%;" />

注：差动放大器中的共模是指当输入信号还没有加入差动值，只加了一个共模电平，输出端如何获得一个确定的共模电压。当电路中存在电流冲突时，输出端的共模电压会不稳。

- 通过共模反馈将共模电平固定下来：

> 由于是两个电流源的冲突导致"一山不容二虎"的情况，故共模反馈的核心思想就是将其中的“一只虎”变弱

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230830102206142.png" alt="image-20230830102206142" style="zoom:50%;" />

​		注：其中的运放是低增益放大器

共模反馈实现例：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230830103922941.png" alt="image-20230830103922941" style="zoom:50%;" />

​		使用两个电阻实现共模电压的检测，但要求两个电阻的阻值很大才可以对差动电路输出影响减小，但阻值一大，电阻的面积就需要很大，不利于集成，故使用两个源跟随器以此减小两个电阻的阻值及面积；新的问题又出现，M~7,8~源随器正常工作允许的V~out1,2~的大小和主电路允许的大小范围不同，即**共模检测电路的差模输入范围和主放大器的差模输出范围不匹配，故导致共模检测出现失真**。

### 9.6 输入范围限制

> 想要扩展输入的范围：使用双折叠
>
> 想要扩展输出的范围：使用class-AB

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230830110847010.png" alt="image-20230830110847010" style="zoom:50%;" />

### 9.7 转换速率（压摆率）

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230830112555002.png" alt="image-20230830112555002" style="zoom:50%;" />

​		当输入突然增大，不管输入增大多少，输出会经过相同的时间变化至稳定。

​		对于RC电路来说上面一句话成立，但对于运放来说，情况不同。

1. 输入信号变化较小时，输出呈指数形式增大变化。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230830112835580.png" alt="image-20230830112835580" style="zoom:50%;" />

2. 输入信号变化较大时，输出呈线性变化，其中线性的斜率为<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230830113053219.png" alt="image-20230830113053219" style="zoom:50%;" />。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230830113027399.png" alt="image-20230830113027399" style="zoom:50%;" />

注：例子中当输入变化太大，I~ss~中的电流不够M~1~和M~2~两个管子分配的，故导致输出变化呈线性。

​		一个电路的压摆率限制了可以处理的信号的最大斜率：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230830113412432.png" alt="image-20230830113412432" style="zoom:50%;" />

### 9.8 电源抑制

电源抑制就是指电路中电源中的波动到达输出点的增益需要抑制。

电源抑制比 = 从电源上到输出端的小信号增益 / 有用的差模值

## 第10章 稳定性与频率补偿

### 10.1 概述

​		负反馈系统中的稳定性问题：负反馈系统的优点参看第8章开头，负反馈系统的缺点：有可能出现系统不稳定的问题（在运放系统中，不稳定是指将运放接为闭环后，没有输入或输入一个直流，但输出为一个振荡的信号）；有可能产生振荡。

- 不稳定问题在时域中的解释

​		输入为直流时的负反馈：输出是一个被放大了的直流，运放两个输入端的压差（V~in+~ - V~in-~）很小

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230830211844524.png" alt="image-20230830211844524" style="zoom:50%;" />

​		输入信号带有频率时的负反馈：只考虑系统输出信号与输入信号直接的相位延迟，可以看出随着输入信号的频率不断增加，相位延迟不断增大，直至某一个频率时会有<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230830212357721.png" alt="image-20230830212357721" style="zoom:50%;" />，即负反馈变为正反馈，此时容易产生自激振荡的现象，此时输出会固定在此频率，并且幅值不断增大。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230830212244402.png" alt="image-20230830212244402" style="zoom:50%;" />

​		注：

1. 相位延迟 = <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230830212555261.png" alt="image-20230830212555261" style="zoom: 33%;" />，ΔT是器件延迟，是固定的，但随着信号的频率的增大，ΔT相对于信号周期所占的比重越来越大，即相位延迟越来越大。

2. 并不是只要不输入某个会导致正反馈频率的信号就不会产生正反馈，当运放供电时（输入信号相当于一个方波，含有丰富的各次谐波），输入信号的波动，噪声等因素都可能会产生振荡，导致正反馈。

3. 为啥只有一个<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230830212357721.png" alt="image-20230830212357721" style="zoom:50%;" />的延迟，负反馈就可能会直接变为正反馈？因为负反馈的输入输出端为V~in+~ - V~in-~，天生自带一个<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230830212357721.png" alt="image-20230830212357721" style="zoom:50%;" />的延迟，再加上特殊频率导致的延迟，共2<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230830212357721.png" alt="image-20230830212357721" style="zoom: 33%;" />，所以负反馈直接变为正反馈。

- 不稳定问题在频域中的解释：巴克豪森准则

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230831080909645.png" alt="image-20230831080909645" style="zoom:50%;" />

​	系统函数的分母为0，则系统增益无穷大，故当有一个频率的信号输入，使得闭环增益幅值为1，相移180°，就会产生振荡。

> 注：**系统中的β越小，系统越稳定，反馈系统β的最大值为1。**

​		稳定系统和不稳定系统：

​		根据==环路增益的波特图判断==

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230831082550229.png" alt="image-20230831082550229" style="zoom:50%;" />

> 其中GX（增益交点）是指==环路增益==为0dB（即单位增益）的点；PX（相位交点）是指相位为 -180° 的点

​		闭环系统的极点与系统稳定性：收敛域包含虚轴（即闭环系统函数的根在虚轴左侧）

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230831083226953.png" alt="image-20230831083226953" style="zoom:50%;" />

例；<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230831083529186.png" alt="image-20230831083529186" style="zoom: 33%;" />单极点系统最大相移为90°，故肯定为稳定系统。

### 10.2 多极点系统

用两极点系统举例：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230831085018678.png" alt="image-20230831085018678" style="zoom:50%;" />

结论：

1. 对于多极点系统，采用闭环增益的波特图分析，寻找GX点和PX点进行比较。
2. 系统的反馈越弱，即β越小，系统越稳定（幅度波特图中的灰色线条，此时GX变小，离PX越来越远），最坏的情况（β最大）β = 1（即单位增益反馈）
2. 没有零点的两极点系统总是稳定的

### 10.3 相位裕度

​		相位裕度（PM）是指GX的点所对应的相位值和PX之间的相位差。

例：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230831090058775.png" alt="image-20230831090058775" style="zoom:50%;" />

​		系统相位裕度 = 5°时，闭环增益在频域中出现了peaking现象（峰值现象），低频增益和高频增益不同会导致输出信号失真；在时域中出现ring现象，输出不断振荡，经过一段时间后才稳定下来，降低了系统的响应速度。

> 闭环系统虽然是稳定的，但是由于==相位裕度不够==，导致闭环增益在接近带宽附近会出现了==peaking现象==；在时域出现==ring现象==。

当相位裕度足够时的现象：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230831091001989.png" alt="image-20230831091001989" style="zoom:50%;" />

- 相位裕度需要多少合适？

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230831092310573.png" alt="image-20230831092310573" style="zoom:50%;" />

​		==**相位裕度范围：63°~72°**==

> 对于一个两极点系统：
>
> <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230831093055138.png" alt="image-20230831093055138" style="zoom:50%;" />

> <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231005210622475.png" alt="image-20231005210622475" style="zoom:50%;" />
>
> 其中*ω*~1~是系统的主极点（一般是系统的输出极点），*ω*~u~是单位增益点（*ω*~u~ = g~m~ / C~L~），*ω*~2~是寄生极点（由系统的寄生电容产生）；在设计运放时，一般先确定*ω*~u~，为了保证系统的稳定，需要将*ω*~2~的值设置为*ω*~u~的2~3倍（此时相位裕度为63度至72度之间）
>
> 故对于一个两极点系统，稳定与否主要取决于*ω*~2~的极点，所以最主要的工作是设计*ω*~2~的值（寄生极点的调整需要经验）

### 10.4 频率补偿

​		主要就是改变极点频率，目标是达到单极点近似。

- 单端输出的套筒式OTA

频率补偿的方式：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230831135106985.png" alt="image-20230831135106985" style="zoom:50%;" />

​		方式一减少极点的个数，极点的个数是由电路结构决定的（一个结点贡献一个极点），故不太容易；方式二通过改变β，实现减小GX，而保持PX不动；方式三移动主极点频率。

> **β越小，信号裕度越大。**
>
> <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230831135436771.png" alt="image-20230831135436771" style="zoom:50%;" />

> 阻抗经验：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230831135856207.png" alt="image-20230831135856207" style="zoom:50%;" />
>
> 其中1/g~m~的情况（低电阻结点）：MOS管源极电阻、二极管连接型器件电阻
>
> 其中r~o~的情况（高电阻结点）：MOS管漏极电阻、单一电流源
>
> **单极运放**：只有一个高电阻结点的运放电路

​                   <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230831141307755.png" alt="image-20230831141307755" style="zoom:50%;" />                 <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230831141340460.png" alt="image-20230831141340460" style="zoom:50%;" />

​		注：主频率极点在输出端（输出端的输出电阻最大）；A极点关联的MOS管最多（3管，5管，6管），故寄生电容最大，故选为次极点。

​		**多个极点在GX左侧，系统不稳定，需要进行频率补偿：移动主极点频率实现**<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230831142327644.png" alt="image-20230831142327644" style="zoom:50%;" />

​		==通过增大输出电容C~L~来移动主极点频率，主要依据：波特图中一个极点的斜率为 -20dB/dec。==

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230831142916180.png" alt="image-20230831142916180" style="zoom:50%;" />

​		**先找到次极点的频率，再通过 -20dB/dec的斜率反推出移动后的主极点频率值*ω*~out~'，通过计算得到C~L~’的值。**

> ==如何根据波特图计算相位裕度：==
>
> <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230831145330269.png" alt="image-20230831145330269" style="zoom: 33%;" />
>
> <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230831150003909.png" alt="image-20230831150003909" style="zoom: 67%;" />

- 全差动套筒式OTA

​		频率特性很好，并且比单端输出的OTA更加稳定，速度更快

### 10.5 两级运放的补偿

​		两级运放较难进行频率补偿，例如

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230901080209901.png" alt="image-20230901080209901" style="zoom:50%;" />

​		两级运放各贡献一个高阻抗的低频结点，且两个结点频率相近，<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230901080322395.png" alt="image-20230901080322395" style="zoom:33%;" />，想要通过加大电容移动主极点频率的方法不可行。

- 米勒补偿：在第二级放大器的输入和输出之间并联跨接一个电容

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230901081443357.png" alt="image-20230901081443357" style="zoom:50%;" />

​		结果：第一级的输出结点的频率显著降低（由于米勒补偿的作用，**借助第二级放大器的增益，把第一级放大器输出结点的电容放大**），第二级的输出结点的频率显著增大（即将两个频率相近的结点的频率拉开）

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230901082716539.png" alt="image-20230901082716539" style="zoom:50%;" />

​		由于增加电容之后多出一条信号通路，故多了一个右半平面的零点。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230901083829836.png" alt="image-20230901083829836" style="zoom:50%;" /><img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230901083924037.png" alt="image-20230901083924037" style="zoom:50%;" />	

​		由于位于右半平面零点的作用，使得相位裕度变为负数，电路不稳定，会产生振荡。

- 如何解决掉由于米勒补偿带来的右半平面的零点？

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230901085128939.png" alt="image-20230901085128939" style="zoom:50%;" />

​		给米勒电容串联一个电阻，通过分析，可以通过改变电阻的大小使得零点消失或者移动至左半平面。

> 理论上可以将零点完全抵消，但由于PVT等因素的影响，会导致电路产生波动，计算好的零点抵消可能会变为右半平面的零点，故完全抵消实际不太可行

电阻R~Z~的确定：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230901085724204.png" alt="image-20230901085724204" style="zoom:50%;" />

​		方式一不靠谱；方式二将零点移动至左半平面，并减小主极点频率的值。

> 可以使用一个MOS管当作一个压控电阻，更方便准确的调控电阻阻值
>
> <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230901085952254.png" alt="image-20230901085952254" style="zoom:33%;" />

> 不同负载电容对于一级运放和两级运放的影响：
>
> <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230901090302287.png" alt="image-20230901090302287" style="zoom:50%;" />
>
> 对于一级运放，随着负载电容的不断增大，输出会越来越稳定，但响应时间会越来越长；对于两级运放，随着负载电容的不断增大，输出会越来越不稳定，可能会产生振荡（由于第二级运放的输出结点频率是次极点，随着负载电容不断增大，次极点频率会减小，与主极点频率接近）

###### ==总结：两级运放的设计过程==

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230901104917364.png" alt="image-20230901104917364" style="zoom:50%;" />

​		两级运放的主极点是在第一级运放的输出极点，次极点是在第二级运放的输出极点。

## 第12章 带隙基准

​		本章目的：CMOS技术中基准产生电路的设计，着重于“带隙”技术。

### 12.1 概述

​		产生基准的目的是建立一个与电源和工艺无关、具有确定温度特性的直流电压或电流。将任务分为两个设计问题：与电源无关的偏置和温度变化关系的确定。

### 12.2 与电源无关的偏置

​		之前使用电流镜时，是通过“复制”的方式将一个“理想的”基准电流输入电路中使用，此时的问题是如何产生这个理想的基准电流？

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230902203929297.png" alt="image-20230902203929297" style="zoom:50%;" />

​		通过用一个电阻作为近似电流源，但输出电流对V~DD~很敏感：<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230902204123136.png" alt="image-20230902204123136" style="zoom:50%;" />

​		目前的想法是消除对V~DD~的敏感，假定电路必须要自己偏置（即**I~ref~需通过某种方式从I~out~得到**）：如果I~out~最终与V~DD~无关，那么I~ref~就可以是I~out~的一个复制。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230902205615382.png" alt="image-20230902205615382" style="zoom:50%;" />

​		通过两个PMOS管将I~out~复制成为I~ref~，

​		注：每个二极管连接型器件都是由一个电流源驱动，故相对来说I~out~和I~ref~与V~DD~无关

### 12.3 与温度无关的基准

​		如何产生一个对温度变化保持恒定的量？将两个具有相反温度系数的量以适当的权重相加，结果就会显示出零温度系数。

​		双极晶体管的特性参数具有良好的重复性，并具有提供正温度系数和负温度系数的、严格定义的量。

- 负温度系数电压

​		双极性晶体管的基极-发射极电压，或者说pn结二极管的正向电压具有负温度系数。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230902211533323.png" alt="image-20230902211533323" style="zoom: 50%;" />

​		V~BE~的温度系数本身与温度有关，如果正温度系数的量表现出一个固定的温度系数，那么在恒定基准的产生电路中就会产生误差。

- 正温度系数电压

​		当两个双极性晶体管工作在不同的电流密度下，他们的基极-发射极电压的差值就与绝对温度成正比。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230902212100902.png" alt="image-20230902212100902" style="zoom:50%;" />

​		                                          <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230902212156254.png" alt="image-20230902212156254" style="zoom:50%;" />                     <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230902212210143.png" alt="image-20230902212210143" style="zoom: 67%;" />

​		此温度系数与温度或集电极电流的特性无关。

- 带隙基准

