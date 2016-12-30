# 命令行索引

- [基础命令](#基础命令)
  - [date](#date)
  - [cal](#cal)
  - [bc](#bc)
  - [man](#man)
  - [info](#info)
  - [sync](#sync)
  - [shutdown](#shutdown)
  - [reboot](#reboot)
  - [poweroff](#poweroff)
  - [dos2unix,unix2dos](#dos2unix,unix2dos)
  - [iconv](#iconv)
  - [type](#type)
  - [echo](#echo)
  - [unset](#unset)
  - [env](#env)
  - [export](#export)
  - [read](#read)
  - [declare](#declare)
  - [ulimit](#ulimit)
  - [alias,unalias](#alias,unalias)
  - [history](#history)
  - [source](#source)
  - [sh](#sh)
  - [set](#set)


- [文件与目录管理相关](#文件与目录管理相关)
  - [ls](#ls)
  - [cd](#cd)
  - [pwd](#pwd)
  - [mkdir](#mkdir)
  - [rmdir](#rmdir)
  - [rm](#rm)
  - [mv](#mv)
  - [cp](#cp)
  - [cat](#cat)
  - [tac](#tac)
  - [nl](#nl)
  - [touch](#touch)
  - [more](#more)
  - [less](#less)
  - [head](#head)
  - [tail](#tail)
  - [od](#od)
  - [ln](#ln)


- [程序管理与SELinux相关](#程序管理与SELinux相关)
  - [ps](#ps)
  - [top](#top)
  - [pstree](#pstree)
  - [jobs](#jobs)
  - [kill](#kill)
  - [killall](#killall)
  - [bg](#bg)
  - [fg](#fg)
  - [nohup](#nohup)
  - [at](#at)
  - [atq](#atq)
  - [atrm](#atrm)
  - [crontab](#crontab)
  - [anacron](#anacron)
  - [nice](#nice)
  - [renice](#renice)
  - [free](#free)
  - [uname](#uname)
  - [uptime](#uptime)
  - [dmesg](#dmesg)
  - [vmstat](#vmstat)
  - [fuser](#fuser)
  - [lsof](#lsof)
  - [pidof](#pidof)
  - [getenforce](#getenforce)
  - [sestatus](#sestatus)
  - [setenforce](#setenforce)
  - [chron](#chron)
  - [restorecon](#restorecon)
  - [seinfo](#seinfo)
  - [sesearch](#sesearch)
  - [getsebool](#getsebool)
  - [semanage](#semanage)


- [压缩相关](#压缩相关)
  - [compress](#compress)
  - [gzip,zcat](#gzip,zcat)
  - [bzip2,bzcat](#bzip2,bzcat)
  - [tar](#tar)
  - [dump](#dump)
  - [restore](#restore)
  - [dd](#dd)
  - [cpio](#cpio)


- [搜索与字符处理相关](#搜索与字符处理相关)
  - [which](#which)
  - [whereis](#whereis)
  - [locate](#locate)
  - [find](#find)
  - [cut](#cut)
  - [grep](#grep)
  - [sort](#sort)
  - [uniq](#uniq)
  - [wc](#wc)
  - [tee](#tee)
  - [tr](#tr)
  - [col](#col)
  - [join](#join)
  - [paste](#paste)
  - [expand](#expand)
  - [split](#split)
  - [xargs](#xargs)
  - [sed](#sed)
  - [printf](#printf)
  - [awk](#awk)
  - [diff](#diff)
  - [cmp](#cmp)
  - [patch](#patch)
  - [管线命令](#管线命令)


- [权限与账号管理相关](#权限与账号管理相关)
  - [umask](#umask)
  - [chattr](#chattr)
  - [lsattr](#lsattr)
  - [chmod](#chmod)
  - [groups](#groups)
  - [newgrp](#newgrp)
  - [useradd](#useradd)
  - [passwd](#passwd)
  - [chage](#chage)
  - [usermod](#usermod)
  - [userdel](#userdel)
  - [finger](#finger)
  - [chfn](#chfn)
  - [chsh](#chsh)
  - [id](#id)
  - [groupadd](#groupadd)
  - [groupmod](#groupmod)
  - [groupdel](#groupdel)
  - [gpasswd](#gpasswd)
  - [setfacl](#setfacl)
  - [getfacl](#getfacl)
  - [su](#su)
  - [sudo](#sudo)

- [磁盘与文件系统相关](#磁盘与文件系统相关)
  - [dumpe2fs](#dumpe2fs)
  - [df](#df)
  - [du](#du)
  - [fdisk](#fdisk)
  - [mkfs](#mkfs)
  - [fsck](#fsck)
  - [badblocks](#badblocks)
  - [mount](#mount)
  - [umount](#umount)
  - [mknod](#mknod)
  - [hdparm](#hdparm)
  - [quotacheck](#quotacheck)
  - [quotaon](#quotaon)
  - [quotaoff](#quotaoff)
  - [edquota](#edquota)
  - [quota](#quota)
  - [repquota](#repquota)
  - [warnquota](#warnquota)
  - [setquota](#setquota)
  - [mdadm](#mdadm)


- [网络相关](#网络相关)
  - [ifconfig](#ifconfig)
  - [ifup](#ifup)
  - [ifdown](#ifdown)
  - [route](#route)
  - [ip](#ip)
  - [iwlist](#iwlist)
  - [iwconfig](#iwconfig)
  - [dhclient](#dhclient)
  - [ping](#ping)
  - [traceroute](#traceroute)
  - [netstat](#netstat)
  - [host](#host)
  - [nslookup](#nslookup)
  - [telnet](#telnet)
  - [ftp](#ftp)
  - [lftp](#lftp)
  - [links](#links)
  - [wget](#wget)
  - [tcpdump](#tcpdump)
  - [nc](#nc)

- [其他](#其他)
  - [chkconfig](#chkconfig)
  - [logrotate](#logrotate)
  - [make](#make)
  - [ldconfig](#ldconfig)
  - [ldd](#ldd)
  - [md5sum/sha1sum](#md5sum/sha1sum)
  - [depmod](#depmod)
  - [lsmod](#lsmod)
  - [insmod](#insmod)
  - [rmmod](#rmmod)
  - [modprobe](#modprobe)
  - [mkinitrd](#mkinitrd)


---

## 基础命令

#####date

> 显示日期

```
date
date +%Y%m%d
```

#####cal

> 显示日历

```
cal [month] [year]
```

#####bc

> 计算器

#####man

> man page

```
man [number] command

number：表示command类型的代号
  1：用户在shell环境中可以操作的指令或可执行文件
  2：系统核心可呼叫的函数与工具等
  3：一些常用的函数与函数库，大部分为C的函数库
  4：装置档案的说明，通常在/dev下的档案
  5：配置文件或者是某些档案的样式
  6：游戏
  7：惯例与协议等，例如Linux文件系统、网络协议、ASCII code 等等的说明
  8：系统管理员可用的管理指令
  9：跟kernel有关的文件

man page的内容划分：
  NAME：简短的指令、数据名称说明
  SYNOPSIS：简短的指令下达语法简介
  DESCRIPTION：较为完整的说明
  OPTIONS：针对SYNOPSIS部分中，有列举的所有可用的选项说明
  COMMANDS：当这个程序在执行的时候，可以在此程序中下达的指令
  FILES：这个程序或数据所使用或参考或链接到的某些档案
  SEE ALSO：可以参考的，跟这个指令或数据相关的其他说明
  EXAMPLE：一些可以参考的范例
  BUGS

man page的常用按键：
  space：向下翻页
  page down：向下翻页
  page up：向上翻页
  home：到第一页
  end：到最后一页
  /string：向下搜寻string
  ?string：向上搜寻string
  n：继续搜寻
  N：反向搜寻
  q：结束
```

#####info

> 与man相似，略

#####sync

> 将数据同步写入硬盘

#####shutdown

> 惯用的关机指令

```
shutdown [-t 秒] [-arkhncfF] 时间 [警告讯息]

-t：后接秒数，即过几秒后关机
-k：不是真的关机，只是将警告讯息发送出去
-r：在将系统的服务停掉后就重新启动（常用）
-h：将系统的服务停掉后，立即关机（常用）
-n：不经过init程序，直接以shutdown的功能来关机
-f：系统重新启动后，强制略过fsck的磁盘检查
-F：系统重新启动后，强制进行fsck的磁盘检查
-c：取消已经在进行的shutdown指令内容
时间：一定要加入的参数，指定系统关机的时间
```

#####reboot

> 重启

#####poweroff

> 关机

#####dos2unix,unix2dos

> DOS与Linux的断行字符

```
dos2unix [-kn] file [newfile]
unix2dos [-kn] file [newfile]

-k：保留该档案原本的mtime时间格式
-n：保留原本的旧档，将转换后的内容输出到新档案
```

#####iconv

> 语系编码转换

```
iconv --list
iconv -f 原本编码 -t 新编码 filename [o newfile]

--list：列出iconv支持的语系数据
-f：from，后接原本的编码格式
-t：to，后接新编码格式
-o file：后接新档名，保留原档
```

#####type

> Bash shell的内建命令

```
type [-tpa] name

不加任何选项与参数是，type会显示出name是外部指令还是bash内建指令
-t：type会将name以下列字眼显示出他的意义
  file：表示为外部指令
  alias：表示该指令为命令别名所设定的名称
  builtin：表示该指令为bash内建的指令功能
-p：如果后面接的name为外部指令时，才会显示完整文件名
-a：会将由PATH变量定义的路径中，将所有含name的指令都列出来，包含alias
```

#####echo

> 变量的取用

```
echo $variable
```

#####unset

> 取消变量

```
unset name
```

#####env

> 观察环境变量

#####export

> 将自定义变量转成环境变量

#####read

> 变量键盘读取

```
read [-pt] variable

-p：后接提示字符
-t：后接等待秒数
```

#####declare

> 变量宣告

```
declare [-aixr] variable

-a：将后接变量定义为数组
-i：将后接变量定义为整型数字
-x：将后接变量导出为环境变量
-r：将后接变量定义为readonly类型，不能修改，也不能unset
```

#####ulimit

> 限制用户的系统资源使用量

```
ulimit [-SHacdfltu] [配额]

-H：hard limit，严格设定，必定不能超过设定值
-S：soft limit，警告设定，可以超过，超过会有警告信息
-a：后将不接任何选项与参数，可列出所有的限制额度
-c：限制每个核心档案的最大容量
-f：此shell可建立的最大档案容量，单位为kbytes
-d：程序可使用的最大内存容量
-l：可用于锁定（lock）的内存量
-t：可使用的最大CPU时间，单位为秒
-u：单一用户可以使用的最大程序数量
```

#####alias,unalias

> 命令别名设定与取消

```
alias xx='xxx'
unalias xx
```

#####history

> 历史命令

```
history [n]
history [-c]
history [-raw] histfiles

n：列出最近n笔命令
-c：将shell中的history内容全部清除
-a：将新增的history指令新增入histfiles中，若没有histfiles，则写入~/.bash_history
-r：将histfiles的内容读到目前shell的history中
-w：将目前的history写入histfiles中
```

#####source

> 读入环境配置文件

```
source 配置文件档名
```

#####sh

> 执行shell脚本

```
sh [-nvx] script.sh

-n：不执行script，仅检查语法
-v：执行script之前，先把script的内容输出到屏幕上
-x：将使用到的script内容显示到屏幕上
```

#####set

> 终端机环境设定

```
set [-uvCHhmBx]

-u：预设不启用。启用后，当使用未设定变量时，会显示错误信息
-v：预设不启用。启用后，在信息被输出前，会先显示信息的原始内容
-x：预设不启用。启用后，在指令被执行前，会显示指令内容
-h：预设启用。与历史命令有关
-H：预设启用。与历史命令有关
-m：预设启用。与工作管理有关
-B：预设启用。与[]的作用有关
-C：预设不启用。若使用>等，则若档案存在时，该档案不会被覆盖
```

## 文件与目录管理相关

#####ls

> 查看档案与目录信息

```
ls [-aAdfFhilnrRSt] 目录名称
ls [--color={never,auto,always}] 目录名称
ls [--full-time] 目录名称

-a：全部档案，连同隐藏档一起列出来
-A：全部档案，连同隐藏档一起列出来，但不包括 . 与 .. 这两个目录
-d：仅列出目录，而不列出目录内的档案数据
-f：直接列出结果，不进行排序
-F：根据档案、目录等信息，给予附加数据结构
-h：将档案容量以GB/KB等形式列出来
-i：列出inode号码
-l：长数据串列出，包含档案的属性与权限等
-n：列出UID与GID而非使用者与群组名称
-r：将排序结果反向输出
-R：连同子目录内容一起列出来
-S：以容量大小排序
-t：以时间排序
--color=never：不依据档案特性给予颜色显示
--color=aways：显示颜色
--color=auto：让系统自动判断是否显示颜色
--full-time：以完整时间模式输出
--time=atime/ctime：输出access时间或改变时间

常用：adl
```

#####cd

> 改变目录

```
.  代表这一层目录
.. 代表上一层目录
-  代表前一个工作目录
~  代表当前用户的home目录
```

#####pwd

> Print Working Directory 显示当前目录

```
pwd [-P]

-P：显示出确定的路径，而非使用link路径
```

#####mkdir

> 新建目录

```
mkdir [-mp] 目录名称

-m：配置文件的权限
-p：建立多层目录
```

#####rmdir

> 删除空目录

```
rmdir [-p] 目录名称

-p：连同上层的空目录一起删除
```

#####rm

> 移除档案或目录

```
rm [-fir] 档案或目录

-f：force 强制执行，忽略警告信息
-i：互动模式，在删除前询问是否删除
-r：递归执行
```

######mv

> 移动档案与目录，或改名

```
mv [-fiu] source destination  
mv [option] source1 source2 ... directory

-f：强制执行
-i：互动模式
-u：若目标档案已存在，且source更新，才会更新
```

#####cp

> 复制档案或目录

```
cp [-adfilprsu] source destination  
cp [options] source1 source2 ... directory

-a：相当于-pdr
-d：若来源文件为link文件的属性，则复制link文件的属性而非档案本身
-f：强制执行，若目标档案已存在且无法开启，则移除后再尝试一次
-i：互动模式
-l：进行硬式链接（hard link）的链接档建立，而非赋值档案本身
-p：连同档案属性一起复制过去
-r：递归执行
-s：复制成为符号链接文件，即快捷方式
-u：更新

常用：aipr
```

#####cat

>concatenate 由第一行开始显示档案内容

```
cat [-AbEnTv]

-A：相当于-vET
-b：列出行号，空白行不标行号
-E：显示断行字符$
-n：列出行号，连同空白行
-T：将tab键以^I显示
-v：列出一些看不出来的特殊字符
```

#####tac

> 由最后一行开始显示

```
与cat相同
```

#####nl

> 显示时，顺便输出行号

```
nl [-bnw] 档案

-b：指定行号，指定的方式有两种
  -b a：不论是否为空行都列出行号（类似cat -n）
  -b t：如果有空行，空行不列出行号（默认值）
-n：列出行号的表示方法，主要有三种
  -n ln：行号在屏幕最左方显示
  -n rn：行号在自己字段的最右方显示，且不加0
  -n rz：行号在自己字段的最右方显示，加0
-w：行号字段占用的位数
```

#####touch

>建立一个空档/修订时间

```
touch [-acdmt] 档案

-a：仅修订access time
-c：仅修该档案的时间，若该档案不存在则不建立新档案
-d：后面可以接欲修订的日期而不用当前日期，也可以使用--date="日期或时间"
-m：仅修该mtime
-t：后面可以接欲修订的时间而不是用当前时间，格式为[YYMMDDhhmm]

modification time(mtine):
  当该档案的数据内容改变时，就会更新这个时间
status time(ctime):
  当该档案的状态（权限与属性）改变时，就会更新这个时间
access time(atime)：
  当该档案的内容被取用时，就会更新这个读取时间
```

#####more

> 一页一页翻动

```
space：下一页
enter：下一行
/字符串：向下搜索字符串
:f：立即显示出文件名以及目前显示的行数
q：离开
b/[ctrl] b：往回翻页，对管线无用
```

#####less

> 一页一页翻动

```
space：下一页
pagedown：下一页
pageup：上一页
/字符串：向下搜索字符串
?字符串：向上收缩字符串
n：重复前一搜寻
N：反向重复前一搜寻
q：离开
```

#####head

> 只看头几行

```
head [-n number] 档案

-n：后接数字，表示显示几行，默认显示前20行
```

#####tail

> 只看最后几行

```
tail [-n number] 档案

-n：后接数字，表示显示几行，默认显示10行
-f：表示持续侦测后面所接的档名，直到ctrl c才会结束tail的侦测
```

#####od

> 读取非纯文本文档

```
od [-t TYPE] 档案

-t：后接各种类型的输出
  a：使用默认的字符来输出
  c：使用ASCII字符来输出
  d[size]：使用十进制（decimal）来输出数据，每个整数占用size bytes
  f[size]：使用浮点数（floating）来输出数据，每个数占用size bytes
  o[size]：使用八进制（octal）来输出数据，每个整数占用size bytes
  x[size]：使用十六进制（hexadecimal）来输出数据，每个整数占用size bytes
```

#####ln

> 建立文件链接

```
ln [-sf] 来源文件 目录文件

-s：默认hard link，加上后symbolic link
-f：如果目标文件存在时，就主动将目标文件直接移除后再建立
```

## 程序管理与SELinux相关

#####ps

> 将某个时间点的程序运作情况截取下来

```
ps aux：观察系统所有程序的数据
ps -lA：观察所有系统的数据
ps axjf：连同部分程序树状态

-A：所有的process均显示出来，与-e具有同样的效果
-a：不与terminal有关的所有process
-u：有效使用者相关的process
x：通常与a一起使用，可列出较完整的信息
l：以较长、较详细的方式将该PID的信息列出
j：工作的格式
-f：做一个更为完整的输出
```

#####top

> 动态观察程序的变化

```
top [-d 数字]
top [-bnp]

-d：后接秒数，就是整个程序画面更新的秒数，预设5秒
-b：以批次的方式执行top，通常会搭配数据流重导向来将批次的结果输出成档案
-n：与-b搭配，意义是，需要进行几次top的输出结果
-p：指定某些PID来进行观察监测

在top执行过程中可以执行的按键命令：
  ?：显示top中可以输入的按键指令
  P：以CPU的使用资源排序显示
  M：以Memory的使用资源排序显示
  N：以PID排序
  T：以process使用CPU时间积累（TIME+）排序
  k：给某个PID一个讯号（signal）
  r：给某个PID重新制定一个nice值
  q：离开
```

#####pstree

> 将某个时间点的程序运作情况截取下来，以程序树的形式

```
pstree [-A|U] [-up]

-A：各程序树之间的连接以ASCII字符来连接
-U：各程序树之间的连接以UTF-8字符来连接
-p：列出每个process的PID
-u：列出每个processd的所属账号名称
```

#####jobs

> 观察当前背景工作状态

```
jobs [-lrs]

-l：除了列出jobnumber与指令串之外，同时列出PID的号码
-r：仅列出正在run的工作
-s：仅列出正在stop的工作
```

#####kill

> 管理背景中的工作

```
kill -signal PID

signal（讯号）
  1 SIGHUP 启动被终止的程序，类似重新启动
  2 SIGINT 相当于ctrl+c，中断程序的进行
  9 SIGKILL 强制中断程序的进行
  15 SIGTERM 以正常结束程序来终止该程序
  17 SIGTOP 相当于ctrl+z，暂停一个程序的进行
  更多信息自行man 7 signal
```

#####killall

```
killall [-iIe] [command name]
killall -signal 指令名称

-i：交互模式
-e：exact的意思，表示后面接的command name要一致，但整个完整的指令不能超过15个字符（并不能看懂是什么意思）
-I：指令名称（可能含参数）忽略大小写
```

#####bg

> 让背景下的状态变成运作中

```
bg %jobnumber

%jobnumber：jobnumber为工作号码，%是可有可无的
```

#####fg

> 将背景工作拿到前景来处理

```
fg %jobnumber

%jobnumber：jobnumber为工作号码，%是可有可无的
```

#####nohup

> 程序脱机执行

```
nohup [指令与参数]      //在终端机前景工作
nohup [指令与参数] &    //在终端机背景工作
```

#####at

> at是个可以处理仅执行一次就结束排程的指令，执行时，必须要有atd这个服务的支持

```
at [-mldv] TIME
at -c 工作号码

-m：完成后，使用email通知使用者
-l：相当于atq，列出系统上的所有该用户的at排程
-d：相当于atm，可以取消一个在at排程中的工作
-v：时间格式
-c：列出后接的该项工作的实际指令内容
TIME：时间格式
```

#####atq

> 查询系统上有多少at工作排程

#####atrm

> 移除某个工作排程

```
atrm [jobnumber]
```

#####crontab

> crontab这个指令所设定的工作会循环执行下去

```
crontab [-u username] [-l|-e|-r]

-u：只有root才能进行这个任务
-e：编辑crontab的工作内容
-l：查看crontab的工作内容
-r：移除所有crontab的工作内容
```

#####anacron

> 可唤醒停机期间的工作任务

```
anacron [-sfn] [job] ...
anacron -u [job] ...

-s：开始一连续的执行各项工作 (job)，会依据时间记录文件的数据判断是否进行
-f：强制
-n：立即执行未进行的任务
-u：仅更新时间记录文件的时间戳，不进行任何操作
job：由/etc/anacrontab定义的各项工作名称
```

#####nice

> 给予新执行的指令新的nice值

```
nice [-n 数字] command

-n：后接数值，范围-20~19
```

#####renice

> 已存在程序的nice重新设定

```
renice [number] PID
```

#####free

> 观察内存使用情况

```
free [-b|-k|-m|-g|] [-t]

-b：B
-k：K
-m：M
-g：G
-t：在输出的最终结果，显示物理内存与swap总量
```

#####uname

> 检查系统与核心相关信息

```
uname [-asrmpi]

-a：所有系统相关的信息
-s：系统核心名称
-r：核心版本
-m：本系统的硬件名称
-p：CPU类型
-i：硬件平台
```

#####uptime

> 观察系统启动时间与工作负载

#####dmesg

> 分析核心产生的信息

#####vmstat

> 侦测系统资源变化

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

######fuser

> 借由档案找出正在使用该档案的程序

```
fuser [-umv] [-k [i] [-signal]] file/dir

-u：除了PID外，同时列出程序的拥有者
-m：后接档名会主动上提到该文件系统的最顶层
-v：可以列出每个档案与程序还有指令的完整相关性
-k：找出使用该档案/目录的PID，并试图给予该signal
-i：与-k配合，交互
-signal：讯号
```

#####lsof

> 列出被程序所开启的档案文件名

```
lsof [-aUu] [+d]

-a：多项数据需要同时成立才显示结果
-U：仅列出Unix Like系统的socket文件类型
-u：后接username，列出该用户相关程序所开启的档案
+d：后接目录，找出某个目录底下已经被开启的档案
```

#####pidof

> 找某支正在执行程序的PID

```
pidof [-sx] program_name

-s：仅列出一个PID而不列出所有的PID
-x：同时列出该program name可能的PPID那个程序的PID
```

#####getenforce

> 显示目前的SELinux模式

#####sestatus

> 查看SELinux的状态

```
sestatus [-vb]

-v：检查位于/etc/sestatus.conf内的档案与程序的安全性文本内容
-b：将目前政策的规则布尔值列出
```

#####setenforce

> 改变SELinux的模式

```
setenforce [0|1]

0：转成permissive模式
1：转成enforcing模式
```

#####chron

> 重设SELinux安全性本文

```
chron [-R] [-t type] [-u user] [-r role] 档案
chcon [-R] --reference=范例文件 档案

-R：连同该目录下的次目录也同时修改
-t：后接安全性本文的类型字段
-u：后接身份识别
-r：后接角色
```

######restorecon

> 重设SELinux安全性本文

```
restorecon [-Rv] 档案或目录

-R：连同次目录一起修改
-v：将过程显示到屏幕上
```

#####seinfo

> 政策查询

```
seinfo [-Atrub]

-A：列出SELinux的状态、规则布尔值、身份识别、角色、类别等所有信息
-t：列出SELinux的所有类别（type）种类
-r：列出SELinux的所有角色（role）种类
-u：列出SELinux的所有身份识别（user）种类
-b：列出所有规则的种类（布尔值）
```

#####sesearch

> 政策查询

```
sesearch [-a] [-s 主体类别] [-t 目标类别] [-b 布尔值]

-a：列出该类别或布尔值的所有相关信息
-t：后接类别
-b：后接布尔值规则
```

#####getsebool

> 查看布尔值条款设定

```
getsebool [-a] [布尔值条款]

-a：列出目前系统上面的所有布尔值条款设定
```

#####semanage

> 默认目录的安全性文本查询与修改

```
semanage {login|user|port|interface|fcontext|translation} -l
semanage fcontext -{a|d|m} [-frst] file_spec

fcontext：主要用在安全性本文方面的用途，-l为查询的意思
-a：增加
-m：修改
-d：删除
```

## 压缩相关

#####compress

> 用compress程序解压或压缩档案

```
compress [-rcv] 档案或目录   //压缩
uncompress 档案.Z         //解压

-r：可以连同目录下的档案一起压缩
-c：将压缩数据输出成为standard output
-v：可以显示压缩后的档案信息以及压缩过程中的一些档名变化
```

#####gzip,zcat

> 解压或压缩gz档案

```
gzip [-cdtv#] 档名
zcat 档名.gz

-c：将压缩的数据输出到屏幕上，可透过数据流重导向来处理
-d：解压缩的参数
-t：可以用来检验一个压缩文件的一致性，查看档案有无错误
-v：可以显示出原档案/压缩文件的压缩比等信息
-#：压缩等级，-1最快，但压缩比最差，-9最慢，但是压缩比最好，默认-6
```

#####bzip2,bzcat

> 解压或压缩bz档案

```
bzip2 [-cdkzv#] 档名
bzcat 档名.bz2

-c：将压缩的过程产生的数据输出到屏幕上
-d：解压缩的参数
-k：保留源文件，而不会删除原始的档案
-z：压缩的参数
-v：可以显示出原档案/压缩文件的压缩比等信息
-#：与gzip相同
```

#####tar

> 打包指令

```
tar [-j|-z] [cv] [-f 建立的档名] filename ... // 打包/压缩
tar [-j|-z] [tv] [-f 建立的档名]          // 查看档名
tar [-j|-z] [xv] [-f 建立的档名] [-C 目录]   // 解压缩

-c：建立打包档案，可搭配-v来查看过程中被打包的档名
-t：查看打包档案的内容含有哪些档名
-x：解压的功能，可以搭配-C在特定目录解开
-j：透过bzip2支持进行压缩/解压，此时文档名最好为*.tar.bz2
-z：透过gzip的支持进行压缩/解压，此时文档名最好为*.tar.gz
-v：在压缩/解压过程中，将正在处理的文件名显示出来
-f filename：-f后面要立刻接要处理的档名，建议-f单独写一个
-C 目录：解压目录
-p：保留备份数据的原本权限与属性，常用于备份重要的配置文件
-P：保留绝对路径，即允许备份数据中含有根目录的意思
```

#####dump

> 备份工具

```
dump [-Suvj] [-level] [-f 备份档] 待备份资料
dump -W

-s：仅列出后面的待备份数据需要多少磁盘空间才能够备份完毕
-u：将这次dump的时间记录到/etc/dumpdates档案中
-v：将dump的档案过程显示出来
-j：加入bzip2支持，将数据进行压缩，默认bzip2压缩等级为2
-level：压缩等级，从-0到-9共十个等级
-f：后接产生的档案
-W：列出在/etc/fstab里面角有dump设定的partition是否有备份过
```

#####restore

> 备份工具

```
restore -t [-f dumpfile] [-h]        //用来观察dump档
restore -C [-f dumpfile] [-D 挂载点]   //比较dump与实际档案
restore -i [-f dumpfile]           //进入互动模式
restore -r [-f dumpfile]           //还原整个文件系统

-t：此模式用在查看dump起来的备份文件
-C：此模式可以将dump内的数据拿出来跟实际的文件系统做比较，最终会列出在dump档案内有记录，且与文件系统不一样的档案
-i：互动模式
-r：此模式用在将整个filesystem还原
-h：查看完整备份数据中的inode与文件系统label等信息
-f：后面接需要处理的dump档案
-D：与-C搭配，可以查出后面接的挂载点与dump内有不同的档案
```

#####dd

> 备份工具

```
dd if="input_file" of="output_file" bs="block_size" count="number"

if：input file，也可以是装置
of：output file，也可以是装置
bs：规划一个block大小，默认512bytes
count：bs个数
```

#####cpio

> 备份工具

```
cpio -ovcB > [file|device]    //备份
cpio -ivcdu < [file|device]   //还原
cpio -ivct < [file|device]    //查看

-o：将数据copy输出到档案或装置上
-B：让预设的blocks可以增加至5120bytes，默认512bytes，可以让大档案的存储速度加快
-i：将数据自档案或装置copy到系统当中
-d：自动建立目录
-u：自动的将较新的档案覆盖较旧的档案
-t：需要配合-i选项，可用在查看以cpio建立的档案或装置的内容
-v：让储存的过程中文件名可以在屏幕上显示
-c：一种较新的portable format方式储存
```

## 搜索与字符处理相关

#####which

> 脚本文件名的搜寻

```
which [-a] command

-a：将所有有PATH目录中可以找到的指令均列出，而不止第一个被找到的指令名称
```

#####whereis

> 寻找特定档案（通过内部数据库）

```
whereis [-bmsu] 档案或目录名

-b：只找二进制格式的档案
-m：只找在说明文件manual路径下的档案
-s：只找source来源档案
-u：搜寻不在上述三个项目当中的其他特殊档案
```

#####locate

> 按档案名寻找档案（通过内部数据库）

```
locate [-ir] keyword

-i：忽略大小写的差异
-r：后面可接正则表达式
```

#####find

> 在磁盘中寻找档案

```
find [PATH] [option] [action]

与时间有关的选项：共有-atime、-ctime与-mtime，以-mtime说明
  -mtime n：n为数字，意义为在n天之前的一天内被变更过内容的档案
  -mtime +n：列出n天之前（不含n天本身）被变更过内容的档案
  -mtime -n：列出n天之内（含n天本身）被变更过内容的档案
  -newer file：列出比file还要新的档案
与使用者或组名有关的参数
  -uid n：n为数字，代表用户的UID
  -gid n：n为数字，代表组名的GID
  -user name：name为用户名
  -group name：name为组名
  -nouser：寻找拥有者在/etc/passwd中不存在的档案
  -nogroup：寻找群组在/etc/group中不存在的档案
与档案权限及名称有关的参数
  -name filename：搜寻文件名为filename的档案
  -size [+-]SIZE：搜寻比SIZE还要大（+）或小（-）的档案。SIZE的规格有：C代表byte，代表kb
  -type TYPE：搜寻档案的类型为TYPE
  -perm mode：搜寻档案权限刚好等于mode的档案
  -perm -mode：搜寻档案权限包括mode权限的档案
  -perm +mode：搜寻档案权限包含任一mode的权限的档案
额外动作
  -exec：后接额外指令处理搜寻到的结果
  -print：将结果打印到屏幕上（默认值）
```

#####cut

> 截取命令

```
cut -d '分隔字符' -f fields     //用于由特定分隔字符
cut -c 字符区间                 //用于排列整齐的信息

-d：后接分隔字符，与-f一起使用
-f：依据-d的分隔字符将一段信息分割成数段，用-f取出第几段
-c：以字符的单位取出固定字符区间
```

#####grep

> 截取命令

```
grep [-acinv] [--color=auto] '搜索字符串' filename
grep [-A] [-B] [--color=auto] '搜寻字符串' filename

-a：将binary档案以text档案方式搜寻数据
-c：计算找到'搜寻字符串'的次数
-i：忽略大小写
-n：输出行号
-v：反向选择
-A：after，后接数字，除了列出该列外，后续的n列也列出来
-B：befer，后接数字，除了列出该列外，前面的n列也列出来
--color=auto：将找到的关键字加上颜色显示
```

#####sort

> 排序命令

```
sort [-fbMnrtuk] [file or stdin]

-f：忽略大小写
-b：忽略最前面的空格部分
-M：以月份来排序
-n：使用纯数字进行排序
-r：反向排序
-u：相同数据中，仅出现一行代表
-t：分隔符，默认以tab键来分隔
-k：以某个区间来进行排序
```

#####uniq

> 排序命令

```
uniq [-ic]

-i：忽略大小写字符的不同
-c：进行计数
```

#####wc

> 排序命令

```
wc [-lwm]

-l：仅列出行
-w：仅列出字数
-m：字符数
```

#####tee

> 双向重导向

```
tee [-a] file

-a：以累加的方式，将数据加入file中
```

#####tr

> 字符串转换命令

```
tr [-ds] SET1...

-d：删除信息中的SET1这个字符串
-s：取代字符
```

#####col

> 字符串转换命令

```
col [-xb]

-x：将tab键转换成对等的空格键
-b：在文字内有/时，仅保留最后接的那个字符
```

#####join

> 字符串转换命令

```
join [-ti12] file1 file2

-t：设置分隔符，默认为空格符
-i：忽略大小写
-1：代表第一个档案用哪个字段来分 析
-2：代表第二个档案用哪个字段来分析
```

#####paste

> 字符串转换命令

```
paste [-d] file1 file2

-d：后接分隔字符，默认为tab键
- ：表示来自standard input的资料
```

#####expand

> 字符串转换命令

```
expand [-t] file

-t：后接数字，表示一个tab键用几个空格替代
```

#####split

> 分隔命令

```
split [-bl] file PREFIX

-b：后接分割成的档案大小，可加单位，b，k，m等
-l：以行数来进行分割
PREFIX：代表前导符
```

#####xargs

> 参数替换

```
xargs [-Oepn] command

-O：当输入的stdin含有特殊字符时使用
-e：EOF（end of file），后接字符串，当xargs解析到这个字符串时，就会停止工作
-p：在执行每个指令的argument时，都会询问使用者
-n：后接次数，每次command指令执行时，要使用几个参数
```

#####sed

> sed工具

```
sed [-nefr] [动作]

-n：使用silent模式。在一般sed的用法中，所有来自stdin的数据一般都会被列出到屏幕上。加上后，只有经过sed特殊处理的那一行才会被列出来
-e：直接在命令行模式上进行sed的动作编辑
-f：后接filename，一个档案内的sed动作
-r：sed动作支持的扩展正则表达式语法
-i：直接修改档案内容，而不是屏幕输出

动作说明：[n1[,n2]]function
n1,n2：代表选择进行动作的列数
function：
  a：新增，后接字符串
  c：取代，后接字符串
  d：删除
  i：插入，后接字符串
  p：打印
  s：取代，后接正则
```

#####printf

> 格式化打印

```
printf '打印格式' 实际内容
```

#####awk

> 数据处理工具

```
awk '条件类型1 {动作1} 条件类型2 {动作2} ...' filename
```

#####diff

> 档案对比工具

```
diff [-bBi] from to

from：原始比对档案
to：目的比对档案
-b：忽略空白字符的差异
-B：忽略空白行的差异
-i：忽略大小写
```

#####cmp

> 档案对比工具

```
cmp [-s] file1 file2

-s：将所有不同字符全部列出来，默认只会输出第一个
```

#####patch

> 档案对比工具

```
patch -pN < file       //更新
patch -R -pN < file    //还原

-p：后接数字，取消几层目录的意思
-R：代表还原
```

#####管线命令

```
command1 | command2 | command3
将1的输出作为2的输入，将2的输出作为3的输入
```

## 权限与账号管理相关

#####umask

> 档案预设权限

```
umask 档案名
0022    //代表默认会拿掉的权限，以此为特殊权限、使用者、群组、其他人
```

#####chattr

> 配置文件隐藏属性

```
chattr [+-=] [ASacdistu] 档案与目录名称

+：增加某一个特殊参数，其他原本存在参数不动
-：移除某一个特殊参数，其他原本存在参数不动
=：后接设定的特殊参数

A：当设定了A属性时，存取档案时，访问时间atime不会改变
S：将对档案的修改同步写入磁盘中
a：设定后，档案只能增加数据，不能删除与不能修改数据，只有root才能设定一个属性
c：设定后，会将档案进行压缩保存，读取时自动解压
d：当dump程序被执行时，不会被dump备份
i：使一个档案不能被删除、改名、设定链接、写入或新增。只有root能设定这个属性
s：当档案设定s属性时，如果这个档案被删除，将会被完全移除出硬盘
u：与s相反
```

#####lsattr

> 显示档案隐藏属性

```
lsattr [-adR] 档案或目录

-a：将隐藏文件的属性也显示出来
-d：如果接的时目录，仅列出目录本身的属性而非目录内的文件名
-R：连同子目录的数据一起列出来
```

#####chmod

```
chmod [-R] xyz 档案或目录

-R：递归变更
数字类型代表档案权限
r：4，w：2，x：1
```

#####groups

> 观察有效与支持群组

#####newgrp

> 创建群组

```
newgrp 组名
```

#####useradd

> 新增使用者

```
useradd [-u UID] [-g 初始群组] [-G 次要群组] [-mM] [-c 说明档] [-d 家目录绝对路径] [-s shell] 使用者账号名

-u：后接UID
-g：后接组名
-G：后接组名
-M：强制不建立用户家目录（系统账号默认值）
-m：强制建立用户家目录（一般账号默认值）
-c：后接说明
-d：指定某个目录成为家目录，而不使用默认值
-r：建立一个系统账号
```

#####passwd

> 用户密码管理

```
passwd [--stdin]  //所有人都可以用来修改自己的密码
passwd [-l] [-u] [--stdin] [-S] [-n 天数] [-x 天数] [-w 天数] [-i 日期] 账号  //root专用

--stdin：可以通过管线来作为密码输入
-l：lock，会将/etc/shadow第二栏加上!使密码失效
-u：unlock
-S：列出密码相关参数
-n：后接天数，shadow的第4字段，不可修改密码天数
-x：后接天数，shadow的第5字段，必须改动密码天数
-w：后接天数，shadow的第6字段，密码过去前警告天数
-i：后接日期，shadow的第7字段，密码失效日期
```

#####chage

> 用户相关设置

```
chage [-ldEImMW] 账号名

-l：列出该账号的详细密码参数
-d：后接日期，shadow第3字段，最近一次修改密码日期
-E：后接日期，shadow第8字段，账号失效日期
-I：后接天数，shadow第7字段，密码失效日期
-m：后接天数，shadow第4字段，密码最短保留天数
-M：后接天数，shadow第5字段，密码多久需要进行修改
-W：后接天数，shadow第6字段，密码过期前警告日期
```

#####usermod

> 用户相关设置

```
usermod [-cdegGlsuLU] username

-c：后接账号说明
-d：后接账号家目录
-e：后接日期
-f：后接天数
-g：后接初始群组
-G：后接次要群组
-a：于-G合用，增加次要群组支持
-l：后接账号名称，即修改账号名称
-s：后接shell档案
-u：后接UID
-L：将用户密码冻结，使其无法登入
-U：解冻用户
```

#####userdel

> 删除用户

```
userdel [-r] username

-r：连同用户的家目录也一起删除
```

#####finger

> 用户拥有功能

```
finger [-s] username

-s：仅列出用户的账号、全名、终端机代号与登入时间等等
-m：列出与后接的账号相同者
```

#####chfn

> 用户拥有功能

```
chfn [-foph] [账号名]

-f：后接完成名称
-o：办公室房间号？
-p：办公室电话号码？？
-h：家庭电话号码？？？
```

#####chsh

> 用户拥有功能

```
chsh [-ls]

-l：列出目前系统上可用的shell，即/etc/shells的内容
-s：修改shell
```

#####id

> 获取用户id

```
id [username]
```

#####groupadd

> 新增群组

```
groupadd [-g gid] [-r] 组名

-g：后接GID
-r：建立系统群组
```

######groupmod

> 群组设置

```
groupmod [-g gid] [-n group_name] 群组名

-g：修改已有的GID
-n：修改已有的组名
```

#####groupdel

> 删除群组

```
groupdel [groupname]
```

#####gpasswd

> 群组管理员功能

```
gpasswd groupname
gpasswd [-A user1,..] [-M user2,..] groupname
gpasswd [-rR] groupname

无参数：代表给予groupname一个密码
-A：后接用户名，即群组管理员
-M：后接用户名，即加入的群组成员
-r：将groupname的密码移除
-R：使groupname的密码失效

群组管理员可执行动作：
gpasswd [-ad] user groupname

-a：将使用者加入群组
-d：将使用者移除群组
```

######setfacl

> 设定某个档案/目录的ACL

```
setfacl [-bkRd] [{-m|-x} acl参数] 目标文件名

-m：设定后续的acl参数给档案使用
-x：删除后续的acl参数
-b：移除所有的acl参数
-k：移除预设的acl参数
-R：递归
-d：设定预设acl参数
```

#####getfacl

> 获取某个档案/目录的ACL

```
getfacl filename

选项与setfacli相同
```

######su

> 使用者身份切换

```
su [-lm] [-c 指令] [username]

-：单纯使用-代表使用login-shell的变量档案读取方式来登入系统
-l：后接欲切换的使用者账号，也是login-shell的方式
-m：代表使用目前的环境设定，而不读取新使用者的配置文件
-c：仅进行一次指令
```

#####sudo

> 使用者身份切换

```
sudo [-b] [-u 新使用者账号]

-b：将后续指令放到背景中去执行
-u：后接欲切换的使用者，默认root
```

##磁盘与文件系统相关

#####dumpe2fs

> 查看文件系统信息

```
dumpe2fs [-bh] 装置文件名

-b：列出保留为坏轨的部分
-h：仅列出superblock的数据，不会列出其他区段内容
```

#####df

> 列出文件系统的整体磁盘使用量

```
df [-ahikHTm] [目录或文件名]

-a：列出所有文件系统，包括系统特有的/proc等文件系统
-k：以KBytes的容量显示各文件系统
-m：以MBytes的容量显示各文件系统
-h：以易阅读的GBytes、MBytes、KBytes等格式自行显示
-H：以M=1000K取代M=1024K的进位方式
-T：连同该partition的filesystem名称也列出
-i：不用硬盘容量，而以inode数量来表示

常用：hi
```

#####du

> 评估文件系统的磁盘使用量

```
du [-ahskm] 档案或目录名称

-a：列出所有档案与目录容量，因为默认仅统计目录底下的档案量而已
-h：以易读的方式显示
-s：列出总量，而不列出每个目录占用容量
-S：不包括子目录下的总计
-k：以KBytes列出
-m：以MBytes列出
```

#####fdisk

> 磁盘分区

```
fdisk [-l] 装置名称

-l：输出后面接的装置所有的partition内容。若仅有fdisk -l时，则系统将会把整个系统内能够搜索到的装置的partition均列出来

无法处理大于2TB的磁盘分区槽
```

#####mkfs

> 磁盘格式化

```
mkfs [-t 文件系统格式] 装置文件名

-t：可以接文件系统格式，例如ext3、ext2、vfat等（系统支持才有效）
```

#####fsck

> 磁盘检验

```
fsck [-t 文件系统] [-ACay] 装置名称

-t：后接文件系统，通常会自动分辨
-A：依据/etc/fstab的内容，将需要的装置扫描一遍
-a：自动修复检查到的有问题的
-y：与-a类似，但是某些filesystem仅支持-y这个参数
-C：可以再检验的过程中，使用一个直方图来显示目前的进度
```

#####badblocks

> 磁盘检验

```
badblocks -[svw] 装置名称

-s：在屏幕上列出进度
-v：在屏幕上列出进度
-w：使用写入的方式来测试
```

#####mount

> 磁盘挂载

```
mount -a
mount [-l]
mount [-t 文件系统] [-L label名] [-o 额外选项] [-n] 装置文件名 挂载点

-a：依照配置文件/etc/fstab的数据将所有未挂载的磁盘都挂载上来
-l：单纯的输入mount会显示当前挂载的信息，加上-l可增加Label名称
-t：后接文件系统类型
-n：默认情况下，系统会将实际挂载的情况实时写入/etc/mtab中，加上后不会写入
-L：系统除了利用装置文件名之外，还可以利用文件系统的Label来进行挂载
-o：后面可以接一些挂载时额外加上的参数
```

#####umount

> 磁盘卸除

```
umount [-fn] 装置文件名或挂载点

-f：强制执行
-n：不更新/etc/mtab情况下卸除
```

#####mknod

> 磁盘参数修订

```
mknod 装置文件名 [bcp] [Major] [Minor]

装置种类：
  b：设定装置名称成为一个周边存储设备档案
  c：设定装置名称成为一个周边输入设备档案
  p：设定装置名称成为一个FIFO档案
Major：主要装置代码
Minor：次要装置代码
```

#####hdparm

> 磁盘参数修订

```
hdparm [-icdmXTt] 装置名称

-i：将核心侦测到的硬盘参数显示出来
-c：设定32-bit存取模式
-d：设定是否启用dma模式
-m：设定同步读取多个sector模式
-X：设定UtraDMA模式
-T：测试暂存区的存取性能
-t：测试硬盘的实际存取性能
```

#####quotacheck

> 扫描文件系统并建立quota的记录文件

```
quotacheck [-avugfM] [/mount_point]

-a：扫描所有在/etc/mtab内，含有quota支持的filesystem
-u：针对用户扫描档案与目录的使用情况，会建立aquota.user
-g：针对群组扫描档案与目录的使用情况，会建立aquota.group
-v：显示扫描过程
-f：强制扫描文件系统，并写入新的quota配置文件中
-M：强制以读写的方式扫描文件系统
```

######quotaon

> 启动quota服务

```
quotaon [-avug]
quotaon [-vug] [/mount_point]

-u：针对使用者启动quota（aquota.user）
-g：针对群组启动quota（aquota.group）
-v：显示启动过程
-a：根据/etc/mtab内的filesystem设定启动有关的quota
```

#####quotaoff

> 关闭quota服务

```
quotaoff [-a]
quotaoff [-ug] [/mount_point]

-a：关闭全部
-u：仅针对后接的mount_point关闭user quota
-g：仅针对后接的mount_point关闭group quota
```

#####edquota

> 编辑账号/群组的限制与宽限时间

```
edquota [-u username] [-g groupname]
edquota -t  //修改宽限时间
edquota -p 范本账号 -u 新账号

-u：后接账号名称
-g：后接组名
-t：后接修改宽限时间
-p：复制范本
```

#####quota

> 单一用户的quota报表

```
quota [-uvs] [username]
quota [-gvs] [groupname]

-u：后接username
-g：后接groupname
-v：显示每个用户在filesystem的quota值
-s：使用1024位倍数来指定单位
```

#####repquota

> 针对文件系统的限额做报表

```
requota -a [-vugs]

-a：直接到/etc/mtab搜寻具有quota标志的filesystem，并报告quota结果
-v：输出的数据将含有filesystem相关的详细信息
-u：显示用户的quota限值（默认值）
-g：显示群组的quota限值
-s：使用M，G为单位显示结果
```

#####warnquota

> 对超过限额者发出警告信

#####setquota

> 直接设定quota配额

```
setquota [-u|-g] 名称 block(soft) block(hard) inode(soft) inode(hard) 文件系统
```

#####mdadm

> 软件磁盘阵列

```
mdadm --detail /dev/md0
mdadm --create --auto=yes /dev/md[0-9] --raid-devices=N --level=[015] --spare-devices=N /dev/sdx /dev/hdx..
mdadm --manage /dev/md[0-9] [--add 装置] [--remove 装置] [--fail 装置]

--create：建立RAID选项
--auto=yes：后接建立软件磁盘阵列的装置
--raid-devices=N：使用多个磁盘作为磁盘阵列装置
--spare-devices=N：使用多个磁盘作为备用装置
--level=[015]：设定这组磁盘阵列的等级
--detail：后接磁盘阵列的详细信息
--add：将后接装置加入md
--remove：将后接装置移出md
--fail：将后接装置设定为fail状态
```

##网络相关

#####ifconfig

> 设定与启动/关闭IP参数

```
ifconfig [interface] [up|down]  //观察与启动接口
ifconfig [interface] [options]  //设定与修改接口

interface：网络卡接口代号
options：
  up，down：启动或关闭该网络接口
  mtu：可以设定不同的MTU数值
  netmask：子屏蔽wangluo
  broadcast：广播地址
```

#####ifup

> 启动网络接口

```
ifup [interface]
```

#####ifdown

> 关闭网络接口

```
ifdown [interface]
```

#####route

> 路由修改

```
route [-nee]
route add [-net|-host] [网络或主机] netmask [mask]
route del [-net|-host] [网络或主机] netmask [mask]

-n：不使用通讯协议或主机名，直接使用IP或port number
-ee：使用更详细的信息来显示
-net：后接路由为一个网域
-host：后接路由为一个主机
netmask：与网域有关，可以设定netmask决定网域的大小
gw：gateway，后接IP
dev：指定由哪一块网络卡联机出去
```

#####ip

> 网络参数综合指令

```
ip [option] [动作] [指令]

option：
  -s：显示出该装置的统计数据

ip [-s] link show

show：仅显示出这个装置的相关内容
set：可以设定的项目
  device：界面代号
  动作：
    up|down：启动或关闭某个接口
    address：可以用来修改MAC，如果装置允许
    name：给予装置名字
    mtu：最大传输单元

ip address show
ip address [add|del] [IP 参数] [dev 装置名] [相关参数]

show：显示IP信息
add|del：增加或删除相关参数
dev：IP参数所要设定的接口
相关参数：
  broadcast：设定广播地址
  label：装置别名
  scope：
    global：允许所有来源的联机
    site：仅支持IPv6，仅允许本主机的联机
    link：仅允许本装置自我联机
    host：仅允许本主机内部联机

ip route show
iproute [add|del] [IP或网域] [via gateway] [dev 装置]

show：单纯显示路由表，也可以使用list
add|del：增加或删除路由
via：由后接gateway出去，不一定需要
dev：由后接装置出去，需要
mtu：最大传输单元
```

#####iwlist

> 利用无线网卡进行无线AP的侦测与取得相关的数据

#####iwconfig

> 设定无线网卡的相关参数

#####dhclient

> 手动使用DHCP自动取得IP参数

```
dhclient xxx  //用后接网络卡以dhcp协议获取IP
```

#####ping

> 两主机两点沟通

```
ping [选项与参数] IP

-c 数值：后接执行ping的次数
-n：输出数据时不进行IP与主机名反查，直接使用IP输出
-s 数值：发送出去的ICMP封包大小，默认56bytes
-t 数值：TTL数值，默认255，每经过一个节点少一
-W 数值：等待响应的秒数
-M [do|dont]：主要再侦测网络的MTU数值大小
  do：代表传送一个DF（Dont't Fragment）旗标，让封包不能重新拆包与打包
  dont：代表不传送，封包可以在其他主机上拆包与打包
```

#####traceroute

> 两主机间各节点分析

```
traceroute [选项与参数] IP

-n：使用IP，不需要进行域名解析
-U：使用UDP来进行侦测，默认
-I：使用ICMP来进行侦测
-T：使用TCP来进行侦测
-w：最大未响应的秒数
-p：端口号
-i 装置：使用在比较复杂的环境
-g 路由：与-i相似，后接gateway的IP
```

#####netstat

> 本机的网络联机

```
netstat -[rn]       //与路由有关的参数
netstat -[antulpc]  //与网络接口有关的参数

-r：列出路由表
-n：不使用主机名与服务名，使用IP与port number
-a：列出所有的联机状态
-t：仅列出TCP封包的联机
-u：仅列出UDP封包的联机
-l：仅列出在Listen的服务的网络状态
-p：列出PID与程序档名
-c：更新频率
```

#####host

> 侦测主机名与IP对应

```
host [-a] hostname [server]

-a：列出该主机详细的各项主机名设定数据
```

#####nslookup

> 侦测主机名与IP对应

```
nslookup [-query=[type]] [hostname|IP]

-query=type：查询的类型
```

#####telnet

> 终端机与BBS联机

```
telnet [host|IP [port]]
```

#####ftp

> FTP联机软件

```
ftp [host|IP] [port]
```

#####lftp

> FTP联机软件

```
lftp [-p port] [-u user[, pass]] [host|IP]
```

#####links

> 文字浏览器

```
links [options] [URL]

-anonymous [0|1]：是否使用匿名登录的意思
-dump [0|1]：是否将网页的数据直接输出到过standard out而非links软件功能
-dump_charset：后接要透过dump输出到屏幕的编码
```

#####wget

> 文字接口下载器

```
wget [option] [网址]

当联机网站需要提供账号密码时可以利用以下两个参数：
--http-user=username
--http=password=password
--quiet：不显示wget在抓取数据时显示的信息
```

#####tcpdump

> 文字接口封包截取器

```
tcpdump [-AennqX] [-i 接口] [-w 储存档名] [-c 次数] [-r 档案] [所欲截取的封包数据格式]

-A：封包的内容以ASCII显示，通常用来抓取WWW的网页资料
-e：使用资料连接层的MAC封包数据来显示
-nn：直接以IP及port number显示，而非主机名与服务名称
-q：仅列出较为简短的封包信息
-X：可以列出16进制以及ASCII的封包内容，对于监听封包内容有用
-i：后接要监听的网络接口
-w：后接档名，将监听的数据储存下来
-r：从后接档案将封包数据读出，由-w制作
-c：监听的封包数
```

#####nc

> 任意启动TCp/UDP封包的端口联机

```
nc [-u] [IP|host] [port]
nc -l [IP|host] [port]

-l：开启一个port来监听用户的联机
-u：不使用TCP而是使用UDP作为联机的封包协议
```

##其他

#####chkconfig

> 管理系统服务默认开机启动与否

```
chkconfig --list [服务名称]
chkconfig [--level [0123456]] [服务名称] [on|off]
chkconfig [--add|--del] [服务名称]

--list：将目前各项服务状态列出来
--level：设定某个服务在该level下启动或关闭
--add：增加一个服务各chkconfig管理，该服务必须在/etc/init.d/内
--del：删除一个交给chkconfig管理的任务
```

#####logrotate

> 测试

```
logrotate [-vf] logfile

-v：显示过程
-f：强制对每个登录档进行rotate
```

#####make

> 编译源码

```
make clean
make
make install
```

#####ldconfig

> 动态与静态函式库

```
ldconfig [-f conf] [-C cache]
ldconfig [-p]

-f conf：使用指定的conf作为函式库取得路径，而不以/etc/ld.so.cof为默认值
-C cache：使用cache作为快取暂存的函式库资料，而不以/etc/ld.so.cache为默认值
-p：列出目前所有的函式库资料
```

#####ldd

> 程序的动态函式库解析

```
ldd [-vdr] [filename]

-v：列出所有内容信息
-d：显示资料有遗失的link点
-r：显示ELF有关的错误内容
```

######md5sum/sha1sum

> 检验软件的正确性

```
md5sum/sha1sum [-bct] filename
md5sum/sha1sum [--status|--warn] --check filename

-b：使用二进制的读档方式，默认为windows/dos档案形态的读取方式
-c：检验档案指纹
-t：以文字形态来读取档案指纹
```

#####depmod

> 核心模块与相依性

```
depmod [-Ane]

-A：更新modules.dep
-n：不写入modules.dep，直接输出到屏幕上
-e：显示目前已加载的不可执行模块
```

#####lsmod

> 核心模块的观察

#####modinfo

> 核心模块的观察

```
modinfo [-adln] [module_name|filename]

-a：仅列出作者名称
-d：仅列出该modules的说明（description）
-l：仅列出授权（license）
-n：仅列出该模块的详细路径
```

#####insmod

> 核心模块的加载

```
insmod [/full/path/module_name] [parameters]
```

#####rmmod

> 核心模块的卸除

```
rmmod [-fw] module_name

-f：强制删除
-w：若模块正在使用，则等待该模块使用完毕后再移除
```

#####modprobe

> 核心模块的查看

```
modprobe [-lcfr] module_name

-c：列出目前系统所有模块
-l：列出磨枪再/lib/modules/uname/kernel当中的所有模块完整文件名
-f：强制加载模块
-r：移除模块
```

#####mkinitrd

> 建立新initrd档案

```
mkinitrd [-v] [--with=模块名称] initrd 文件名 核心版本

-v：显示mkinitrd的运作过程
initrd档名：要建立的initrd档名
```
