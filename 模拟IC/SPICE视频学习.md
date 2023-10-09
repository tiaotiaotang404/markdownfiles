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

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230930193955849.png" alt="image-20230930193955849" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230916192241173.png" alt="image-20230916192241173" style="zoom:50%;" />

##### 		考虑沟道调制效应：

##### 		1）直流分析

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230916192441778.png" alt="image-20230916192441778" style="zoom:50%;" />

##### 		2）交流分析

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230916192537906.png" alt="image-20230916192537906" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230916192638766.png" alt="image-20230916192638766" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230916192728485.png" alt="image-20230916192728485" style="zoom:50%;" />

###### 共源放大器（电阻负载）输入输出特性仿真：

- 直流分析

```fortran
CS(R-load)_vi&vo
.OPTION POST
.PROTECT
.LIB "/home/PDK/UMK55FDKLPC00000OA_A10_PB/Models/Hspice/l55lp_mm_v0131.lib" tt_lp_rvt12
.UNPROTECT
M1 Vo Vi 0 0 n_12_lprvt w=2u l=0.6u
R0 vdd Vo 10k
vdd vdd 0 5
v1 vi 0 1.2
.op
.dc v1 0 5 0.1
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

仿真结果：vi（绿色），vo（黄色）

![image-20230930200640664](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230930200640664.png)

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230930201014469.png" alt="image-20230930201014469" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230930212317927.png" alt="image-20230930212317927" style="zoom:50%;" />

> 当输入电压大于4.8V时，管子仍处于线性区，但输出电压开始增大，MOS管的I~D~电流开始增大，原因未知

###### 参数分析三种方法：

不同负载下的输入输出特性（参数扫描方法）

```fortran
CS(R-load)_vi&vo_param
.OPTION POST
.PROTECT
.LIB "/home/PDK/UMK55FDKLPC00000OA_A10_PB/Models/Hspice/l55lp_mm_v0131.lib" tt_lp_rvt12
.UNPROTECT
.param rload=10k
M1 Vo Vi 0 0 n_12_lprvt w=2u l=0.6u
R0 vdd Vo rload
vdd vdd 0 5
v1 vi 0 1.2
.op
.dc v1 0 4.5 0.1 sweep rload 5k 10k 1k
.probe dc v(Vo) deriv('v(Vo)')
.end
```

![image-20230930215218370](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230930215218370.png)

不同负载下的输入输出特性（参数列表方法）

```fortran
CS(R-load)_vi&vo_param
.OPTION POST
.PROTECT
.LIB "/home/PDK/UMK55FDKLPC00000OA_A10_PB/Models/Hspice/l55lp_mm_v0131.lib" tt_lp_rvt12
.UNPROTECT
.param rload=10k
M1 Vo Vi 0 0 n_12_lprvt w=2u l=0.6u
R0 vdd Vo rload
vdd vdd 0 5
v1 vi 0 1.2

.data rload_table
rload
5k
7k
10k
.enddata

.op
.dc v1 0 4.5 0.1 sweep data=rload_table
.probe dc v(Vo) deriv('v(Vo)')
.end
```

不同负载下的输入输出特性（参数点方法）

```fortran
CS(R-load)_vi&vo_param
.OPTION POST
.PROTECT
.LIB "/home/PDK/UMK55FDKLPC00000OA_A10_PB/Models/Hspice/l55lp_mm_v0131.lib" tt_lp_rvt12
.UNPROTECT
.param rload=10k
M1 Vo Vi 0 0 n_12_lprvt w=2u l=0.6u
R0 vdd Vo rload
vdd vdd 0 5
v1 vi 0 1.2
.op
.dc v1 0 4.5 0.1 sweep rload POI 5k 10k 20k
.probe dc v(Vo) deriv('v(Vo)')
.end
```

- 交流分析

```fortran
CS(R-load)_ac
.OPTION POST
.PROTECT
.LIB "/home/PDK/UMK55FDKLPC00000OA_A10_PB/Models/Hspice/l55lp_mm_v0131.lib" tt_lp_rvt12
.UNPROTECT
.param rload=10k
M1 Vo Vi 0 0 n_12_lprvt w=2u l=0.6u
R0 vdd Vo rload
vdd vdd 0 5
v1 vi 0 1.2 ac 1

.op
.ac dec 10 10 10G sweep rload 10k 100k 20k
.print ac vdb(Vo) vp(Vo)
*.dc v1 0 4.5 0.1 sweep rload POI 5k 10k 20k
*.probe dc v(Vo) deriv('v(Vo)')
.end
```

### 2，共源放大器（二极管连接负载）

- NMOS二极管连接负载

```fortran
CS(ndiode-load)_vi&vo
.OPTION POST
.PROTECT
.LIB "/home/PDK/UMK55FDKLPC00000OA_A10_PB/Models/Hspice/l55lp_mm_v0131.lib" tt_lp_rvt12
.UNPROTECT
M1 Vo Vi 0 0 n_12_lprvt w=10u l=0.6u
M2 vdd vdd Vo 0 n_12_lprvt w=2u l=0.6u
vdd vdd 0 3.3
v1 vi 0 1.2
.op
.dc v1 0 3.3 0.1
.print dc v(Vo)
.end
```

![image-20231002110315786](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231002110315786.png)

![image-20231002110511514](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231002110511514.png)

```fortran
CS(ndiode-load)_vi&vo
.OPTION POST
.PROTECT
.LIB "/home/PDK/UMK55FDKLPC00000OA_A10_PB/Models/Hspice/l55lp_mm_v0131.lib" tt_lp_rvt12
.UNPROTECT
M1 Vo Vi 0 0 n_12_lprvt w=10u l=0.6u
M2 Vo Vo vdd vdd p_12_lprvt w=2u l=0.6u
vdd vdd 0 3.3
v1 vi 0 1.2
.op
.dc v1 0 3.3 0.1
.print dc v(Vo)
.end
```

![image-20231002113751223](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231002113751223.png)

![image-20231002113824636](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231002113824636.png)

- 参数扫描

```fortran
CS(ndiode-load)_vi&vo
.OPTION POST
.PROTECT
.LIB "/home/PDK/UMK55FDKLPC00000OA_A10_PB/Models/Hspice/l55lp_mm_v0131.lib" tt_lp_rvt12
.UNPROTECT
.param w1=10u
M1 Vo Vi 0 0 n_12_lprvt w=w1 l=0.6u
M2 Vo Vo vdd vdd p_12_lprvt w=2u l=0.6u
vdd vdd 0 3.3
v1 vi 0 1.2
.op
.dc v1 0 3.3 0.1 sweep w1 2u 10u 2u
.print dc v(Vo)
.end
```

![image-20231002114754010](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231002114754010.png)

- 交流分析

```fortran
CS(ndiode-load)_ac
.OPTION POST
.PROTECT
.LIB "/home/PDK/UMK55FDKLPC00000OA_A10_PB/Models/Hspice/l55lp_mm_v0131.lib" tt_lp_rvt12
.UNPROTECT
.param w1=10u
M1 Vo Vi 0 0 n_12_lprvt w=w1 l=0.6u
M2 Vo Vo vdd vdd p_12_lprvt w=2u l=0.6u
vdd vdd 0 3.3
v1 vi 0 1.2 ac 1
.op
.ac dec 10 10 10G sweep w1 2u 10u 2u
*.dc v1 0 3.3 0.1 sweep w1 2u 10u 2u
.print ac vdb(Vo) vp(Vo)
.end
```

![image-20231002120049395](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231002120049395.png)

### 3，共源放大器（电流源负载）

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231002183606348.png" alt="image-20231002183606348" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231002183642699.png" alt="image-20231002183642699" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231002183707553.png" alt="image-20231002183707553" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231002190610851.png" alt="image-20231002190610851" style="zoom:50%;" />

### 4，共栅极

- 直流分析

```fortran
CG_vi&vo
.OPTION POST
.PROTECT
.LIB "/home/PDK/UMK55FDKLPC00000OA_A10_PB/Models/Hspice/l55lp_mm_v0131.lib" tt_lp_rvt12
.UNPROTECT
M1 Vo vb Vi 0 n_12_lprvt w=2u l=0.6u
R0 vdd Vo 50k
vdd vdd 0 3.3
vb vb 0 2
v1 vi 0 1.2
.op
.dc v1 0 3.3 0.1 sweep vb 2 4 0.5
.print dc v(Vo)
.end
```

![image-20231002194759345](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231002194759345.png)

- 交流分析

```fortran
CG_ac
.OPTION POST
.PROTECT
.LIB "/home/PDK/UMK55FDKLPC00000OA_A10_PB/Models/Hspice/l55lp_mm_v0131.lib" tt_lp_rvt12
.UNPROTECT
M1 Vo vb Vi 0 n_12_lprvt w=2u l=0.6u
R0 vdd Vo rload
vdd vdd 0 3.3
vb vb 0 2
v1 vi 0 1.2 ac 1
.op
.ac dec 10 10 50G sweep rload 10k 100k 20k
*.dc v1 0 3.3 0.1 sweep vb 2 4 0.5
.print ac vdb(Vo) vp(Vo)
.end
```

![image-20231002200602508](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231002200602508.png)

- 输入输出阻抗仿真

```fortran
CG_ri_ro
.OPTION POST
.PROTECT
.LIB "/home/PDK/UMK55FDKLPC00000OA_A10_PB/Models/Hspice/l55lp_mm_v0131.lib" tt_lp_rvt12
.UNPROTECT
M1 Vo vb Vi 0 n_12_lprvt w=2u l=0.6u
R0 vdd Vo rload
vdd vdd 0 3.3
vb vb 0 2
v1 vi 0 1.2
.op
.dc rload 10k 100k 20k
.tt v(Vo) v1
.end
```

> .tt 在直流分析基础上进行传输特性分析，即求电路的传输，输入输出电阻

![image-20231002202733737](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231002202733737.png)

### 5，模型参数提取

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231003103043789.png" alt="image-20231003103043789" style="zoom:50%;" />

```fortran
*NMOS I-V Characteristic
.OPTIONS POST
.PROTECT
.lib "/home/PDK/UMK55FDKLPC00000OA_A10_PB/Models/Hspice/l55lp_mm_v0131.lib" tt_lp_rvt12
.UNPROTECT
.param IDS=1mA Ln=1u Wn="2*Ln" 
M1 1 1 0 0 n_12_lprvt  W=Wn L=Ln 
I1 VDD 1 IDS  
V1 VDD 0 3.3V
.OP
.DC IDS 1u 100u 1u SWEEP Ln POI 9 55n 100n 110n 165n 200n 220n 275n 330n 400n 
.PRINT vth=par('LV9(M1)') vgs=par('LX2(M1)') 
.PRINT gm=par('LX7(M1)') gds=par('LX8(M1)') 
.PRINT KN=par("gm/(vgs-vth)/(Wn/Ln)")
.PRINT Weff=par('LV2(M1)') Leff=par('LV1(M1)')
.PRINT KN2=par("gm/(vgs-vth)/(Weff/Leff)")
.PRINT KN3=par("LV21(M1)/(Wn/Ln)")
.PRINT LAMBDA=par("gds/LX4(M1)")
.PRINT GAMMA=par("LV22(M1)")
.PRINT dc id(M1) V(1)
*.ac dec 10 1k 200meg 
*.DC VIN 0 5 0.01
*.PRINT AC VP(VOUT) VDB(VOUT)
*.PRINT dc V(VOUT)
.END 
```

