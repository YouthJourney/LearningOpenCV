## 有关Visual Studio 2015+openCV3.4.1安装和配置问题 ##
### 1、下载 ###
- vs2015下载  
官方下载下载地址：https://visualstudio.microsoft.com/zh-hans/vs/older-downloads/  
其他下载地址：https://msdn.itellyou.cn/  
百度网盘资源：链接：https://pan.baidu.com/s/1C3C6Fm8SA3F0ug5gRtSqIg 
提取码：inya（企业版）链接：https://pan.baidu.com/s/1KRnMY1QSaCfMTLRiR36LVw 
提取码：5dvh（社区版）
- vs2015各版本密钥  
Visual Studio Professional 2015简体中文版（专业版）  
KEY：HMGNV-WCYXV-X7G9W-YCX63-B98R2  
Visual Studio Enterprise 2015简体中文版（企业版）  
KEY：HM6NR-QXX7C-DFW2Y-8B82K-WTYJV
- openCV3.4.1下载  
官方下载地址：https://opencv.org/  
百度网盘资源：链接：https://pan.baidu.com/s/1-NfDxXu4qrAQyRLRfahO6Q 
提取码：2jz3  
### 2、安装 ###
- vs2015的安装   
首先解压你所下载的压缩包，在里面找到vs_enterprise.exe双击运行，就出现了安装界面，选择安装路径后再选择自定义安装，在里面选择你所需要安装的功能，以我的enterprise版本为例，我只选择了update3和C++语言，点击下一步进入漫长的安装过程。
- openCV3.4.1安装  
直接将opencv-3.4.1-vc14_vc15.exe双击，然后解压到安装路径，之后在path里面添加环境变量，如本人添加的为：D:\OpenCV3.4.1\opencv\build\bin
### 3、vs2015里配置opencv3.4.1环境 ###
- 配置属性表  
这个百度一下多的是本人在这里就不再重复了，详情请参考：https://blog.csdn.net/cherishlicoolboy/article/details/81195364
- 调试别人的程序(以《OpenCV3编程入门》OpenCV3版书本配套程序为例)  
***错误1***  
![加载错误](https://i.imgur.com/BpQiupd.png)  
如上图打开一个别人的项目弹出是加载错误，可以通过以下方法解决：    
![项目文件夹](https://i.imgur.com/R7DFDEO.png)  
打开项目文件夹找到vcxproj，使用记事本打开：  
![找到文件](https://i.imgur.com/i5pqHwm.png)  
找到上图框中的属性表文件，将其路径改成自己本机这个属性表的路径，本人的该表在E盘更目录，就将其全部换成E:\OpenCV3.4.1.props  
然后保存，在vs中执行下列操作：  
![重新加载](https://i.imgur.com/URo51JZ.png)  
在该项目上右键选择重新加载项目，此问题就轻松解决了。  
***错误2***  
关于支持向量机的两个程序，再用opencv3.0以上版本时会出现代码错误，解决办法可以参考：https://blog.csdn.net/qq_29762941/article/details/79723359  
***错误3***  
关于点追踪程序，它会提示goodFeaturesToTrack函数参数不匹配，这是因为里面有两个参数是double类型，它写成了int类型导致找不到对应的参数列表与之匹配，需要将第五个和第八个参数改成double类型，即在后面加上"**.00**"  
***错误4***  
打开项目后会发现提示说打不开opencv头文件，即如下错误:  
![文件无法打开](https://i.imgur.com/uPr8PRC.png)  
这是因为关于opencv的配置没有导入进来，你可以重新配置，也可以导入你最开始配置的属性表，本人建议后者方式，做法如下：  
![属性管理器](https://i.imgur.com/QIlZ22L.png)  
打开属性管理器再右键点击debug×64（因为本人配置属性表为这个版本），选择添加现有项。如下：
![添加](https://i.imgur.com/PIO60t3.png)  
添加进去后程序就可以正常运行了。  
  
*以上便是本人对这次配置环境即调试程序一些总结，希望能给大家带来一点帮助，有问题请在Issues中给本人留言。*