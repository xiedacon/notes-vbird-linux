# Linux档案与目录管理

###目录的相关操作

####cd：更换目录

```
cd [相对路径或绝对路径]
```

####pwd：显示当前目录

```
pwd [-P]

-P：显示出确实的路径，而非使用链接（link）路径
```

####mkdir：新建目录

```
mkdir [-mp] 目录名称

-m：直接设置文件的权限
-p：建立多层目录
```

####rmdir：删除空的目录

```
rmdir [-p] 目录名称

-p：连同上层空的目录一起删除
```

###档案与目录管理

####ls：查看档案与目录

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

####cp：复制档案或目录

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

####rm：移除档案或目录

```
-f：force 强制执行，忽略警告信息
-i：互动模式，在删除前询问是否删除
-r：递归执行（非常危险的选项）
```

####mv：移动档案与目录，或改名

```
mv [-fiu] source destination
mv [option] source1 source2 ... directory

-f：强制执行
-i：互动模式
-u：若目标档案已存在，且source更新，才会更新
```

####取得路径的文件名与目录名称

```
获取路径文件名
  basename 路径
  
获取目录
  dirname 路径
```

###查看档案内容

####cat：由第一行开始显示档案内容

```
cat [-AbEnTv]

-A：相当于-vET
-b：列出行号，空白行不标行号
-E：显示断行字符$
-n：列出行号，连同空白行
-T：将tab键以^I显示
-v：列出一些看不出来的特殊字符
```

####tac：由最后一行开始显示

```
正好与cat相反
```

####nl：显示时，顺便输出行号

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

####more：一页一页的显示档案内容

```
space：代表下一页
enter：代表下一行
/字符串：代表向下搜寻字符串
:f：立刻显示出文件名以及目前显示的行数
q：离开
b或ctrl b：代表往回翻页，只对档案有用，对管线无用
```

####less：一页一页的显示档案内容

```
space：代表下一页
pagedown：代表下一页
pageup：代表上一页
/字符串：代表向下搜寻字符串
?字符串：代表向上搜寻字符串
n：重复前一个搜寻
N：反向重复前一个搜寻
q：离开
```

####head：只看头几行

```
head [-n number] 档案

-n：后接数字，表示显示几行，默认显示前20行
```

####tail：只看最后几行

```
tail [-n number] 档案

-n：后接数字，表示显示几行，默认显示10行
-f：表示持续侦测后面所接的档名，直到ctrl c才会结束tail的侦测
```

####od：读取非纯文本文档

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

####touch：修该档案时间或建立新档

```
modification time(mtine):
  当该档案的数据内容改变时，就会更新这个时间
status time(ctime):
  当该档案的状态（权限与属性）改变时，就会更新这个时间
access time(atime)：
  当该档案的内容被取用时，就会更新这个读取时间
  
touch [-acdmt] 档案
 
-a：仅修订access time
-c：仅修该档案的时间，若该档案不存在则不建立新档案
-d：后面可以接欲修订的日期而不用当前日期，也可以使用--date="日期或时间"
-m：仅修该mtime
-t：后面可以接欲修订的时间而不是用当前时间，格式为[YYMMDDhhmm]
```

###档案与目录的默认权限与隐藏权限

####umask：档案预设权限

```
umask
0022

代表默认会拿掉的权限，以此为特殊权限、使用者、群组、其他人
```

####chattr：配置文件隐藏属性

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

####lsattr：显示档案隐藏属性

```
lsattr [-adR] 档案或目录

-a：将隐藏文件的属性也显示出来
-d：如果接的时目录，仅列出目录本身的属性而非目录内的文件名
-R：连同子目录的数据一起列出来
```

####档案特殊权限：SUID、SGID、SBIT

#####SUID：4

* 仅对二进制程序有效
* 执行者对于该程序需要有x的可执行权限
* 本权限仅在执行该程序的过程中有效
* 执行者具有该程序拥有者的权限

#####SGID:2

* 仅对二进制程序有效
* 执行者对于该程序需要有x的可执行权限
* 本权限仅在执行该程序的过程中有效
* 执行者具有该程序群组的权限

#####SBIT：1

* 只对目录有效
* 当用户具有w、x权限时，就具有r权限
* 当用户在该目录下建立档案或目录时，仅有自己与root才有权利删除档案

###指令与档案的搜寻

####which：脚本文件名的搜寻

```
which [-a] command

-a：将所有有PATH目录中可以找到的指令均列出，而不止第一个被找到的指令名称
```

####whereis：寻找特定档案（通过内部数据库）

```
whereis [-bmsu] 档案或目录名

-b：只找二进制格式的档案
-m：只找在说明文件manual路径下的档案
-s：只找source来源档案
-u：搜寻不在上述三个项目当中的其他特殊档案
```

####locate：按档案名寻找档案（通过内部数据库）

```
locate [-ir] keyword

-i：忽略大小写的差异
-r：后面可接正则表达式
```

####find：在磁盘中寻找档案

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













