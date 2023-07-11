### Ubuntu连接不了网络/没有网络图标解决：

[(27条消息) Ubuntu无网络连接/无网络标识解决方法_ubuntu网络连接不上_菠菠萝宝的博客-CSDN博客](https://blog.csdn.net/qq_45400167/article/details/125874887?ops_request_misc=%7B%22request%5Fid%22%3A%22168523888116800217268800%22%2C%22scm%22%3A%2220140713.130102334..%22%7D&request_id=168523888116800217268800&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~top_positive~default-1-125874887-null-null.142^v88^control_2,239^v2^insert_chatgpt&utm_term=Ubuntu无网络连接&spm=1018.2226.3001.4187)

#### 问题：

![](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230528100506587.png)

```c
ping github.com
```

​		ping不通。

#### 解决：

##### 方式一：重启网络

```c
sudo systemctl start NetworkManager
sudo systemctl restart NetworkManager
```

##### 方式二：NetworkManager出问题（大概率）

###### 更新NetworkManager的配置：

```c
sudo gedit /etc/NetworkManager/NetworkManager.conf
```

​		将第五行 managed=False 改为 managed=True ，然后 ctrl+s 保存后退出

![image-20230528100943999](C:\Users\张云鑫\AppData\Roaming\Typora\typora-user-images\image-20230528100943999.png)

###### 删除NetworkManager配置

```c
service NetworkManager stop
sudo rm /var/lib/NetworkManager/NetworkManager.state 
service NetworkManager start 
```

​		注意看桌面左上角状态来会自动恢复网络连接的，会出现图标。

##### VM设置

​		将vm中网络适配器从NAT模式换为桥接模式，或者桥接模式换为NAT模式。

​		别忘了之后重启一下vm！