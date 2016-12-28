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
  - [rm](#rm)
  - [mv](#mv)
  - [cp](#cp)
  - [cat](#cat)
  - [touch](#touch)
  - [more](#more)
  - [less](#less)
  - [head](#head)
  - [tail](#tail)
  

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
  - [grep](#grep)
  - [管线命令](#管线命令)
  

* [权限相关](#权限相关)
  - [locate](#locate)
  - [chmod](#chmod)
  

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

```
ls [-aAdfFhilnrRSt] 目录名称

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

>Print Working Directory

```
pwd [-P]

-P：显示出确定的路径，而非使用link路径
```

#####mkdir

```
mkdir [-mp] 目录名称

-m：配置文件的权限
-p：建立多层目录
```

#####rm

```
rm [-fir] 档案或目录

-f：force 强制执行，忽略警告信息
-i：互动模式，在删除前询问是否删除
-r：递归执行
```

######mv

```
mv [-fiu] source destination  
mv [option] source1 source2 ... directory

-f：强制执行
-i：互动模式
-u：若目标档案已存在，且source更新，才会更新
```

#####cp

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
```

#####cat

>concatenate 浏览文档

```
cat [-AbEnTv]

-A：相当于-vET
-b：列出行号，空白行不标行号
-E：显示断行字符$
-n：列出行号，连同空白行
-T：将tab键以^I显示
-v：列出一些看不出来的特殊字符
```

#####touch

>建立一个空档/修订时间

```
touch [-acdmt] 档案

modification time (mtime)：内容改变时更新
status time (stime)：状态改变时更新
access time (atime)：读取时更新

-a：仅修改access time
-c：仅修改档案的时间，若档案不存在则不创建新档
-d：后面可以接欲修订的时间而不用目前的时间，也可以使用--date="日期或时间"
-m：仅修改mtime
-t：后面可以接欲修订的时间而不用目前的时间，格式为[YYMMDDhhmm]
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

> 取出前面几行

```
head [-n number] 档案

-n：后接数字，代表行数
```

#####tail

> 取出后面几行

```
tail [-n number] 档案

-n：后接数字，代表行数
-f：表示持续侦测后面所接的档名
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

#####locate

```
locate [-ir] keyword

-i：忽略大小写
-r：正则表达式
```

#####chmod

```
chmod [-R] xyz 档案或目录

-R：递归变更
数字类型代表档案权限
r：4，w：2，x：1
```



