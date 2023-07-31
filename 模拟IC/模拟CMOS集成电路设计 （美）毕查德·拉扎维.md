## 第2章 MOS器件物理基础

​		本章目的：通过对器件工作状态的解析描述来为每个器件建立电路模型

### 2.1 MOS晶体管的结构

![image-20230728152238973](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230728152238973.png)

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

​		其中V<sub>GS</sub>-V<sub>TH</sub>称为**“过驱动电压”**。

​		当**V<sub>DS</sub> << 2(V<sub>GS</sub>-V<sub>TH</sub>)**，可得

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230729103804082.png" alt="image-20230729103804082" style="zoom: 33%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230729104152613.png" alt="image-20230729104152613" style="zoom:33%;" />

​		此时器件工作在**深三极管区**，MOSFET可看作一个**线性压控可变电阻**，电阻值为

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230729104049857.png" alt="image-20230729104049857" style="zoom:33%;" />

- 饱和区

​		当**V<sub>DS </sub> > V<sub>GS</sub>-V<sub>TH</sub>**时，I<sub>D</sub>相对恒定。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230729144551892.png" alt="image-20230729144551892" style="zoom:50%;" />

- 夹断区

​		如果**V<sub>DS</sub> 略大于V<sub>GS</sub>-V<sub>TH</sub>**，则反型层将在x ≤ L处终止，称为沟道被夹断。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230729144841457.png" alt="image-20230729144841457" style="zoom: 50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230729144948228.png" alt="image-20230729144948228" style="zoom:50%;" />

> 总结：
>
> <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230729145809520.png" alt="image-20230729145809520" style="zoom: 33%;" />
>
> V<sub>GS</sub> > V<sub>TH</sub>时：V<sub>DS </sub> > V<sub>GS</sub>-V<sub>TH</sub>对应饱和区；V<sub>DS </sub> < V<sub>GS</sub>-V<sub>TH</sub>对应线性区；
>
> 工作在饱和区所需的最小的V<sub>DS</sub>也称为V<sub>D,sat</sub>，V<sub>D,sat</sub> = V<sub>GS</sub>-V<sub>TH</sub>

- MOSFET的跨导

​		跨导 = 漏电流的变化量 ➗ 栅源电压的变化量（通常定义在饱和区）

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230729152206131.png" alt="image-20230729152206131" style="zoom: 33%;" />

​		g<sub>m</sub>单位是1/Ω 或西门子（S）。

​		饱和区的g<sub>m</sub>值等于深三极管区R<sub>on</sub>的倒数。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230729152440090.png" alt="image-20230729152440090" style="zoom:33%;" />

### 2.3 二级效应

- 体效应：MOS管的阈值电压将随其源极和衬底之间电位的不同而发生变化

​		随着V<sub>B</sub>的下降，Q<sub>d</sub>增加，V<sub>TH</sub>也增加。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230729155436343.png" alt="image-20230729155436343" style="zoom:50%;" />

​		在考虑体效应后，

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230729155617269.png" alt="image-20230729155617269" style="zoom: 33%;" />

​		其中<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230729155741035.png" alt="image-20230729155741035" style="zoom:25%;" />称为体效应系数，V<sub>SB</sub>是源衬电势差。γ的典型值在0.3V<sup>1/2</sup>到0.4V<sup>1/2</sup>之间。

​		产生体效应，并不需要改变衬底电势V<sub>sub</sub>：源电压相对于V<sub>sub</sub>发生改变，会产生同样的现象。

例如：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230729161245558.png" alt="image-20230729161245558" style="zoom: 33%;" />

> 体效应的存在会导致阈值电压的改变

- 沟道长度调制

​		**此效应发生在饱和区**，沟道长度L`是V<sub>DS</sub>的函数（从式2.13可得）。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230729161328814.png" alt="image-20230729161328814" style="zoom:33%;" />

> 沟道长度调制的存在导致I<sub>DS</sub>/V<sub>DS</sub>特性曲线在饱和区出现非零斜率，使D和S之间的电流源非理想。

> 沟道长度加倍，会使I<sub>D</sub>~V<sub>DS</sub>曲线的斜率减为原来的1/2

- 亚阈值导电性

​		V<sub>GS</sub> ≈ V<sub>TH</sub>时，器件不会突然关断，一个“弱”的反型层仍然存在，甚至当V<sub>GS</sub> < V<sub>TH</sub>时，I<sub>D</sub>也并非无限小，而是与V<sub>GS</sub>呈指数关系。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730090545296.png" alt="image-20230730090545296" style="zoom:50%;" />

### 2.4 小信号模型

#### 2.4.1 MOS器件版图

![image-20230730091400780](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730091400780.png)

例如：

![image-20230730091509154](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730091509154.png)

#### 2.4.2 MOS器件电容

​		考虑器件电容以便于预测器件的高频特性。

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730091757956.png" alt="image-20230730091757956" style="zoom: 33%;" />

- 四个电容值计算：

![image-20230730092026998](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730092026998.png)

​		（1）栅和沟道之间的氧化层电容C<sub>1</sub> = WLC<sub>OX</sub>

​		（2）衬底和沟道之间的耗尽层电容C<sub>2</sub> = <img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730092311801.png" alt="image-20230730092311801" style="zoom: 33%;" />

​		（3）多晶硅栅与源和漏的覆盖而产生的电容C<sub>3</sub>和C<sub>4</sub>。每单位宽度的覆盖电容用C<sub>OV</sub>表示，单位F/m。栅源和栅漏覆盖电容等于C<sub>OV</sub>W。

​		（4）源/漏区与衬底之间的结电容。**用C<sub>j</sub>和C<sub>jsw</sub>分别表示单位面积的电容（F/m<sup>2</sup>）和单位长度的电容（F/m）**。<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730093026401.png" alt="image-20230730093026401" style="zoom: 33%;" /><img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730093051779.png" alt="image-20230730093051779" style="zoom:33%;" />，式中V<sub>R</sub>是结的反向电压，Φ<sub>B</sub>是结的内建电势，幂指数m的值一般在0.3到0.4之间。

- 不同工作区域的MOSFET的各端子之间的电容：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730102839441.png" alt="image-20230730102839441" style="zoom: 33%;" />

#### 2.4.3 MOS小信号模型

​		得到小信号模型的步骤：

1. 给器件的各个端子施加一个偏置电压
2. 在两个端子之间产生一个电压增量而其他端子的电压保持不变
3. 测量所有端子电流的变化

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730110228509.png" alt="image-20230730110228509" style="zoom: 33%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730111126083.png" alt="image-20230730111126083" style="zoom:33%;" />

### 2.5 SPICE模型

​		一级MOS SPICE模型参数定义：

![image-20230730111906638](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730111906638.png)

