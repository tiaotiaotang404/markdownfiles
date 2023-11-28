|   输入电压   | 2.5V  |   负载调整率@1kHz   | 30mV/A |
| :----------: | :---: | :-----------------: | :----: |
|   输出电压   | 1.8V  |  负载调整率@100kHz  | 50mV/A |
|   参考电压   | 0.9V  |   线性调整率@1kHz   | 2mV/V  |
|   负载电流   | 10mA  |  线性调整率@100kHz  | 30mV/V |
|   负载电容   |  1uF  |  输出噪声电压@1kHz  |  25nV  |
|   静态电流   | 500nA | 输出噪声电压@100kHz |  10nV  |
| 输出电压精度 |  ±1%  |      相位裕度       |  45°   |

### FVF-LDO的核心结构：

![image-20231123143454978](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231123143454978.png)

​		MC1和MC2形成折叠共源共栅放大器，其用作误差放大器（EA）。由于FVF是单端结构，对于类似的动态响应，与传统差分EA[14]相比，基于FVF的LDO仅花费约50%的电流。因此，基于FVF的LDO优选用于物联网等低功耗应用。另一方面，应改进基于FVF的LDO的控制电压V~BIAS~调节，以获得更高的精度。

1，折叠共源共栅放大器学习：

​		[电子技术——共源共栅放大器-CSDN博客](https://blog.csdn.net/jiahonghao2002/article/details/128951923)

> 对于共源共栅的分析挺好的，通俗易懂

![image-20231123184733548](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231123184733548.png)

![image-20231124095903667](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231124095903667.png)

![image-20231128170550848](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231128170550848.png)

![image-20231126004151620](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231126004151620.png)

![image-20231126004213102](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231126004213102.png)

负载瞬态响应：

![image-20231128170318765](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231128170318765.png)

![image-20231128170337011](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231128170337011.png)

![image-20231128170606187](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20231128170606187.png)