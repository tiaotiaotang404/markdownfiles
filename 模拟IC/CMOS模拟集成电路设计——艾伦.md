## 第四章

### 第一节 单个MOS管

![image-20230810210805252](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230810210805252.png)

1. 注意区分大信号和小信号
2. **MOS管本质上是压控电流源**
3. *μ*——载流子迁移率；C<sub>ox</sub>——栅氧化极的厚度

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230810211457580.png" alt="image-20230810211457580" style="zoom:50%;" />

#### 交流放大倍数：

![image-20230810211703254](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230810211703254.png)								    		**g<sub>m</sub>表示MOS管将输入的电压转换成电流的能力**

#### 交流电阻：

![image-20230810215135318](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230810215135318.png)

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230810213726011.png" alt="image-20230810213726011" style="zoom:50%;" />

### 第二节 两个MOS管——如何放大（放大电路主要研究是对交流信号的放大）

![image-20230810214458319](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230810214458319.png)

#### MOS管构成的放大电路，根据负载的不同分为下面三种：

![image-20230810215857986](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230810215857986.png)

（1）负载是一个 栅极和漏极相连的MOS管：

​		**M2一旦导通就处于饱和区**

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230810222946340.png" alt="image-20230810222946340" style="zoom:50%;" />

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

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230817224326844.png" alt="image-20230817224326844" style="zoom:50%;" />

<img src="C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230817224439796.png" alt="image-20230817224439796" style="zoom:50%;" />
