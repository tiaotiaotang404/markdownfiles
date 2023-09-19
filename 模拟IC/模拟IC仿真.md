## 仿真：

1. 编写.sp文件

2. ```bash
   hspice -i 文件名.sp > 文件名.lis   #会产生数据分析文件和波形文件（和.sp内容有关）
   ```

3. ```bash
   wv  #仿真波形查看
   ```

![image-20230907223226348](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230907223226348.png)

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230908102532505.png" alt="image-20230908102532505"  />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230801085344954.png" alt="image-20230801085344954" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230730111906638.png" alt="image-20230730111906638" style="zoom: 50%;" />

##### 2-5

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230908100926968.png" alt="image-20230908100926968" style="zoom: 80%;" />

```fortran
EX2-5 a
*circuit description
M1 1 1 2 0 MOS1 W=5U L=1.0U
VDD 1 0 DC 5.0
VX 2 0 DC 1.5
*circuit control
.OPTION LIST NOSD POST
.MODEL MOS1 NMOS VTO=0.7 KP=110U GAMMA=0.4 LAMBDA=0.04 PHI=0.7
.DC VX 0 1.5 0.1  *直流扫描
.END
```

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230908102616965.png" alt="image-20230908102616965" style="zoom:50%;" />

```fortran
EX2-5 b
*circuit description
M1 1 2 3 0 MOS1 W=5U L=1.0U
VS 3 0 DC 1.0
VX 1 0 DC 3.0
VG 2 0 DC 1.9
*circuit control
.OPTION LIST NOSD POST
.MODEL MOS1 NMOS VTO=0.7 KP=110U GAMMA=0.4 LAMBDA=0.04 PHI=0.7
.DC VX 0 3.0 0.1
.END
```

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230908105800140.png" alt="image-20230908105800140" style="zoom:50%;" />

> 结果分析：仿真结果与理论值不同，HSPICE仿真中无法做到MOS管源漏互换的情况，原因是仿真中MOS管的四个极是通过MOS管的描述语句中的结点顺序来判断的，并不能根据各个结点的电压大小关系来区分。

```fortran
EX2-5 b
*circuit description
M1 1 2 3 4 MOS1 W=5U L=1.0U
VD 1 0 DC 1.5
VG 2 0 DC 1.9
VS 3 0 DC 1.0
VB 4 0 DC 3.0
*circuit control
.OPTION LIST NOSD POST
.MODEL MOS1 NMOS VTO=0.7 KP=110U GAMMA=0.4 LAMBDA=0.04 PHI=0.7
.DC VB 0 3.0 0.1
.END
```

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230908111521260.png" alt="image-20230908111521260" style="zoom:50%;" />

##### test:

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230912153132513.png" alt="image-20230912153132513" style="zoom:50%;" />

###### 直流分析：

```fortran
TEST_DC
*circuit description
M1 2 1 0 0 MOSN W=5U L=1U
M2 2 3 4 4 MOSP W=5U L=1U
M3 3 3 4 4 MOSP W=5U L=1U
R1 3 0 100K
VDD 4 0 DC 5.0
VIN 1 0 DC 5.0
*circuit control
.OPTION LIST NOSD POST
.MODEL MOSN NMOS VTO=0.7 KP=110U GAMMA=0.4 LAMBDA=0.04 PHI=0.7
.MODEL MOSP PMOS VTO=-0.7 KP=50U GAMMA=0.57 LAMBDA=0.05 PHI=0.8
.DC VIN 0 5 0.1
.PRINT DC V(2)
.END
```

>  `.OPTION LIST NOSD POST` 时，实际上是告诉HSPICE生成一个包括节点电压和支路电流的输出列表，同时省略了详细的子电路定义，使输出更加简洁，侧重于仿真结果。这对于处理包含许多子电路的复杂电路时，可以简化输出，使其更加专注于仿真结果，而不受子电路的干扰。

![image-20230912160231997](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230912160231997.png)

- 输出列表文件.lis：

1. NMOS管的各类参数（几何参数、阈值电压参数、温度参数等）
2. PMOS管的各类参数
3. 仿真电路器件总结（电路中用到的各种器件的名字、结点、相关参数等）
4. PRINT打印输出的数据
5. 电路、运行时间等内容的统计信息



###### 交流分析：

![image-20230912160857231](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230912160857231.png)

```fortran
TEST_AC
*circuit description
M1 2 1 0 0 MOSN W=5U L=1U
M2 2 3 4 4 MOSP W=5U L=1U
M3 3 3 4 4 MOSP W=5U L=1U
CL 2 0 5P
R1 3 0 100K
VDD 4 0 DC 5.0
VIN 1 0 DC 1.07 AC 1.0
*circuit control
.OPTION LIST NOSD POST
.MODEL MOSN NMOS VTO=0.7 KP=110U GAMMA=0.4 LAMBDA=0.04 PHI=0.7
.MODEL MOSP PMOS VTO=-0.7 KP=50U GAMMA=0.57 LAMBDA=0.05 PHI=0.8
.AC DEC 20 100 100MEG
.OP
.PRINT AC VM(2) VDB(2) VP(2)
.END
```

> `VIN 1 0 DC 1.07 AC 1.0` 命令表示在节点1和地之间创建一个电压源，该电压源提供1.07伏特的直流电压和1.0伏特的交流电压。这可以用于模拟电路中同时存在直流和交流信号的情况，例如交流信号叠加在一个直流偏置上。

> `.AC DEC 20 100 100MEG`在对数频率轴上从100Hz到100MHz的范围内每十倍频计算20个点

> `.OP`打印所有电路结点的直流电压，验证交流分析是否在期望的区域

VM线性幅度；VDBdb幅度；VP相位

![image-20230912161752379](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230912161752379.png)

###### 瞬态分析：

```fortran
TEST_TR
*circuit description
M1 2 1 0 0 MOSN W=5U L=1U
M2 2 3 4 4 MOSP W=5U L=1U
M3 3 3 4 4 MOSP W=5U L=1U
CL 2 0 5P
R1 3 0 100K
VDD 4 0 DC 5.0
*VIN 1 0 DC 21.07 AC 1.0
VIN 1 0 PWL(0 0V 1U 0V 1.05U 3V 3U 3V 3.05U 0V 6U 0V)
*circuit control
.OPTION LIST NOSD POST
.MODEL MOSN NMOS VTO=0.7 KP=110U GAMMA=0.4 LAMBDA=0.04 PHI=0.7
.MODEL MOSP PMOS VTO=-0.7 KP=50U GAMMA=0.57 LAMBDA=0.05 PHI=0.8
.TRAN 0.01U 4U
.OP
.PRINT TRAN V(2) V(1)
.END
```

> `VIN 1 0 PWL(0 0V 1U 0V 1.05U 3V 3U 3V 3.05U 0V 6U 0V)`分段线性源（PWL），`(0 0V 1U 0V 1.05U 3V 3U 3V 3.05U 0V 6U 0V)`：这是一个以时间和电压值交替排列的序列，定义了电压源在不同时间点的电压值。每对值代表了一个时间点和该时间点的电压值。`(0 0V)` 表示在时间0秒时电压为0伏特。`(1U 0V)` 表示在时间1微秒（1U，其中U表示微）时电压保持在0伏特。

> `.TRAN 0.01U 4U` 命令表示要进行时间步长为0.01微秒的时间域仿真，仿真将运行从时间0开始，一直到时间4微秒结束

![image-20230912162654932](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230912162654932.png)

##### 3-15

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230914142510792.png" alt="image-20230914142510792" style="zoom: 50%;" />



##### 3-16

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230914142710886.png" alt="image-20230914142710886" style="zoom:50%;" />



##### 3-17

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230914142747341.png" alt="image-20230914142747341" style="zoom:50%;" />

