# 黑苹果系列
![writter](https://img.shields.io/badge/%E4%BD%9C%E8%80%85-zwiss%20cai-brightgreen)
[![website](https://img.shields.io/badge/%E9%A6%96%E5%8F%91-%E4%BB%80%E4%B9%88%E5%80%BC%E5%BE%97%E4%B9%B0-red)](https://post.smzdm.com/p/a5k6q4dl/)



![题图](https://qna.smzdm.com/201907/16/5d2d459320ee16660.jpg_fo742.jpg)
## 前言
这篇文章记录了我一次成功安装黑苹果的过程。虽然安装黑苹果比较费事，但是如果用对方法和硬件的话，整个安装过程还是比较顺畅的。虽然标题是小白的黑苹果实录，不过这篇文章更适合有一定DIY装机经验的值友来参考就是了。（第一篇文章，若有不正确的地方还请大佬指正）

在安装方法上是按照tonymacx86一套相对成熟教程来安装的，tonymacx86是国外一个比较大的黑苹果社区，他们有制作一套软件来帮助普通用户来制作启动盘、打驱动补丁等，同时这些软件目前还在更新维护，所以如果出现问题的话也总是能找到解决方案（不过需要一定的英语水平）。另外我在硬件选择上都是选了能在macOS下免驱的硬件（同时是第一次安装，就选了便宜的硬件来尝试），这样在后续安装过程就比较顺畅。

文章的最后我会附上一些我参考的文章。

* 制作系统启动盘
* 安装系统
* 驱动显卡（GT740）
* 驱动无线网卡（360随身Wi-Fi 2代）

我参考的各种文章链接

## 选择硬件


预先在国内外各种论坛网站里瞎逛，像国内知名的远景，国外的tonymacx86。最后锁定了用tonymacx86上的方法来安装黑苹果。同时我也参考了油管上一个Ultra budget $65 Hackintosh - 2017（65刀5超低预算黑苹果配置）的视频，这个视频是用tonymacx86（后面简称T站了）上给的安装方法来安装的，感觉比其他论坛上的方法来的简单。所以这篇文章主要参考了那个视频。下面我逐步介绍整个安装过程，和我遇到的一些问题及解决方法。

首先是选择硬件和系统：

安装黑苹果比较关键的两个硬件是：主板和显卡。主板这里我选择和油管up主相同的技嘉G41MT-S2PT。显卡这里原本我参考黑果小兵的mojave硬件支持列表中AMD HD7850，上某鱼搞了一块华硕 HD7850 1GB，但是后面安装系统时发现进入系统前就黑屏了，后来爬T站看到一个和我主板一眼的帖子用了华硕GTX550TI，于是又在某鱼上找了一个一样的但是发现进系统时还是黑屏。最后换了七彩虹GT740 2GB DDR5。

系统一开始我是打算安装mojave的，但是后来查了一些资料发现775平台的CPU不适合安装mojave。尤其是使用AMD的免驱显卡时。按网友的说法是775平台CPU不支持sse4.2，而AMD免驱的显卡需要用到这个，具体的细节我也不太清楚，网上似乎有工具解决这个问题，但是我为了稳定，只好放弃黑暗模式选择High Sierra了。

最终硬件配置是：

CPU：英特尔E8500 3.0GHz
主板：技嘉G41MT-S2PT（2.1版）
显卡：七彩虹GT740 2GB DDR5
内存：杂牌DDR3 1333 4+2GB
硬盘：西数500GB 机械硬盘

其他不影响安装黑苹果的硬件就不贴出来了，反正都是上古硬件。

## 制作启动盘
按照T站的方法，制作启动盘需要在mac下完成。这里我就只好厚着脸皮借了同学的mac完成了（这也是这个方法唯一不太友好的地方）。T站给的系统下载方法是用mac 的app store 里下载系统，但是不知道是我的网络有问题还是苹果服务器的问题，总是下到一半就出错，要从新开始下载。最后我找到了macOS High Sierra Patcher Tool，下载到了原生的系统。下载完成后你的启动台里面就会多出一个“安装High Sierra”的软件，这个时候就代表你下载完成了

![打开macOS High Sierra Patcher Tool在菜单里面选择下载系统](http://dosdude1.com/highsierra/tutorialimages/downloadMacOS.png)

题外话：黑果小兵里面也有带Clover的系统下载，可以用transmac在Windows系统下制作启动盘，但是只能做EFI启动盘，这里我的主板不支持就没有试过这个方法。

然后就是使用T站的UniBeast制作启动盘（需要且注册账户后才能下载），用这个软件前需要把系统语言改成英语。这里根据你要按照的系统选择不同版本的UniBeast来安装。

1.插入U盘，打开Disk Utility（系统自带），注意在“显示”选择“显示所有设备”之后在选中你的U盘

![选择U盘](https://www.tonymacx86.com/attachments/screen-shot-2016-09-12-at-9-36-54-am-png.210183/)
选择U盘

2.选择“抹掉”，格式选择“Mac OS Extended (Journaled)”

![格式化U盘](https://www.tonymacx86.com/attachments/screen-shot-2016-09-12-at-9-37-44-am-png.210182/)格式化U盘

完成后即可打开UniBeast,依次选择你的U盘、选择你要安装的系统，选择启动模式（UEFI和传统），选择显卡注入（可选，这里我没有勾选）。之后等待一会儿就OK啦。（以上图片来自T站）

## 安装系统
安装系统这里就比较简单了，BIOS这里我没有做任何修改，直接选择U盘启动，进入到Clover的界面下选择Boot OS X Install from Install macOS High Sierra，进入安装界面后，同制作启动盘一样先用Disk Utility把要安装到的硬盘格式化（这里我是安装单系统，双系统没有尝试也没有打算），然后就正常开始安装。之后电脑会重启一次，重启后在Clover的界面选择多出来的Install macOS High Sierra继续安装。

注：如果重启后安装到一半提示系统空间不足的话回到格式化硬盘那一步Disk Utility下“显示所有设备”后在选择有倒三角的那行来格式化。

不出意外的话这里就进入初始化设置界面了，进入系统后用MultiBeast 来安装Clover和其他驱动。

![选择Legacy Boot mode](https://www.tonymacx86.com/attachments/screen-shot-2016-09-27-at-10-55-44-am-png.212542/)选择Legacy Boot mode

![注入声卡的驱动](https://qnam.smzdm.com/201907/16/5d2d1990d7a364319.png_e680.jpg)
注入声卡驱动

   

![保持默认](https://qnam.smzdm.com/201907/16/5d2d1990c65099319.png_e680.jpg)
保持默认

![Install!](https://qnam.smzdm.com/201907/16/5d2d19911ed015491.png_e680.jpg)
安装

这里因为我买到的主板是2.1版本的，相比油管视频里的那个1.0版本网口更换了，以至于没有办法在这里直接安装对应的驱动了，后面因为用了USB网卡也就没有在意这里了。

完成后在用Clover Configurator先在挂载分区中找到对应的EFI分区挂载并且打开，按照下图里的路径打开config.plist然后在启动参数中增加nvda_drv=1。最后重启系统就大功告成了！


至此我的黑苹果安装就是这样了，之后或许会出一个T站使用指南以及如何驱动360随身Wi-Fi2代的小教程吧。

欢迎各位值友留言交流（别问太难的问题呀）

参考文章

Ultra budget $65 Hackintosh - 2017（油管视频）

[UniBeast: Install macOS Mojave on Any Supported Intel-based PC](https://www.tonymacx86.com/threads/unibeast-install-macos-mojave-on-any-supported-intel-based-pc.259381/)

[【黑果小兵】macOS Mojave 10.14.5 18F132 正式版 with Clover 4928原版镜像](https://blog.daliansky.net/macOS-Mojave-10.14.5-18F132-official-version-with-Clover-4928-original-image.html)

[macOS安装教程兼小米Pro安装过程记录](https://blog.daliansky.net/MacOS-installation-tutorial-XiaoMi-Pro-installation-process-records.html)

[Mojave硬件支持列表（持续更新中）](https://blog.daliansky.net/Mojave-Hardware-Support-List.html)

[macOS High Sierra Patcher Tool for Unsupported Macs](http://dosdude1.com/highsierra/)

