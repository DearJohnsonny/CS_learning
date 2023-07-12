# CS知识汇总
## 网络通信知识
### 网络分层
网络是什么？网络是用物理链路将工作站或主机相连在一起，组成数据链路，从而达到资源共享和通信的目的。这里的物理链路不仅仅指的是我们能够看得到的双绞线、光纤，也可能是无线电波。

网络通信，狭义的讲，可以理解为计算机与计算机之间基于网络进行的数据交换。当然，这个过程中也有人与计算机的交互。

简单来说，互联网协议就是在互联网上传输数据的规则。当然，协议是非常多的，比如TCP、UDP、IP协议、FTP协议等等。而使用这些协议最基本的要求就是发送方和接收方所使用的协议必须一致，否则不就鸡同鸭讲了嘛。

当我们说几层协议时，一般来说：一台设备上的第X层与另一台设备上的第X层进行通信的规则就是第X层协议。

<div align=center>
<img src="https://github.com/DearJohnsonny/CS_learning/assets/111955215/0af3f013-eea5-4419-b6b5-cff14cf95695" width="600">
</div>

<a href="https://zhuanlan.zhihu.com/p/380119935">全文可以看知乎上对于网络分层的介绍</a>

**笔者的一点理解**
同一子网：MAC地址沟通
不同子网：涉及到网络层，用IP协议定位，再用ARP协议获取目标主机的MAC地址

从而实现对计算机之间的联通。

### 局域网
我们的校园网就是局域网

<a href="https://zhuanlan.zhihu.com/p/605989647">知乎对于局域网的介绍</a>

局域网中的私网地址不可重复，但是不同局域网中可以存在相同的IP地址，比如我家可以用192.168.1.1的网段，而我的公司也可以用192.168.1.1网段

### DNS
DNS （Domain Name System 的缩写）的作用非常简单，就是根据域名查出IP地址。你可以把它想象成一本巨大的电话本。

举例来说，如果你要访问域名math.stackexchange.com，首先要通过DNS查出它的IP地址是151.101.129.69。

#### 域名的层级
**顶级域名/一级域名：**
* .COM商业性的机构或公司
* .ORG非盈利的组织、团体
* .GOV政府部门
* .MIL军事部门
* .NET从事Internet相关的网络服务的机构或公司
**二级域名：**
* baidu.com
* bilibili.com
* weibo.com
**三级域名**
* www.baidu.com
* www.weibo.com
* www.liqinzhanglab.com

而https://www.baidu.com是一个网址

### IP地址

<a href="https://cloud.tencent.com/developer/article/2165741">腾讯云上关于私有和公有IP地址的介绍博客</a>

#### 公有IP地址
简单来说，公网IP地址是可以通过 Internet 直接访问的 IP 地址，不同的公共 IPv4 地址的数量是有限的，它们通常由 Internet 服务提供商 (ISP) 分配给设备。

互联网上的所有服务器和站点都使用公共 IP 地址，且所有公共 IP 地址对其主机或服务器都是唯一的，不能重复。

对于家庭用户，ISP（运营商） 可以提供一个或多个公共 IP 地址（通常是付费服务）。

支持 NAT 的 IPv4 路由器允许家庭网络设备使用它从 WAN 接口上的提供商处获得的一个公共 IP 地址用于 Internet 连接。此外部公共 IP 地址也可用于从 Internet 访问家庭网络设备，但为此，需要在路由器上设置端口转发 。

由于公共 IP 地址的数量有限和互联网用户数量的增加，ISP 现在更普遍地向用户提供私有 IP 地址。

* A类的公有IP：1.0.0.0~9.255.255.255   +    11.0.0.0~126.255.255.255
* B类的公有IP：128.0.0.0~172.15.255.255   +   172.32.0.0~191.255.255.255
* C类的公有IP：192.0.0.0~192.168.255.255   +   192.169.0.0~223.255.255.255

#### 私有IP地址
私网IP地址不在 Internet 上路由，也无法从 Internet 向它们发送流量，它们只应该在本地网络中工作。

私有 IP 地址通常用于住宅、办公室和企业区域的局域网。每台连接到互联网的设备——例如计算机、智能手机、平板电脑或打印机，都将拥有一个私有 IP 地址。路由器需要一种方法来识别这些设备，而这些设备可能还需要相互识别，这就是私有IP地址的来源，私有IP地址是由路由器生成的，用于识别。

有两种类型的私网IP地址： IPv4 和IPv6。最初，创建私有 IP 地址是为了帮助延迟 IPv4 地址的耗尽，因为 IPv4 地址的数量有限，即使使用 32 位系统创建的 4,294,967,296 个理论上的地址，IPv4 地址空间也开始随着进入企业和家庭的新互联网连接设备的数量而减少。因此，私有 IP 地址允许私有网络在内部使用相同的 IP 地址，而不会导致公共 IP 地址冲突（有利于复用，节约IP地址号）

* A类私有IP地址：10.0.0.0～10.255.255.255
* B类私有IP地址：172.16.0.0～172.31.255.255
* C类私有IP地址：192.168.0.0～192.168.255.255

#### 其他
IPv4地址分为A、B、C、D、E五类，出去特殊作用的D、E两类，剩下的A、B、C三类地址是我们常见的IP地址段。A类地址的容量最大，可以容纳16777214个主机，B类地址可以容纳65534个主机，C类地址可以容纳254个主机。

在这三类地址中，绝大多数的IP地址都是公有地址，需要向国际互联网信息中心申请注册。但是在IPv4地址协议中预留了3个IP地址段（分别位于ABC三类中），作为私有地址，供组织机构内部使用。

所以局域网在选取使用私有地址时，一般会按照实际需要容纳的主机数来选择私有地址段。常见的局域网由于容量小，一般选择C类的192.168.0.0作为地址段使用，一些大型企业就需要使用B类甚至A类地址段作为内部网络的地址段。

<div align=center>
<img src="https://github.com/DearJohnsonny/CS_learning/assets/111955215/82165cef-e049-4292-95b7-eec3912b4d67" width="1500">
</div>

<div align=center>
<img src="https://github.com/DearJohnsonny/CS_learning/assets/111955215/20f79e23-0aa9-44b7-b82a-51c28659f872" width="400">
</div>

从上图可以看出来，北医的校园网是B类IP地址，因此前两位是网络层。而下图的PC机遇cellphone分发的IP地址虽然不同，但是把IP地址与子网掩码相与，发现是一样的，说明了是位于同一个子网下面的。

<div align=center>
<img src="https://github.com/DearJohnsonny/CS_learning/assets/111955215/4f3a01cf-e90b-47e4-aa6c-ebc4a98ce97d" width="800">
</div>

而在cmd中输入ipconfig之后发现WSL这个虚拟机的地址与真正的校园网的地址不同，是C类IP地址，但是把IP地址与子网掩码相与，发现是一样的，证明还是在同一个IP地址下面。

<div align=center>
<img src="https://github.com/DearJohnsonny/CS_learning/assets/111955215/44f94716-d8a7-44fd-a930-499befac7e1a" width="800">
</div>

<a href="https://zhuanlan.zhihu.com/p/434989401">关于IP地址和子网掩码</a>

### 关于云服务器
云服务器就是把物理服务器（俗称“母鸡”），用虚拟机技术虚拟出多台主机（俗称“小鸡”）。
#### 什么是虚拟机？
<a href="https://www.redhat.com/zh/topics/virtualization/what-is-a-virtual-machine">红帽的虚拟机技术简介</a>

虚拟机（VM）是一种创建于物理硬件系统（位于外部或内部）、充当虚拟计算机系统的虚拟环境，它模拟出了自己的整套硬件，包括 CPU、内存、网络接口和存储器。通过名为虚拟机监控程序的软件，用户可以将机器的资源与硬件分开并进行适当置备，以供虚拟机使用。

虽然构成计算机的部件（称为硬件）是物理的、有形的，但 VM 通常被认为是物理服务器中的虚拟计算机或软件定义的计算机，仅以代码的形式存在。

**虚拟机的工作原理**
* 虚拟化技术允许多个虚拟环境共享一个系统。虚拟机监控程序负责管理硬件并将物理资源与虚拟环境分隔开。来自物理环境的资源根据需要进行分区后，会分配给虚拟机使用。
* 虚拟机运行时，当用户或程序发出需要从物理环境获取更多资源的指令，虚拟机监控程序会调度物理系统的资源请求，以便虚拟机的操作系统和应用可以访问共享的物理资源池。

**虚拟机的优点**
* 服务器整合是使用虚拟机的首要原因。部署到裸机时，大多数操作系统和应用部署都只会使用少量的物理资源。通过虚拟化服务器，可以在每个物理服务器上设置大量虚拟服务器，从而提高硬件利用率。 这样就无需购买额外的物理资源（例如硬盘驱动器或硬盘），也不用压缩数据中心对电能、空间和冷却能力的需求。通过支持故障转移和冗余，虚拟机提供了额外的灾难恢复选项，而这以前只能通过增加硬件才能实现。
* 虚拟机可以提供一个与系统其余部分隔离开的环境。这样，无论虚拟机内部运行什么，都不会干扰主机硬件上运行的其他内容。由于虚拟机处于隔离状态，因此堪称是测试新应用或设置生产环境的理想之选。此外，针对特定的进程，还可以运行单用途虚拟机。

<a href="https://zhuanlan.zhihu.com/p/141973142">windows自带的虚拟机Hyper-V</a>
#### 本组的华为云服务器

<div align=center>
<img src="https://github.com/DearJohnsonny/CS_learning/assets/111955215/88dd6e79-19c4-44f6-9ade-c4d0208846d5" width="500">
</div>

买的是入门版，服务器的容量是150G

**关于云速建站：**
* 云速建站与传统开发模式不同的是，模板开发完成后不需要将代码上传到FTP虚拟空间，因为整套系统与云基础设施相连，代码可直接无缝提交到云主机上，只要将域名解析到云主机即可上线，为开发者节省了大量开发环境部署，服务器搭建，代码上传的时间。云建站是一种提供代码级别的定制性，以云计算为基础设施，低投入，高品质，省时，省心的新型建站方式。
* 当然华为也提供云服务器的租借，这种一般价格也不便宜，而且麻烦需要自己去用HTML代码设计网页。
* 云速建站的劣势：直接套用模板，做出来的网站千篇一律，毫无新意，可能网上一搜就有一大把一样模板的网站。这样的网站会被搜索引擎认为是雷同站点，可能不予以收录展现，直接影响网站的后期运营。当然目前我们在网页搜索老板名字还是可以搜索的，那就没事了。

总结：建网站不容易，租服务器要花钱（一年几百），租域名也要花钱（一年几十）。
## Bacis computer knowledge

<a href="https://zhuanlan.zhihu.com/p/468515490">window的cmd命令行基本操作</a>

<a href="https://iknow.lenovo.com.cn/robot/knowledge/id/134435">windows10的快捷键操作</a>

### 关于环境变量
<a href="https://blog.csdn.net/jrl12345/article/details/106661324">CSDN的关于环境变量的理解</a>

环境变量是在操作系统中一个具有特定名字的对象，它包含了一个或者多个应用程序所将使用到的信息。当要求系统运行一个程序而没有告诉它程序所在的完整路径时，系统除了在当前目录下面寻找此程序外，还应到path中指定的路径去找。用户通过设置环境变量，来更好的运行进程。

### 举例
如下图，每个软件由.exe启动，而该程序一般有自己的安装路径。

<div align=center>
<img src="https://github.com/DearJohnsonny/CS_learning/assets/111955215/aaad52c6-f9fb-4e46-91ef-ed433db4962d" width="500">
</div>

而在windows的命令行中，如果我们不添加环境变量，直接运行matlab，有可能会找不到对象；所以需要输入下列代码才可以直接打开程序。

```
C:\Matlab\matlab_profiles\bin\matlab.exe
```

但是如果添加了环境变量，则在命令行中输入application.exe可以直接打开该程序

**为什么有的软件需要配置环境变量，有的软件就不需要？**

**A1：**
通常我们使用的软件（应用程序），比如QQ，微信，英雄联盟等都是一个应用程序（houzhui为.exe）,不需要配置环境变量
而当我们安装jdk，android sdk，python等应用程序时，我们是通过eclipse，myeclipse，idea，pycharm等另一个应用程序（ide）使用它们，所以要配置环境变量Path，让系统知道它们在哪里，以便咱们使用ide时可以调用它们

**A2：**
* 一些依赖关系简单的软件不需要修改环境变量。
* 比较人性化的环境类软件会自动安装在系统环境变量目录下，或者自动/手动添加目录到环境变量目录，我记得notepad++在安装时就提供“add to path”选项。
* 实际上，需要手动修改环境变量的软件极少，为数不多的软件典型如JDK、OpenCV，也是软件开发所需，使用者多为软件开发人员或计算机高端用户，所以也不存在壁垒问题


## Python_learning
### 一些理解
#### 关于创建类时的__init__方法

<a href="https://blog.csdn.net/m0_57290404/article/details/129735807?spm=1001.2101.3001.6650.3&utm_medium=distribute.pc_relevant.none-task-blog-2%7Edefault%7EYuanLiJiHua%7EPosition-3-129735807-blog-82822896.235%5Ev35%5Epc_relevant_default_base&depth_1-utm_source=distribute.pc_relevant.none-task-blog-2%7Edefault%7EYuanLiJiHua%7EPosition-3-129735807-blog-82822896.235%5Ev35%5Epc_relevant_default_base&utm_relevant_index=4">CSDN的关于init函数的理解</a>

定义一个类时，大家用得最多的就是 __init__ 方法。__init__方法负责对象的初始化。

Python是一门面向对象的编程语言，面向对象是一种代码封装的技术，包含了各种功能，让代码能重复利用、高效节能。我们通过class来定义类，类又包含了属性、方法等，属性是类里面的变量，方法是类里面的函数而__init__就是其中一种函数，叫做构造函数。通俗来讲，它就像是一个构造函数，当我们创建一个类的实例时，__init__方法会被自动调用，用于初始化对象的属性。 举个例子，如果我们定义了一个名为Person的类，那么在创建一个Person对象时，会自动调用__init__方法来为这个对象初始化属性。

* __init__() 方法的第一个参数必须是 self（self代表类的实例，可以用别的名字，但建议使用约定成俗的self），后续参数则可以自由指定，和定义函数没有任何区别。
* 带有两个下划线开头的函数是声明该属性为私有,不能在类地外部被使用或直接访问。
* init函数（方法）支持带参数的类的初始化 ，也可为声明该类的属性
* init函数（方法）的第一个参数必须是 self（self为习惯用法，也可以用别的名字），后续参数则可以自由指定，和定义函数没有任何区别。
### Class 类
第一个例子
```
class File:
    def __init__(self):
        self.name = "f1"
        self.create_time = "today"

my_file = File()
print(my_file.name)
print(my_file.create_time)
```
第二个例子
```

class Box:
    def setDimension(self, width, height, depth):
        self.width = width
        self.height = height
        self.depth = depth
 
    def getVolume(self):
        return self.width * self.height * self.depth
 
b = Box()
b.setDimension(10, 20, 30)
```

## Linux_learning
常见的版本有Ubuntu Fedora Debian等，做该笔记时采用版本为Ubuntu

<a href="https://www.cnblogs.com/LXP-Never/p/11607551.html#blogTitle11">关于装机器和计算机基本知识</a>

<a href="https://zhuanlan.zhihu.com/p/380119935">关于网络分层和协议</a>

部分内容引自网络博客，仅做学习笔记使用
### 数据处理
#### 正则表达式

<div align=center>
<img src="https://github.com/DearJohnsonny/Linux_learning/assets/111955215/57d62c2e-71b2-4fa5-8256-a50a8479ecb4" width="800">
</div>

下图为例子：

<div align=center>
<img src="https://github.com/DearJohnsonny/Linux_learning/assets/111955215/b8174005-d6d7-4a4e-b155-0c5ba5cc3dc9" width="800">
</div>

还有个比较常用的用法是锚定首行，尤其在我们做核酸序列的这里常用，下图为例子：

<div align=center>
<img src="https://github.com/DearJohnsonny/Linux_learning/assets/111955215/af92fede-cb66-4404-b8da-110ea1f469d5" width="800">
</div>

#### grep命令

<a href="https://cloud.tencent.com/developer/article/1554542">关于grep命令</a>

<a href="https://www.cnblogs.com/flyor/p/6411140.html">关于grep命令，这篇更好</a>

```
grep "ATC[AT]" test.txt # []括号用于匹配一组字符中的任何一个。 [1-3]表示连续的数字都可以

grep "^ATC" test.txt # 结合正则表达是进行查找

grep "TGC$" test.txt # 同上

grep "Class [^1-2]" Students.txt # 带方括号的脱字符号用于从搜索模式中排除字符。

```
#### awk命令
<a href="https://blog.csdn.net/Dark_Tk/article/details/114844529">CSDN的关于awk命令的博客，针不戳</a>

一些有意思的操作_通过管道、双引号调用 Shell 命令：

<div align=center>
<img src="https://github.com/DearJohnsonny/Linux_learning/assets/111955215/6fac9b79-7519-45bf-a3a6-2bc86bbb886d" width="1200">
</div>

常规操作：
```
awk '/^root/{print}' /etc/passwd		#输出以 root 开头的行

awk '/nologin$/{print}' /etc/passwd		#输出以 nologin 结尾的行

awk '(NR%2)==1{print}' name.txt 		#输出所有奇数行的内容

awk '(NR%2)==0{print}' name.txt		    #输出所有偶数行的内容

awk 'NR==1,NR==3 {print}' name.txt	    #输出第 1~3 行内容

awk 'NR==1;NR==3 {print}' name.txt	    #输出第 1和第3 行内容

awk '(NR>=1)&&(NR<=3) {print}' name.txt	#输出第 1~3 行内容

```
#### sed命令

<a href="https://www.cnblogs.com/zakun/p/linux-cmd-sed.html">非常全面的关于sed命令的博客</a>

##### 替换操作
```
sed 's/STR1/STR2/' test.txt ## 常规的sed操作，可以在真正替换前尝试一下;s是不能少的

sed 's/STR1/STR2/g' test.txt ## 可以将所有符合条件的字段全部替换了，而上文只能替换第一个匹配字段

sed -i 's/STR1/STR2' test.txt ## 带有 -i表示真正在修改txt文件，不带只是替换之后查看一下

sed -n 's/STR1/STR2/p' test.txt ## 将替换了字段的行单独摘出来
```

##### 删除操作
```
sed '2d' test.txt ## 删除第二行

sed '/^$/d' test.txt ## 删除空白行

sed '/^ATCG/d' test.txt ## 删除开头是ATCG的行

sed '/AGAGGTC$/d' test.txt ## 删除结尾是AGAGGTC的行
```
### 关于环境配置的理解
其实主要也就是/etc/profile和/home/john/.bashrc的理解

<a href="https://blog.csdn.net/u011262253/article/details/86083351">这是一个总结，下面也会多次提到</a>

#### /home/john/.bashrc的理解
下文也有提到:
```
# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi
```
起一个enable color和add handy aliases的作用

#### /etc/profile的理解
<a href="https://www.cnblogs.com/lh03061238/p/9952659.html">见此帖</a>
* 常在/etc/profile文件中修改环境变量，在这里修改的内容是对所有用户起作用的。以下主要操作将在该文件中进行。
* 使用修改.bashrc文件（在用户的家目录下）进行环境变量的编辑，只对当前用户有用。使用修改 /etc/profile 文件进行环境变量的编辑，是对所有用户有用。一定要注意区别。
* Linux profile文件在系统启动时将被运行。用户可以在里面加入其他命令，但是一定要加正确，不然的话系统会启动不起来的。

### 一些其他的理解
#### 关于常见的转义字符，要加echo -e
<a href="http://c.biancheng.net/linux/echo.html">见此帖</a>

echo的中文是回声的意思，在Linux中用于打印

转义字符，是 Shell 中的一些具有特殊功能的字符，比如 \n 表示换行、\t 表示制表符等。转义字符统一由反斜线“\”开头，后跟一个或几个字符，这样就赋予了字符“神奇的能力”。

在 echo 中，要使用转义字符，需要使用-e选项，并使用双引号将转义字符括起来。

此外，printf 命令也可以用来输出，它的使用方法类似于 C 中的 printf() 函数。

#### linux中的.d是什么意思
linux中“.d”文件表示的是：1、依赖文件，其中d是dependence的意思；2、默认配置文件，其中d是default的意思；3、动态意义的文件，其中d是Dynamic的意思。

<a href="https://www.php.cn/linux-490277.html#:~:text=linux%E4%B8%AD%E2%80%9C.d%E2%80%9D%E6%96%87%E4%BB%B6%E8%A1%A8%E7%A4%BA%E7%9A%84%E6%98%AF%EF%BC%9A1%E3%80%81%E4%BE%9D%E8%B5%96%E6%96%87%E4%BB%B6%EF%BC%8C%E5%85%B6%E4%B8%ADd%E6%98%AFdependence%E7%9A%84%E6%84%8F%E6%80%9D%EF%BC%9B2%E3%80%81%E9%BB%98%E8%AE%A4%E9%85%8D%E7%BD%AE%E6%96%87%E4%BB%B6%EF%BC%8C%E5%85%B6%E4%B8%ADd%E6%98%AFdefault%E7%9A%84%E6%84%8F%E6%80%9D%EF%BC%9B3%E3%80%81%E5%8A%A8%E6%80%81%E6%84%8F%E4%B9%89%E7%9A%84%E6%96%87%E4%BB%B6%EF%BC%8C%E5%85%B6%E4%B8%ADd%E6%98%AFDynamic%E7%9A%84%E6%84%8F%E6%80%9D%E3%80%82,%E6%9C%AC%E6%95%99%E7%A8%8B%E6%93%8D%E4%BD%9C%E7%8E%AF%E5%A2%83%EF%BC%9Alinux7.3%E7%B3%BB%E7%BB%9F%E3%80%81Dell%20G3%E7%94%B5%E8%84%91%E3%80%82">见此帖</a>

借助下面的代码帮助理解
```
if [ -d /etc/profile.d ]; then              # 判断/etc/profile.d 是不是一个目录。所以profile.d是搭配profile使用的
  for i in /etc/profile.d/*.sh; do       #如果是一个目录，到该目录下，取出每一个shell程序
    if [ -r $i ]; then                             #如果该shell可以执行

      . $i                                               # 则执行它
    fi
  done
  unset i
fi
```

#### /etc/passwd的理解
<a href="https://blog.csdn.net/xiaopang1122/article/details/105095684#:~:text=Linux%20%E7%B3%BB%E7%BB%9F%E4%B8%AD%E7%9A%84%20%2Fetc%2Fpasswd%20%E6%96%87%E4%BB%B6%EF%BC%8C%E6%98%AF%E7%B3%BB%E7%BB%9F%E7%94%A8%E6%88%B7%E9%85%8D%E7%BD%AE%E6%96%87%E4%BB%B6%EF%BC%8C%E5%AD%98%E5%82%A8%E4%BA%86%E7%B3%BB%E7%BB%9F%E4%B8%AD%E6%89%80%E6%9C%89%E7%94%A8%E6%88%B7%E7%9A%84%E5%9F%BA%E6%9C%AC%E4%BF%A1%E6%81%AF%EF%BC%8C%E5%B9%B6%E4%B8%94%E6%89%80%E6%9C%89%E7%94%A8%E6%88%B7%E9%83%BD%E5%8F%AF%E4%BB%A5%E5%AF%B9%E6%AD%A4%E6%96%87%E4%BB%B6%E6%89%A7%E8%A1%8C%E8%AF%BB%E6%93%8D%E4%BD%9C%E3%80%82%20%E5%90%8C,%2Fetc%2Fpasswd%20%E6%96%87%E4%BB%B6%E4%B8%80%E6%A0%B7%EF%BC%8C%E6%96%87%E4%BB%B6%E4%B8%AD%E6%AF%8F%E8%A1%8C%E4%BB%A3%E8%A1%A8%E4%B8%80%E4%B8%AA%E7%94%A8%E6%88%B7%EF%BC%8C%E5%90%8C%E6%A0%B7%E4%BD%BF%E7%94%A8%20%22%3A%22%20%E4%BD%9C%E4%B8%BA%E5%88%86%E9%9A%94%E7%AC%A6%EF%BC%8C%E4%B8%8D%E5%90%8C%E4%B9%8B%E5%A4%84%E5%9C%A8%E4%BA%8E%EF%BC%8C%E6%AF%8F%E8%A1%8C%E7%94%A8%E6%88%B7%E4%BF%A1%E6%81%AF%E8%A2%AB%E5%88%92%E5%88%86%E4%B8%BA%209%20%E4%B8%AA%E5%AD%97%E6%AE%B5%E3%80%82">见此帖</a>

Linux 系统中的 /etc/passwd 文件，是系统用户配置文件，存储了系统中所有用户的基本信息，并且所有用户都可以对此文件执行读操作。
执行函数后，可以得到以下输出:
```
root:x:0:0:root:/root:/bin/bash
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc:x:39:39:ircd:/run/ircd:/usr/sbin/nologin
gnats:x:41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
systemd-network:x:100:102:systemd Network Management,,,:/run/systemd:/usr/sbin/nologin
systemd-resolve:x:101:103:systemd Resolver,,,:/run/systemd:/usr/sbin/nologin
messagebus:x:102:105::/nonexistent:/usr/sbin/nologin
systemd-timesync:x:103:106:systemd Time Synchronization,,,:/run/systemd:/usr/sbin/nologin
syslog:x:104:111::/home/syslog:/usr/sbin/nologin
_apt:x:105:65534::/nonexistent:/usr/sbin/nologin
uuidd:x:106:112::/run/uuidd:/usr/sbin/nologin
tcpdump:x:107:113::/nonexistent:/usr/sbin/nologin
john:x:1000:1000:,,,:/home/john:/bin/bash
```
其分别代表的意义是（共九个字段）:用户名；加密密码；最后一次修改时间；最小修改时间间隔；密码有效期；密码需要变更前的警告天数；密码过期后的宽限时间；账号失效时间；保留字段

/etc/passwd应该与passwd命令区别开，这个是改用户密码的，我也不会退出，输错密码就行

#### 美元符号$的理解

<a href="https://blog.csdn.net/lenchio/article/details/8233256#:~:text=linux%E8%84%9A%E4%B8%AD%E7%BB%8F%E5%B8%B8%E4%BC%9A%E9%81%87%E5%88%B0%E7%BE%8E%E5%85%83%E7%AC%A6%E5%8F%B7%20%28%24%29%EF%BC%8C%E4%BB%A5%E4%B8%8B%E6%98%AF%E4%BB%96%E4%BB%AC%E4%BB%A3%E8%A1%A8%E7%9A%84%E5%90%AB%E4%B9%89%EF%BC%9A%20%240%20shell%E7%9A%84%E5%91%BD%E4%BB%A4%E6%9C%AC%E8%BA%AB,%28%E5%8C%85%E6%8B%AC%E5%AE%8C%E6%95%B4%E8%B7%AF%E5%BE%84%29%20%241%E5%88%B0%249%20%E6%95%B0%E5%AD%97%E8%A1%A8%E7%A4%BAshell%20%E7%9A%84%E7%AC%AC%E5%87%A0%E4%B8%AA%E5%8F%82%E6%95%B0">见此帖</a>

### 基本操作

<a href="https://www.cnblogs.com/savorboard/p/bash-guide.html#g.-mv">其实这个帖子写得很好，看它就够</a>

#### bash的操作

<div align=center>
<img src="https://user-images.githubusercontent.com/111955215/235345738-5e7d4a35-e28b-45b2-91a9-05ee80bbb89e.png" width="800">
</div>

许多 Bash 脚本会在文件首行加上 #!/bin/bash 。这里 #! 符号的名称是 shebang（也叫 sha-bang，即 sharp # 与 bang !）。当一个文本文件首行有 shebang，且以可执行模式执行时，shebang 后的内容会看作这个脚本的解释器和相关参数，系统会执行解释器命令，并将脚本文件的路径作为参数传递给该命令。

例如，某个foo.sh 首行为 #!/bin/bash，则执行./foo.sh 就等于执行 /bin/bash./foo.sh。
```
touch hello.sh

vim hello.sh

#!/bin/bash
I=John
She=dudu
echo "$I love $She"
```

#### touch的操作
touch是Linux常用的一条基本命令，它有如下两个功能：

（1）是用于把已存在文件的时间标签更新为系统当前的时间（默认方式），它们的数据将原封不动地保留下来；

（2）是用来创建新的空文件。

<a href="https://blog.csdn.net/JIEJINQUANIL/article/details/100941369#:~:text=touch%E6%98%AFLinux%E5%B8%B8%E7%94%A8%E7%9A%84%E4%B8%80%E6%9D%A1%E5%9F%BA%E6%9C%AC%E5%91%BD%E4%BB%A4%EF%BC%8C%E5%AE%83%E6%9C%89%E5%A6%82%E4%B8%8B%E4%B8%A4%E4%B8%AA%E5%8A%9F%E8%83%BD%EF%BC%9A,%EF%BC%881%EF%BC%89%E6%98%AF%E7%94%A8%E4%BA%8E%E6%8A%8A%E5%B7%B2%E5%AD%98%E5%9C%A8%E6%96%87%E4%BB%B6%E7%9A%84%E6%97%B6%E9%97%B4%E6%A0%87%E7%AD%BE%E6%9B%B4%E6%96%B0%E4%B8%BA%E7%B3%BB%E7%BB%9F%E5%BD%93%E5%89%8D%E7%9A%84%E6%97%B6%E9%97%B4%EF%BC%88%E9%BB%98%E8%AE%A4%E6%96%B9%E5%BC%8F%EF%BC%89%EF%BC%8C%E5%AE%83%E4%BB%AC%E7%9A%84%E6%95%B0%E6%8D%AE%E5%B0%86%E5%8E%9F%E5%B0%81%E4%B8%8D%E5%8A%A8%E5%9C%B0%E4%BF%9D%E7%95%99%E4%B8%8B%E6%9D%A5%EF%BC%9B%20%EF%BC%882%EF%BC%89%E6%98%AF%E7%94%A8%E6%9D%A5%E5%88%9B%E5%BB%BA%E6%96%B0%E7%9A%84%E7%A9%BA%E6%96%87%E4%BB%B6%E3%80%82">具体见此帖子</a>

#### vim的操作
* 进入输入模式:单击””键进入输入模式，这时可以对文件进行插入、删除等操作。单击“Esc"回到命令模式
* 进入末行模式:单击”:"键进入末行模式。该模式下可以保存刚刚编辑的内容，具体操作是单击w”；单击"q"可退出vim；q!是强制退出
* 
#### 一些快捷键
ctrl + p :逐渐向前搜索历史记录

ctrl + n :向后搜索历史记录

ctrl + r :直接按关键词搜索历史记录

ctrl + l :刷屏到最上面

ctrl + u :清除指针前面的所有内容


<div align=center>
<img src="https://user-images.githubusercontent.com/111955215/235349392-7baa3d61-331b-41e9-b076-b5f17bca0804.png" width="1500">
</div>

#### 一些常用操作
* 查看配制的环境:
```
echo $PATH
```
* 打开jupyter，输入:
```
jupyter-notebook
```
点进最下面的链接
编辑完后，回到linux界面，ctrl + c，y退出

* 输入多Line文本，可以：
```
cat > name.txt << EOF
this is the first line
this is the 2nd line
this is the 3rd line
this is the 4th line
EOF
```
* 如果想去除重复行显示某多行文本，可以:
```
sort filename.txt | uniq -c
```
uniq去重复，但是只对连续行有用，所以需要和sort一起连用；而-c可以显示某行总共重复次数

* 用tree显示文件夹子目录格局，小文件夹会一直跑，一般会:
```
tree -L 3|less
```
3表示显示子树的层级，
也可以直接ls -l
我们加入了la = ls -al的操作，直接la即可

* 在wsl中搜索windows系统的内容的操作：
```
cd /home/john/mnt
cd c
cd d
```
* 换用户的操作
```
sudo su root
```
上面的sudo表示权限，而su表示更换用户，root是管理员权限
输入上述命令后发现颜色变为灰白色
再输入
```
source /home/john/.bashrc
```
就能发现命令行由白色上色了（因为bash中定义了color = auto，cat /home/john/.bashrc后可以看到下面的内容）

```
# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi
```

<div align=center>
<img src="https://user-images.githubusercontent.com/111955215/235342547-49149740-f24c-4856-8235-4cc29aa29693.png" width="800">
</div>

#### 要编写alias定义长期的函数
可以输入
```
vim /home/john/.bashrc_aliases
```
然后在vim模式下按  ':',再编辑（如下）
```
alias py39='conda activate py39'
alias pyb='conda activate base'
alias la='ls -al --color=auto'
```
