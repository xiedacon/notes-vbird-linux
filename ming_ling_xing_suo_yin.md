# 命令行索引


* ls

ls [-aAdfFhilnrRSt] 目录名称

```
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

* cd 改变目录

```
.  代表这一层目录
.. 代表上一层目录
-  代表前一个工作目录
~  代表当前用户的home目录
```

* pwd (Print Working Directory)

pwd [-P]

```
-P：显示出确定的路径，而非使用link路径
```

* mkdir

mkdir [-mp] 目录名称
```
-m：配置文件的权限
-p：建立多层目录
```

* rm

rm [-fir] 档案或目录
```
-f：force 强制执行，忽略警告信息
-i：互动模式，在删除前询问是否删除
-r：递归执行
```

* mv

mv [-fiu] source destination
mv [option] source1 source2 ... directory
```
-f：强制执行
-i：互动模式
-u：若目标档案已存在，且source更新，才会更新
```

* cp

cp [-adfilprsu] source destination
cp [options] source1 source2 ... directory
```
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

* cat (concatenate)浏览文档

cat [-AbEnTv]

```
-A：相当于-vET
-b：列出行号，空白行不标行号
-E：显示断行字符$
-n：列出行号，连同空白行
-T：将tab键以^I显示
-v：列出一些看不出来的特殊字符
```

* touch 建立一个空档/修订时间

touch [-acdmt] 档案
```
modification time (mtime)：内容改变时更新
status time (stime)：状态改变时更新
access time (atime)：读取时更新

-a：仅修改access time
-c：仅修改档案的时间，若档案不存在则不创建新档
-d：后面可以接欲修订的时间而不用目前的时间，也可以使用--date="日期或时间"
-m：仅修改mtime
-t：后面可以接欲修订的时间而不用目前的时间，格式为[YYMMDDhhmm]
```

* more
* less
* head
* tail
* ps
* top
* kill
* killall
* bg
* fg
* jobs
* tar
* gzip
* grep
* 管线命令
* locate
* chmod




