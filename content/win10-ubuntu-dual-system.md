Title: 在已有win10的电脑上装ubuntu18.04双系统
Date: 2019-09-27
Category: Misc
Modified: 2019-09-27 23:11
Tags: Ubuntu

# 动机
家里的台式机有GPU(Nvidia 1060 6G)，但是一直拿来玩游戏，开始是说要学习机器学习才用爸爸的钱买的。为了完成当初的flag，打算在已有的Win10操作系统的基础上装Ubuntu，并且使用Windows作为引导(在网上看到如果用Ubuntu引导的话可能重装Ubuntu会影响Windows，毕竟很多游戏存档都在Windows里面，所以你懂的)。在网上搜了一些教程，现总结一下安装Ubuntu的基本流程。

# 先决条件
我的台式机好像不支持UEFI，所以需要用Universal USB Installer，一开始使用了rufus各种bug，后来重新烧了一下就好了，基本安装流程和[参考资料1](https://blog.csdn.net/fesdgasdgasdg/article/details/54183577)类似(其实一开始看的不是这个教程，但是后来找不到了，这个和原来看的差不多)

# 具体步骤
 * 把Ubuntu的iso镜像通过Universal USB Installer写入U盘
 * 开机进入BIOS选择U盘启动
 * 参考资料1中的安装步骤，注意分区时要选择其他
 * 我的分区策略：
    * / 40G 主分区
    * SWAP 16G 逻辑分区
    * /boot 200M 逻辑分区
    * /home 有多少用多少
* 注意启动项要选择/boot对应的目录，这样可以在Windows里面通过Easy BCD进入Ubuntu
* 安装完成后重启，默认时进入Win10的，此时安装Easy BCD，然后在`添加新条目` -> `驱动器`选择刚才`/boot`对应的那个分区
* 然后再重启的时候就可以选择Ubuntu啦！