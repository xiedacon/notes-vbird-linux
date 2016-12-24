# 开机流程、模块管理与Loader

### Linux开机流程分析

#### 开机流程

1. 加载BIOS的硬件信息与进行自我测试，并依据设定取得第一个可开机的装置
2. 读取并执行第一个开机装置内MBR的boot Loader，即grub、spfdisk等程序
3. 依据boot loader的设定加载Kernel，Kernel会开始检测硬件与加载驱动信息
4. 在硬件驱动成功后，Kernel会主动呼叫init程序，而init会取得run-level信息
5. init执行/etc/rc.d/rc/sysinit档案来准备软件执行的作业环境
6. init启动run-level的各个服务
7. init执行/etc/rc.d/rc.local档案
8. init执行终端机仿真程序mingetty来启动login程序，等待用户登录

#### BIOS，boot loader与kernel载入

* BIOS，开机自我测试与MBR

* Boot Loader的功能

![](/assets/boot loader安装在MBR,boot sector与操作系统的关系.png)

1. 提供选单：用户可以选择不同的开机项目，即多重引导
2. 载入核心档案：直接指向可开机的程序区段来开始操作系统
3. 转交其它loader：将开机管理功能转交给其它loader负责

![](/assets/开机管理程序的选单功能与控制权转交功能示意图.png)

* 加载核心检测硬件与initrd的功能

![](/assets/BIOS与boot loader及核心加载流程示意图.png)

####第一支程序init及配置文件/etc/inittab与runlevel

* runlevel

|等级|意义|
|--|--|
|0|halt（系统直接关机）|
|1|single user mode（单人模式）|
|2|Multi-user,without NFS（无NFS服务）|
|3|Full multi-user mode（含有网络功能的纯文本模式）|
|4|unused（系统保留功能）|
|5|X11（X Window）|
|6|reboot（重新启动）|

* init的处理流程

1. 先取得runlevel即默认执行等级的相关等级（例如5）
2. 使用/etc/rc.d/rc.sysinit进行系统初始化
3. 由于runlevel是5，因此只进行l5:5:wait:/etc/rc.d/rc 5，其它行略过
4. 设定ctrl+alt+del的组合键功能
5. 设定不断电系统的pf，pr两种机制
6. 启动mingetty的六个终端机（tty1-tty6）
7. 最终以/etc/X11/perfdm -nodaemon启动图形接口

####init处理系统初始化流程（/etc/rc.d/rc.sysinit）

1. 取得网络环境与主机类型
2. 测试与挂载内存装置/proc及USE装置/sys
3. 决定是否启动SELinux
4. 启动系统的随机数生成器
5. 设定终端机字型
6. 设定显示与开机过程中的欢迎画面（text banner）
7. 设定系统时间与时区设定
8. 接口设备的检测与Plug and Play参数测试
9. 用户自定义模块功能
10. 加载核心相关设定
11. 设定主机名与初始化电源管理模块（ACPI）
12. 初始化软件磁盘阵列
13. 初始化LVM的文件系统
14. 以fsck检验磁盘文件系统
15. 进行磁盘配额quota的转换（非必要）
16. 重新以可擦写模式挂载系统磁盘
17. 启动quota功能
18. 启动系统虚拟随机数生成器（pseudo-random）
19. 清除开机过程中的临时文件
20. 将开机相关信息加载到/var/log/dmesg档案中

####启动系统服务与相关启动配置文件（/etc/rc.d/rc N & /etc/sysconfig）

####用户自定义开机启动程序（/etc/rc.d/rc.local）

####依据/etc/inittab，加载终端机或X-Window

####开机过程会用到的主要配置文件

* 关于模块：/etc/modprobe.conf

* /etc/sysconfig/*

  * authconfig：主要在规范使用者的身份认证机制
  * clock：设定Linux主机时区
  * i18n：语系相关
  * keyboard & mouse：设定键盘与鼠标形式
  * network：网络相关
  * network-script：主要用在设定网卡
  
####run level的切换

init runlevel

###核心与核心模块

* 核心：/boot/vmlinuz或/boot/vmlinuz-version
* 核心解压缩所需RAM Disk：/boot/initrd(/boot/initrd-version)
* 核心模块：/lib/modules/version/kernel或/lib/modules/&(username)/kernel
* 核心原始码：/usr/src/linux
* 核心版本：/proc/version
* 系统核心功能：/proc/sys/kernel

####核心模块与相依性

```
depmod [-Ane]

-A：更新modules.dep
-n：不写入modules.dep，直接输出到屏幕上
-e：显示目前已加载的不可执行模块
```

####核心模块的观察

```
lsmod

modinfo [-adln] [module_name|filename]

-a：仅列出作者名称
-d：仅列出该modules的说明（description）
-l：仅列出授权（license）
-n：仅列出该模块的详细路径
```

####核心模块的加载与卸除

```
insmod [/full/path/module_name] [parameters]
```

```
rmmod [-fw] module_name

-f：强制删除
-w：若模块正在使用，则等待该模块使用完毕后再移除
```

```
modprobe [-lcfr] module_name

-c：列出目前系统所有模块
-l：列出磨枪再/lib/modules/uname/kernel当中的所有模块完整文件名
-f：强制加载模块
-r：移除模块
```

####核心模块的额外参数设定：/etc/modprobe.conf

###Boot Loader：Grub

####boot loader的两个stage

* stage 1：执行boot loader主程序

* stager 2：主程序加载配置文件

####grub的配置文件/boot/grub/menu.lst与选单类型

####initrd的重要性与建立新initrd档案

```
mkinitrd [-v] [--with=模块名称] initrd 文件名 核心版本

-v：显示mkinitrd的运作过程
initrd档名：要建立的initrd档名
```

####测试与安装grub

```
grub-install [--root-directory=DIR] INSTALL_DEVICE

--root-directory=DIR：实际目录，默认在/boot/grub/*
```

###开机过程的问题解决

####忘记root密码

重新开机进入单人维护模式，使用passwd重设密码

####init配置文件错误

将第一支程序改为/bin/bash，将根目录挂载为可擦写，然后进行相关救援

####BIOS磁盘对应问题（device.map）

grub-install --recheck /dev/xxx

####因文件系统错误而无法开机

####利用chroot切换到另一个磁盘工作

利用一个Linux系统修复坏的

























