# Minecraft 阿里云开服及游玩教程

制作者：闫枫

## 一、购买服务器（以阿里云为例）

访问[阿里云官网]([阿里云权益中心_助力学生、开发者、企业用云快速上云-阿里云 (aliyun.com)](https://www.aliyun.com/benefit/waitou/V2?utm_content=se_1016983803))，登录账号后，点击“产品”—>"云服务ECS"来购买合适的云服务器

我搭建的是Forge服，大概添加了二十个mod，使用了一款2V8G的服务器，有40G内存，预装了Ubuntu。（仅供参考）





## 二、配置Java环境

### 1、下载JDK17压缩包

有两种方法，（1）是直接在linux终端使用命令进行安装，（2）是在本地主机上下好JDK的压缩包后传到服务器
这里推荐使用命令进行安装，如（1）无法安装，在通过（2）进行安装

这里我将JDK安装在/usr/local/java目录下，首先创建目录（这一步无论哪种方法都要执行）

```
mkdir -p /usr/local/java
```


#### （1）在linux终端使用命令进行安装

在你购买的云服务器控制台界面有远程连接选项，远程连接后即进入linux服务器命令终端

进入创建好的目录

```
cd /usr/local/java
```

运行下面这行代码

```
wget https://download.oracle.com/java/17/latest/jdk-17_linux-x64_bin.tar.gz
```



#### （2）通过Xftp传到服务器

访问[Xftp官网]([XFTP - NetSarang Website (xshell.com)](https://www.xshell.com/zh/xftp/))下载Xftp

打开软件后无需注册，点击Later，然后在主界面的右上角新建一个SFTP连接

HOST填你的服务器公网IP地址

Method选Password

User Name 填你的服务器管理员名称

Password填你的密码

最后点击connect

连接成功后主界面右侧会出现服务器的文件列表，左侧为本地主机的文件列表

在浏览器下载适用于你服务器系统版本的的OpenJDK压缩包。（注意！！首先明确自己要部署哪一版本的Minecraft服务端，这关乎你要下载哪一版本的JDK，如果服务端版本在1.20以上请安装OpenJDk17,其他版本请自行查询）

下载好后在连接好的Xftp中找到该压缩包传到服务器/usr/local中，只需从左侧将文件拖至右侧对应文件夹中即可



### 2、解压JDK

解压JDK需要在终端执行以下代码

```
# 解压当前目录下的JDK压缩文件到安装目录，将下面压缩包名字替换成你下载的，即jdk-17_linux-x64_bin.tar.gz部分
tar -zxvf jdk-17_linux-x64_bin.tar.gz -C /usr/local/java/
```



### 3、配置环境变量

进入安装java的文件夹，如果在该文件夹下，此步可以省略

```
cd /usr/local/java
```

用vim或vi 打开/etc/profile 文件

```
vim /etc/profile
```

点击键盘"i"键进入编辑模式，并将以下三行代码粘贴到末尾

```
export JAVA_HOME=/home/local/java/jdk1.8.0_271
export PATH=$JAVA_HOME/bin:$PATH
export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
```

点击"ESC",输入":wq"保存并退出



### 4、检查Java环境是否配置完成

输入以下代码惊醒检查

```
java -version
```

不报错则安装成功



## 三、安装MCSM面板

### 1、放行23333和24444端口

在云服务器控制台选择"安全组"—>”管理规则“—>添加23333和24444端口



### 2、安装MCSM面板

这里将该面板安装在/usr/local文件夹

如在该文件夹下请进行后续操作，如没有请自行查询如何进入。您也可以安装在其他文件夹下

在终端输入安装MCSM的命令

```
#一键安装代码
wget -qO- https://gitee.com/mcsmanager/script/raw/master/setup.sh | bash
```

等待面板安装完成后，使用以下命令运行面板

```
systemctl start mcsm-{daemon,web}
```



### 3、访问面板

在浏览器网址栏输入

```
http://你云服务器的公网IP:23333
```

即可访问

### 4、常用的面板指令

```
#面板指令
systemctl start mcsm-{daemon,web}.service # 启动面板
systemctl stop mcsm-{daemon,web}.service # 停止面板
systemctl restart mcsm-{daemon,web}.service # 重启面板
systemctl enable mcsm-{daemon,web}.service #开机自启 
 
systemctl restart mcsm-web.service # 只重启面板 Web 服务
systemctl restart mcsm-daemon.service # 只重启面板守护进程服务
```



## 四、安装Forge服务端核心

### 1、下载Forge服务端核心

在[Forge官网]([Downloads for Minecraft Forge for Minecraft 1.20.2](https://files.minecraftforge.net/net/minecraftforge/forge/))下载你想部署版本的forge服务端

### 2、通过MCSM上传到服务器中





## 五、开服



## 六、安装mod和配置游戏文件

### 1、下载mod

### 2、上传mod

### 3、可能会遇到的问题

### 4、配置游戏文件



## 七、客户端游玩教程（以HMCL为例）

### 1、下载HMCL启动器

### 2、下载与服务的相同版本的游戏

### 3、安装与服务器相同的mod

### 4、加入服务器



## 八、一些常用的游戏指令



