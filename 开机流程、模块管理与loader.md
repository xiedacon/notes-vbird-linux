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



















