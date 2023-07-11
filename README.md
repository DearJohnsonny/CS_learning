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
