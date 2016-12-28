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
  

* [程序管理相关](#程序管理相关)
  - [ps](#ps)
  - [top](#top)
  - [jobs](#jobs)
  - [kill](#kill)
  - [killall](#killall)
  - [bg](#bg)
  - [fg](#fg)
  - [tar](#tar)
  - [gzip](#gzip)
  

* [压缩相关](#压缩相关)
  - [tar](#tar)
  - [gzip](#gzip)
  

* [搜索相关](#搜索相关)
  - [which](#which)
  - [whereis](#whereis)
  - [locate](#locate)
  - [find](#find)
  - [grep](#grep)
  - [管线命令](#管线命令)
  

* [权限相关](#权限相关)
  - [umask](#umask)
  - [chattr](#chattr)
  - [lsattr](#lsattr)
  - [chmod](#chmod)
  
* [磁盘相关](#磁盘相关)
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

## 程序管理相关

#####ps

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

#####jobs

> 观察当前背景工作状态

```
jobs [-lrs]

-l：除了列出jobnumber与指令串之外，同时列出PID的号码
-r：仅列出正在run的工作
-s：仅列出正在stop的工作
```

#####kill

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

> 让一个工作在背景下运行

```
bg % jobnumber
```

#####fg

> 将背景工作拿到前景来处理

```
fg % jobnumber
```

## 压缩相关

#####tar

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

#####gzip

```
gzip [-cdtv#] 档名

-c：将压缩的数据输出到屏幕上，可透过数据流重导向来处理
-d：解压缩的参数
-t：可以用来检验一个压缩文件的一致性
-v：可以显示出原档案/压缩文件的压缩比等信息
-#：压缩等级。-1最快，但压缩比差。-9最慢，但压缩比好。预设是-6
```

## 搜索相关

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

#####grep

```
grep [-acinv] [--color=auto] '搜索字符串' filename

-a：将binary档案以text档案方式搜寻数据
-c：计算找到'搜寻字符串'的次数
-i：忽略大小写
-n：输出行号
-v：反向选择
--color=auto：将找到的关键字加上颜色显示
```

#####管线命令

```
command1 | command2 | command3
将1的输出作为2的输入，将2的输出作为3的输入
```

## 权限相关

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

##磁盘相关

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