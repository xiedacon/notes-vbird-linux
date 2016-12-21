#程序管理与SELinux初探

###程序（process）

####process&program

* program：通常为binary program，以实体档案的形态存在
* process：program被触发后，执行者的权限与属性，程序的程序代码与所需数据等都会被加载到内存中，操作系统给予这个内存内的单元一个标识符（PID）

####Linux的多人多任务环境

* 多人环境
* 多任务环境
* 多重登入环境的七个基本终端窗口
* 特殊的程序管理行为
* bash环境下的工作管理
* 多人多任务的系统资源分配

###工作管理（job control）

####工作管理

* 工作管理只能作用于自己bash的子程序
* 前景：可以控制与下达命令的这个环境称为前景工作（foreground）
* 背景：可以自行运作的工作，无法使用ctrl+c终止，可使用bg/fg呼叫该工作
* 背景中执行的程序不能等待terminal/shell的输入

####job control管理

* 直接将指令丢到背景中执行的&

```
tar -zpcf /xxx.tar.gz /xxx &
```

* 将目前的工作丢到背景中暂停：ctrl+c

* 观察目前背景工作状态：jobs

```
jobs [-lrs]

-l：除了列出job number与指令串之外，同时列出PID的号码
-r：仅列出正在背景run的工作
-s：仅列出正在背景stop的工作
```

* 将背景工作拿到前景来处理：fg

```
fg %jobnumber

%jobnumber：jobnumber为工作号码，%是可有可无的
```

* 让背景下的状态变成运作中：bg

```
bg %jobnumber

%jobnumber：jobnumber为工作号码，%是可有可无的
```

* 管理背景中的工作：kill

```
kill -signal %jobnumber
kil -l

-l：列出目前kill能够使用的signal
signal：讯号
  -1：重新读取一次参数的配置文件
  -2：与ctrl+c相同
  -9：立即强制删除一个工作
  -15：以正常的程序结束方式终止一项工作
```

####脱机管理问题

```
nohup [指令与参数]      //在终端机前景工作
nohup [指令与参数] &    //在终端机背景工作
```

###程序管理

####程序的观察

* ps：将某个时间点的程序运作情况截取下来

```
ps aux     //观察系统所有的程序数据
ps -lA     //观察系统所有的程序数据
ps axjf    //连同部分程序树状态

-A：所有的process均显示出来，与-e具有相同的效果
-a：不予terminal有关的所有process
-u：有效使用者相关的process
x：通常与a一起使用，可列出较完整信息
l：较长、较详细的将该PID的信息列出
j：工作的格式
-f：做一个更为完整的输出
```

* top：动态观察程序的变化

```
top [-d 数字] 
top [-bnp]

-d：后接秒数，即程序画面更新的秒数
-b：以批次的方式执行top，通常会搭配数据流重导向来将批次结果输出成为档案
-n：与-b搭配，指需要进行几次top的输出结果
-p：指定某些PID来进行检查
在top执行过程中可以使用的按键命令：
  ?：显示在top当中可以输入的按键命令
  p：以CPU的使用资源排序显示
  M：以Memory的使用资源排序显示
  N：以PID排序
  T：有该process使用CPU时间积累（TIME+）排序
  k：给予某个PID一个讯号（signal）
  r：给予某个PID重新指定一个nice值
  q：离开
```

* pstree

```
pstree [-A|U] [-up]

-A：各程序树之间的连接以ASCII字符来连接
-U：各程序树之间的连接以UTF-8字符来连接
-p：列出每个process的PID
-u：列出每个processd的所属账号名称
```

####程序的管理

|代号|名称|内容|
|--|--|
|1|SIGHUP|启动被终止的程序，类似重新启动|
|2|SIGINT|相当于ctrl+c|
|9|SIGKILL|强制中断一个程序的进行|
|15|SIGTERM|以正常的结束程序终止该程序|
|17|SIGSTOP|相当于用ctrl+z，暂停|

* kill -signal PID
* killall -signal 指令名称

```
killall [-iIe] [command name]

-i：interactive，交互式，若需要删除时，会出现提示字符给用户
-e：exact，表示后接的command name要一致，但整个完整的指令不能超过15个字符
-I：指令名称忽略大小写
```

####程序的执行顺序

* nice：新执行的指令即给予新的nice值

```
nice [-n 数字] command

-n：后接数值，范围-20~19
```

* renice：已存在程序的nice重新设定

```
renice [number] PID
```

####系统资源观察

* free：观察内存使用情况

```
free [-b|-k|-m|-g|] [-t]

-b：B
-k：K
-m：M
-g：G
-t：在输出的最终结果，显示物理内存与swap总量
```

* uname：检查系统与核心相关信息

```
uname [-asrmpi]

-a：所有系统相关的信息
-s：系统核心名称
-r：核心版本
-m：本系统的硬件名称
-p：CPU类型
-i：硬件平台
```

* uptime：观察系统启动时间与工作负载

* netstat：观察网络或插槽文件

```
netstat -[atunlp]

-a：将系统上所有联机、监听、socket数据都列出来
-t：列出tcp网络封包的数据
-u：列出udp网络封包的数据
-n：不以程序的服务名称，以端口号显示
-l：列出目前正在网络监听的服务
-p：列出该网络服务的程序PID
```

* dmesg：分析核心产生的信息

* vmstat：侦测系统资源变化

```
vmstat [-a] [延迟 [总计侦测次数]]    //CPU/内存等信息
vmstat [-fs]                       //内存相关
vmstat [-S 单位]                   //设定显示数据的单位
vmstat [-d]                       //与磁盘有关
vmstat [-p 分割槽]                 //与磁盘有关

-a：使用inactive/active取代buffer/cache的内存输出信息
-f：将开机到目前位置，系统复制（fork）的程序数
-s：将一些事件导致的内存变化情况列表说明
-S：后接单位，显示的数据单位
-d：列出磁盘的读写总量统计表
-p：后面列出分割槽，可显示该分割槽的读写总量统计表
```

###特殊档案与程序

####具有SUID/SGID权限的指令执行状态

####/proc/*代表意义

|档名|档案内容|
|--|--|
|/proc/cmdline|加载kernel时所下达的相关参数|
|/proc/cpuinfo|CPU相关信息|
|/proc/devices|记录了系统各个主要装置的代号|
|/proc/filesystems|目前系统已经加载的文件系统|
|/proc/interrupts|目前系统上的IRG分配状态|
|/proc/ioports|目前系统上的各个装置所配置的I/O地址|
|/proc/kcore|内存大小|
|/proc/loadavg|记录平均数|
|/proc/meminfo|使用free列出内存信息|
|/proc/modules|目前系统已加载的模块列表|
|/proc/mounts|系统已挂载的数据|
|/proc/swaps||
|/proc/partitions|目前所有的partition|
|/proc/pci|在PCI总线上面，每个装置的详细情况|
|/proc/uptime|使用uptime时，会出现的信息|
|/proc/version|核心版本|
|/proc/bus/*|一些总线装置，还有USB装置|

####查询已开启档案或已执行程序开启的档案

* fuser：借由档案找出正在使用该档案的程序

```
fuser [-umv] [-k [i] [-signal]] file/dir

-u：除了PID外，同时列出程序的拥有者
-m：后接档名会主动上提到该文件系统的最顶层
-v：可以列出每个档案与程序还有指令的完整相关性
-k：找出使用该档案/目录的PID，并试图给予该signal
-i：与-k配合，交互
-signal：讯号
```

* lsof：列出被程序所开启的档案文件名

```
lsof [-aUu] [+d]

-a：多项数据需要同时成立才显示结果
-U：仅列出Unix Like系统的socket文件类型
-u：后接username，列出该用户相关程序所开启的档案
+d：后接目录，找出某个目录底下已经被开启的档案
```

* pidof；找某支正在执行程序的PID

```
pidof [-sx] program_name

-s：仅列出一个PID而不列出所有的PID
-x：同时列出该program name可能的PPID那个程序的PID
```

###SELinux初探

####SELinux的运作模式

* 主体（Subject）

* 目标（Object）

* 政策（Policy）

* 安全性本文

![](/assets/SELinux运作的各组件的相关性.png)

####SELinux的启动、关闭与观察

* enforcing：强制模式，代表SELinux运作中，且已经正确的开始限制domain/type
* permissive：宽容模式，代表SELinux运作中，不过仅会有警告信息并不会实际限制domian/type的存取
* disabled：关闭

```
getenforce     //显示目前的SELinux模式

sestatus [-vb]

-v：检查位于/etc/sestatus.conf内的档案与程序的安全性文本内容
-b：将目前政策的规则布尔值列出

setenforce [0|1]

0：转成permissive模式
1：转成enforcing模式
```

####SELinux网络服务运作

* 网络服务的启动与观察

* 错误的SELinux安全性本文

* 重设SELinux安全性本文

```
chron [-R] [-t type] [-u user] [-r role] 档案
chcon [-R] --reference=范例文件 档案

-R：连同该目录下的次目录也同时修改
-t：后接安全性本文的类型字段
-u：后接身份识别
-r：后接角色

restorecon [-Rv] 档案或目录

-R：连同次目录一起修改
-v：将过程显示到屏幕上
```

####SELinux所需的服务

####SElinux的政策与规则管理

* 政策查询

```
seinfo [-Atrub]

-A：列出SELinux的状态、规则布尔值、身份识别、角色、类别等所有信息
-t：列出SELinux的所有类别（type）种类
-r：列出SELinux的所有角色（role）种类
-u：列出SELinux的所有身份识别（user）种类
-b：列出所有规则的种类（布尔值）

sesearch [-a] [-s 主体类别] [-t 目标类别] [-b 布尔值]

-a：列出该类别或布尔值的所有相关信息
-t：后接类别
-b：后接布尔值规则
```

* 布尔值的查询与修改

```
getsebool [-a] [布尔值条款]

-a：列出目前系统上面的所有布尔值条款设定
```

* 默认目录的安全性文本查询与修改

```
semanage {login|user|port|interface|fcontext|translation} -l
semanage fcontext -{a|d|m} [-frst] file_spec

fcontext：主要用在安全性本文方面的用途，-l为查询的意思
-a：增加
-m：修改
-d：删除
```










