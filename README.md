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

#### IP地址

<div align=center>
<img src="https://github.com/DearJohnsonny/CS_learning/assets/111955215/82165cef-e049-4292-95b7-eec3912b4d67" width="1500">
</div>

<div align=center>
<img src="https://github.com/DearJohnsonny/CS_learning/assets/111955215/20f79e23-0aa9-44b7-b82a-51c28659f872" width="800">
</div>

从上图可以看出来，北医的校园网是B类IP地址，因此前两位是网络层。而下图的PC机遇cellphone分发的IP地址虽然不同，但是前两位的数字是一样的，说明了是位于同一个子网下面的。

<div align=center>
<img src="https://github.com/DearJohnsonny/CS_learning/assets/111955215/4f3a01cf-e90b-47e4-aa6c-ebc4a98ce97d" width="800">
</div>

而在cmd中输入ipconfig之后发现WSL这个虚拟机的地址与真正的校园网的地址不同，是C类IP地址，但是最终的子网掩码是一样的，证明还是在同一个IP地址下面。

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
