#  第一章：基本电路分析方法

## 一，MOS场效应管模型

![image-20230730224721414](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730224721414.png)

### 1，MOS1模型

![image-20230730224846830](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730224846830.png)

![image-20230730224957980](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730224957980.png)

#### 1.1，MOS1模型器件工作特性

![image-20230730225035264](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730225035264.png)

![image-20230730225232066](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730225232066.png)

### 2，MOS2模型

![image-20230730225334133](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730225334133.png)

### 3，MOS3模型

![image-20230730225527731](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730225527731.png)

### 4，MOS电容模型

![image-20230730225709120](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730225709120.png)

![image-20230730225739580](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730225739580.png)

![image-20230730225820975](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730225820975.png)

### 5，MOS4模型——BSIM模型

![image-20230730225949951](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730225949951.png)

![image-20230730230137300](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730230137300.png)

![image-20230730230313419](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730230313419.png)

### 6，不同模型应用场合

![image-20230730230420683](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730230420683.png)

## 二，SPICE基本语法

### 1，SPICE输入文件

![image-20230730230847837](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730230847837.png)

### 2，输入描述语句构成

![image-20230730231004170](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730231004170.png)

![image-20230730231153572](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730231153572.png)

### 3，输入描述语句规定

![image-20230730231247598](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730231247598.png)

![image-20230730231403279](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730231403279.png)

![image-20230730231517074](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730231517074.png)

![image-20230730231711071](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730231711071.png)

### 4，元件描述语句

#### 4.1 电阻

![image-20230730231911629](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730231911629.png)

#### 4.2 电容和电感

![image-20230730232002004](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730232002004.png)

![image-20230730232054130](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730232054130.png)

#### 4.3 半导体器件

![image-20230730232121168](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730232121168.png)

##### 4.3.1 二极管

![image-20230730232215729](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730232215729.png)

##### 4.3.2 双极性三极管

![image-20230730232254603](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730232254603.png)

##### 4.3.3 MOS场效应管

![image-20230730232345013](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730232345013.png)

![image-20230730232459050](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730232459050.png)

![image-20230730232537736](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730232537736.png)

##### 4.3.4 结型场效应管

![image-20230730232619287](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730232619287.png)

#### 4.4 电源

![image-20230730232706312](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730232706312.png)

##### 4.4.1 独立电源

![image-20230730232747494](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730232747494.png)

![image-20230730232854802](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730232854802.png)

##### 4.4.2 脉冲源

![image-20230730232919917](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730232919917.png)

##### 4.4.3 正弦波

![image-20230730233031532](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730233031532.png)

![image-20230730233217385](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730233217385.png)

##### 4.4.4 分段线性源

![image-20230730233253030](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730233253030.png)

![image-20230730233415036](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730233415036.png)

#### 4.5 线性受控源

![image-20230730233453521](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730233453521.png)

![image-20230730233543543](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730233543543.png)

![image-20230730233629495](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730233629495.png)

![image-20230730233604755](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730233604755.png)

#### 4.6 模型

![image-20230730233653386](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730233653386.png)

![image-20230730233745556](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730233745556.png)

#### 4.7 子电路

![image-20230730233834510](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730233834510.png)

![image-20230730234131384](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730234131384.png)

#### 4.8 文件包含

![image-20230730234232686](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730234232686.png)

## 三，直流分析

### 1，直流工作点分析

![image-20230731100117418](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230731100117418.png)

![image-20230731100425580](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230731100425580.png)

### 2，直流扫描分析

![image-20230731100645972](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230731100645972.png)

### 3，小信号传输函数

![image-20230731101136833](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230731101136833.png)

### 4，直流或小信号交流灵敏度分析

![image-20230731101250438](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230731101250438.png)

### 5，零极点分析

![image-20230731101405896](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230731101405896.png)

## 四，交流分析和瞬态分析

### 1，交流特性分析

![image-20230731101511970](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230731101511970.png)

### 2，噪声分析

![image-20230731101753534](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230731101753534.png)

### 3，瞬态特性分析

![image-20230731101904116](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230731101904116.png)

例子：

![image-20230731102157990](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230731102157990.png)

![image-20230731102247585](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230731102247585.png)

### 4，傅里叶分析

![image-20230731102414019](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230731102414019.png)

例子：

![image-20230731102434681](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230731102434681.png)

### 5，失真分析

![image-20230731102617371](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230731102617371.png)

### 6，分析控制语句

#### 6.1 初始节点电压设置

![image-20230731102714908](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230731102714908.png)

#### 6.2 初始条件设置

![image-20230731102756948](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230731102756948.png)

#### 6.3 输出控制

![image-20230731102911206](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230731102911206.png)

![image-20230731103037440](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230731103037440.png)

### 7，HSPICE输入输出文件

![image-20230731103215809](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230731103215809.png)

### 8，重置参数

![image-20230731103313460](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230731103313460.png)

# 第二章：电流镜和差动放大器的设计仿真

### 一，单极放大器的设计仿真

#### 电路分析思路：

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230916185244707.png" alt="image-20230916185244707" style="zoom:50%;" />

#### 1，共源放大器（电阻负载）

##### 		忽略沟道调制效应：

##### 		1）直流分析

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230916185824865.png" alt="image-20230916185824865" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230916190018533.png" alt="image-20230916190018533" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230916190051210.png" alt="image-20230916190051210" style="zoom:50%;" />

##### 得到输入输出关系，判定放大器的工作范围（饱和区）

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230916190206813.png" alt="image-20230916190206813" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230916190718821.png" alt="image-20230916190718821" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230916190934164.png" alt="image-20230916190934164" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230916191007757.png" alt="image-20230916191007757" style="zoom: 50%;" />

##### 确定合适的直流工作点（直流工作点的确定与电路的输入输出摆幅直接相关）

##### 2）交流小信号分析

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230916191947781.png" alt="image-20230916191947781" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230916192241173.png" alt="image-20230916192241173" style="zoom:50%;" />

##### 		考虑沟道调制效应：

##### 		1）直流分析

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230916192441778.png" alt="image-20230916192441778" style="zoom:50%;" />

##### 		2）交流分析

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230916192537906.png" alt="image-20230916192537906" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230916192638766.png" alt="image-20230916192638766" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230916192728485.png" alt="image-20230916192728485" style="zoom:50%;" />

###### 输入输出特性仿真：

```fortran
CS(R-load)_vi&vo
.OPTION POST
.PROTECT
.LIB "l55lp_mm_v0131.lib" tt_lp_rvt12
.UNPROTECT
M1 Vo Vi 0 0 n_12_lprvt w=2u l=0.6u
R0 vdd Vo 10k
vdd vdd 0.5
v1 vi 0 1.2
.op
.dc v1 0.5 0.1
.print dc v(Vo)
.end
```

```bash
55lp_mm_v0131.lib:
1,模型列表 model list
2，corner model
3，模型使用举例
* model usage
*  1. use .lib statements to include sections from the library corresponding to the devices to be simulated.
*     .lib "modelfilename.lib" sectionname
*     for example, if the model n_12_lprvt will be used, one of its corresponding corner sections need
*     to be included (tt_lp_rvt12, ss_lp_rvt12, ff_lp_rvt12, snfp_lp_rvt12, or fnsp_lp_rvt12).
*     example: .lib "l55lp_mm_v0131.lib" tt_lp_rvt12
*  2. define devices to be simulated.
*     example: m1 d g s b n_12_lprvt w=w l=l as=as ad=ad ps=ps pd=pd
*              + nf=nf dtemp=dtemp sa=sa sb=sb sd=sd sca=sca scb=scb scc=scc
* tt:   typical n-ch mosfet and typical p-ch mosfet
* ff:   fast n-ch mosfet and fast p-ch mosfet
* ss:   slow n-ch mosfet and slow p-ch mosfet
* fnsp: fast n-ch mosfet and slow p-ch mosfet
* snfp: slow n-ch mosfet and fast p-ch mosfet
* tt_tn:   typical n-ch mosfet and typical p-ch mosfet with thermal noise enhancement
* ff_tn:   fast n-ch mosfet and fast p-ch mosfet with thermal noise enhancement
* ss_tn:   slow n-ch mosfet and slow p-ch mosfet with thermal noise enhancement
* fnsp_tn: fast n-ch mosfet and slow p-ch mosfet with thermal noise enhancement
* snfp_tn: slow n-ch mosfet and fast p-ch mosfet with thermal noise enhancement
```

