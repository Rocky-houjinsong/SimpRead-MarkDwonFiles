> 本文由 [简悦 SimpRead](http://ksria.com/simpread/) 转码， 原文地址 [zhuanlan.zhihu.com](https://zhuanlan.zhihu.com/p/339908228?utm_id=0)

> windows 用户如想使用 linux 有一个非常简单的方法，就是开启 windows 下的 linux 子系统，也叫做 WSL(Windows Subsystem for Linux)，下面简述一下安装过程。

windows 用户如想使用 linux 有一个非常简单的方法，就是开启 windows 下的 linux 子系统，也叫做 WSL(Windows Subsystem for Linux)，下面简述一下安装过程。

首先打开控制面板，程序功能下面的开启或关闭 windows 功能

![](https://pic1.zhimg.com/v2-3f9883bba9dba0153712b196239862a0_r.jpg)

然后再下面这个界面勾上适用于 Linux 的 Windows 子系统

![](https://pic1.zhimg.com/v2-7a69f3b2f245b0ab61ebe3ec81e58020_r.jpg)

这还没完，接下来打开 Microsoft Store，搜索 Ubuntu，也就是下面这个，我这里已经安装了。正常未安装的话会有一个 “获取” 的按钮，点击即可。

![](https://pic4.zhimg.com/v2-ca9479e036e212200c1294956d411adf_r.jpg)

接下来在 cmd 中可用 wsl -l 指令来查看子系统，输入 bash 即可进入子系统。

![](https://pic4.zhimg.com/v2-58d82064874d7e83e4cb1d17e26f46f3_r.jpg)

这样我们就安装好了这个 Linux 子系统，用户目录是 / home/user，C 盘目录是 / mnt/c。但是这个子系统其实是在 C 盘上的，如果你要在上面配置一些环境可能会大量占用 C 盘空间，未来保证系统盘空间充足，我们还要将其迁移到非系统盘 (下面以 D 盘为例)。

首先下载一个 WSL 的管理工具叫 LxRunOffline，github 地址是[这里](https://github.com/DDoSolitary/LxRunOffline/releases)。本文以版本 v3.4.0 为例。

![](https://pic1.zhimg.com/v2-194bc07843526f99fbf8efa70ccf4f9c_r.jpg)

下载后在其目录下，shift + 鼠标右键开启 powershell，之后可以通过

```
.\LxRunOffline.exe list   查看可用的子系统
.\LxRunOffline.exe move -n Ubuntu -d D:\WSL 
将Ubuntu放在D盘的WSL文件夹下(-n指定迁移的系统，-d指定迁移路径)

```

![](https://pic4.zhimg.com/v2-d95f8bbb378b40e05a44d2d54835b47b_r.jpg)

之后可以使用

```
.\LxRunOffline.exe get-dir 查询系统目录

```

![](https://pic4.zhimg.com/v2-5753a1c4a4c072b8dbf89f207ef9dfcf_r.jpg)

可见已经迁移成功！