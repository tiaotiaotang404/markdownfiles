[(26条消息) windows系统下上传代码到github的较详细教程_windows上传github代码_叶长晴的博客-CSDN博客](https://blog.csdn.net/weixin_44017406/article/details/129906172)

[(26条消息) windows上传本地项目到github_github 本地传脚本 windows_cool同学的博客-CSDN博客](https://blog.csdn.net/qq_40466537/article/details/128170063)

[(26条消息) 搭建github-ssh连接时，Could not resolve hostname github的解决方案(无法ping通github)_这世界比瞳孔还漆黑的博客-CSDN博客](https://blog.csdn.net/Hacker_MAI/article/details/123270836)

### 上传本地项目到github

上传到本地仓库

1. 首先，还是进入到项目根目录的Git控制台中，初始化本地仓库

```c
git init
```

2. 接着把项目中的文件放到暂存区，其中的 . 是指代当前目录下的所有文件

```c
git add .
```

3. 随后进行第一次提交，到本地仓库

```c
git commit -m "origin version"
```

> 其中的“origin version”是备注，自己填写即可

### 上传到远程仓库

1. 首先在github上新建一个仓库，并复制该仓库的链接：即xxx.git
2. 建立本地仓库和远程仓库的连接关系

```c
git remote add origin xxx.git
```

3. 最后，把本地仓库的代码提交到远程仓库分支

```c
git push -u origin master
```

> origin后面是远程仓库分支的名称，与本地当前分支对应

以上就完成了第一次的上传本地项目到github

### 上传github：

```c
git add .
git commit -m "origin version"
git push -u origin master
```



