**clion配置stm32配置教程**（我踩的坑）

## 首先需要下载clion这个软件，[jetbrains官网](https://www.jetbrains.com/zh-cn/)

然后下载**clion**即可，会有30天的免费试用，在校学生的话最好用学校给注册的邮箱在jetbrains官网

进行认证即可。

### 然后需要下载**stm32cumax**这个软件，[stm32cubemx官网]()进行下载即可

#### 需要三个 配置环境 ，openocd，mingw64，arm-none-eabi

openocd的官网，[点这个](https://gnutoolchains.com/arm-eabi/openocd/)然后下载压缩包，OpenOCD旨在提供针对嵌入式设备的调试、系统编程和边界扫描功能。OpenOCD的功能是在仿真器的辅助下完成的，仿真器是能够提供调试目标的电信号的小型硬件单元。仿真器是必须的，因为调试主机（运行OpenOCD的主机）通常不具备这种电信号的直接解析功能。

MinGW，是*Minimalist [GNU](https://baike.baidu.com/item/GNU)for Windows*的缩写。它是一个可自由使用和自由发布的Windows特定[头文件](https://baike.baidu.com/item/头文件/10978258)和使用GNU工具集导入库的集合，允许你在[GNU](https://baike.baidu.com/item/GNU)/[Linux](https://baike.baidu.com/item/Linux)和[Windows](https://baike.baidu.com/item/Windows)平台生成本地的Windows程序而不需要第三方C运行时（C Runtime）库。MinGW 是一组包含文件和端口库，其功能是允许控制台模式的程序使用微软的标准C运行时（C Runtime）库（[MSVCRT.DLL](https://baike.baidu.com/item/MSVCRT.DLL)）,该库在所有的 NT OS 上有效，在所有的 [Windows 95](https://baike.baidu.com/item/Windows 95)发行版以上的 Windows OS 有效，使用基本运行时，你可以使用 GCC 写控制台模式的符合美国标准化组织（ANSI）程序，可以使用微软提供的 C 运行时（C Runtime）扩展，与基本运行时相结合，就可以有充分的权利既使用 CRT（C Runtime）又使用 Windows[API](https://baike.baidu.com/item/API)功能。
链接：https://www.jianshu.com/p/427ed0f03ec4

arm-none-eabi，交叉编译器。[下载地址](https://launchpad.net/gcc-arm-embedded/+download)下载安装即可

**网上下载的贼慢，然后我打包好了**

**链接：https://pan.baidu.com/s/1YUrs7CxWCB6VslX4WIzqUg 
提取码：hjk6 
复制这段内容后打开百度网盘手机App，操作更方便哦***

##### 这三个环境装完之后，（win10可以装在别的盘中），然后配置环境，打开我的电脑，右键属性，高级系统设置，环境变量，然后在下面的系统变量中找到path这个，然后编辑，新建，然后分别进到你装的那三个软件的位置，然后进到bin目录下，如（C:\GNU_Tool_Arm_Embedded\bin），然后三个确定，一共有三个，三个都是这样的。

![](https://i.loli.net/2021/05/03/ZS2OGlvpJrRmBia.png)

**完全配置好环境如下图**

![](https://i.loli.net/2021/05/03/LbCgJV4IWmRZuAP.png)

**到这里运行环境已经完全完成了**

**可以在命令行中进行验证，是否环境配置好了**

**命令是 gcc -v 和 arm-none-eabi-gcc -v **

**然后会出现版本信息**

![](https://i.loli.net/2021/05/03/irGECIMmJnzd6eR.png)



**然后打开clion**

![](https://i.loli.net/2021/05/03/H3QDe5vrzFAxodb.png)

**上面那个创建工程的时候那个文件名要注意，后面要和stm32cubemx里相对应**



**值得一提的是jetbrains家的软件都支持插件功能，在那个plugin那里可以找到汉化包，直接下载安装重新打开即可**



**如下图**

![](https://i.loli.net/2021/05/03/e3jphJdY7zUMHVZ.png)



**然后是**

![](https://i.loli.net/2021/05/03/nUlmKxvcPgzHyf5.png)

**点击在stm32cubemx打开**



**然后进到stm32cubemx这个软件**



![](https://i.loli.net/2021/05/03/s2PiSuH6y1D7FjE.png)

**通过上面的mcumpu那里可以选你对应的芯片，选好之后，直接双击即可**



**然后是一些配置选项**

![](https://i.loli.net/2021/05/03/8y4sFwt9oWQ1BXc.png)

![](https://i.loli.net/2021/05/03/V73MPIrNOmqBQZt.png)

**最后是最重要的那个项目管理那里，名字要和之前clion的对应**

![](https://i.loli.net/2021/05/03/iDM3GCVpwlOh9FN.jpg)

**需要特别注意的是项目名字下面那个选项，项目位置。注意，在第一步的时候，我们在clion里创建项目的时候，那个文件下面已经有了demo1文件**

![](https://i.loli.net/2021/05/03/mVg1wRroJuTD57U.png)

**然后这里我们不进去那个demo1文件，在demo1的上一级目录创建，也就是相当于再创建一个demo1文件**



**这里我之前一直在踩坑**



**然后点击右上角的general code 生成代码，会提示**

![](https://i.loli.net/2021/05/03/oPj6l5MEHOrkLZW.png)

**这里对应我上面说的，他的意思是，demo1文件已经存在了，问你是否要修改**

**点击yes**

**接着clion右下角会弹出提示，然后会弹出烧录面板选择，也就是之前配的openocd**

![](https://i.loli.net/2021/05/03/T9qsPAEUztFi5Yn.png)

![](https://i.loli.net/2021/05/03/n6gmckUM9S3L8Yt.png)

**这样就配置好了**

![](https://i.loli.net/2021/05/03/NpxK7tZjSeuJ5F1.jpg)

**点击小锤子是编译，然后下面提示出现.hex文件，就可以了，然后那个三角是下载，这个下载需要那个openocd那个配置文件，具体芯片的配置文件不一样**

**代码下载成功会提示**

![](https://i.loli.net/2021/05/03/M5IQB6DF4vtGxJR.png)

**会显示多少字节，右下角也会提示**



**为我所踩过的坑，祭奠一下**



**keil 搭配stm32cubemx也是一样的，但是clion更好看，也更流行，jetbrains的全家桶哈哈哈**

