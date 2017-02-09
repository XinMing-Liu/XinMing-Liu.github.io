---
title: Android 开发环境配置
categories: Android 开发
---

##开发环境配置
    android开发，首先建议使用ubuntu或者使用Moc，当然对我这样的穷屌丝。moc是买不起的我只能使用ubuntu了。至于为什么要这样做那，理解android机制或者有过ROM开发经验的都会知道，对于处入门的小白可以不必纠结直接上ubuntu就行了。
###1、Ubuntu 安装
ubunu安装其实很简单网上有很多教程我这里就不一一展开说了,可以参考以下链接安装
[baidu](http://jingyan.baidu.com/article/a378c9609aaf4eb3282830e6.html)

安装好ubutun，接下来就是安装android开发的必要环境及工具：([如果你可以翻墙可以参考谷歌官方推荐安装](http://source.android.com/source/initializing.html))
* [openjdk安装并配置环境变量](http://www.cnblogs.com/madyina/p/3705520.html)
* android 源码编译必要工具
` sudo apt-get install git gnupg flex bison gperf build-essential zip curl libc6-dev libncurses5-dev:i386 x11proto-core-dev libx11-dev:i386 libreadline6-dev:i386 libgl1-mesa-dri:i386 libgl1-mesa-dev g++-multilib mingw32 tofrodos python-markdown libxml2-utils xsltproc zlib1g-dev:i386 dpkg-dev`
`sudo ln -s /usr/lib/i386-linux-gnu/mesa/libGL.so.1 /usr/lib/i386-linux-gnu/libGL.so`
* 设置usb权限（将如下内容加入到/etc/udev/rules.d/51-android.rules文件中）
```
# adb protocol on passion (Nexus One)  
SUBSYSTEM=="usb", ATTR{idVendor}=="18d1", ATTR{idProduct}=="4e12", MODE="0600", OWNER="<username>"  
# fastboot protocol on passion (Nexus One)  
SUBSYSTEM=="usb", ATTR{idVendor}=="0bb4", ATTR{idProduct}=="0fff", MODE="0600", OWNER="<username>"  
# adb protocol on crespo/crespo4g (Nexus S)  
SUBSYSTEM=="usb", ATTR{idVendor}=="18d1", ATTR{idProduct}=="4e22", MODE="0600", OWNER="<username>"  
# fastboot protocol on crespo/crespo4g (Nexus S)  
SUBSYSTEM=="usb", ATTR{idVendor}=="18d1", ATTR{idProduct}=="4e20", MODE="0600", OWNER="<username>"  
# adb protocol on stingray/wingray (Xoom)  
SUBSYSTEM=="usb", ATTR{idVendor}=="22b8", ATTR{idProduct}=="70a9", MODE="0600", OWNER="<username>"  
# fastboot protocol on stingray/wingray (Xoom)  
SUBSYSTEM=="usb", ATTR{idVendor}=="18d1", ATTR{idProduct}=="708c", MODE="0600", OWNER="<username>"  
# adb protocol on maguro/toro (Galaxy Nexus)  
SUBSYSTEM=="usb", ATTR{idVendor}=="04e8", ATTR{idProduct}=="6860", MODE="0600", OWNER="<username>"  
# fastboot protocol on maguro/toro (Galaxy Nexus)  
SUBSYSTEM=="usb", ATTR{idVendor}=="18d1", ATTR{idProduct}=="4e30", MODE="0600", OWNER="<username>"  
# adb protocol on panda (PandaBoard)  
SUBSYSTEM=="usb", ATTR{idVendor}=="0451", ATTR{idProduct}=="d101", MODE="0600", OWNER="<username>"  
# adb protocol on panda (PandaBoard ES)  
SUBSYSTEM=="usb", ATTR{idVendor}=="18d1", ATTR{idProduct}=="d002", MODE="0600", OWNER="<username>"  
# fastboot protocol on panda (PandaBoard)  
SUBSYSTEM=="usb", ATTR{idVendor}=="0451", ATTR{idProduct}=="d022", MODE="0600", OWNER="<username>"  
# usbboot protocol on panda (PandaBoard)  
SUBSYSTEM=="usb", ATTR{idVendor}=="0451", ATTR{idProduct}=="d00f", MODE="0600", OWNER="<username>"  
# usbboot protocol on panda (PandaBoard ES)  
SUBSYSTEM=="usb", ATTR{idVendor}=="0451", ATTR{idProduct}=="d010", MODE="0600", OWNER="<username>"  
# adb protocol on grouper/tilapia (Nexus 7)  
SUBSYSTEM=="usb", ATTR{idVendor}=="18d1", ATTR{idProduct}=="4e42", MODE="0600", OWNER="<username>"  
# fastboot protocol on grouper/tilapia (Nexus 7)  
SUBSYSTEM=="usb", ATTR{idVendor}=="18d1", ATTR{idProduct}=="4e40", MODE="0600", OWNER="<username>"  
# adb protocol on manta (Nexus 10)  
SUBSYSTEM=="usb", ATTR{idVendor}=="18d1", ATTR{idProduct}=="4ee2", MODE="0600", OWNER="<username>"  
# fastboot protocol on manta (Nexus 10)  
SUBSYSTEM=="usb", ATTR{idVendor}=="18d1", ATTR{idProduct}=="4ee0", MODE="0600", OWNER="<username>"
```
* [git](http://blog.csdn.net/abclixu123/article/details/46464089) 及 [repo](http://source.android.com/source/downloading.html)安装没有什么难度，问一下度娘相信你一定能找到你满意的答案

---
以上操作成功可以下载一套安装源码试一下：[国内镜像下载Android源码](http://blog.csdn.net/konga/article/details/49970577)
使用国内的镜像服务器下载，可以减少时间。安卓源码sync结束请直行以下指令
```
source build/envsetup.sh
lunch aosp_flo-userdebug
make -j8
```
编译结束生成的文件都在out目录下。

* 除此之外我还习惯使用如下工具
meld（对比工具），sublime（文本编辑工具），TeamView（远程控制工具）
### 2、安装eclipse及AS







