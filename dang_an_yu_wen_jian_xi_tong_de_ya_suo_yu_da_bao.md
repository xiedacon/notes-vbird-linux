# 档案与文件系统的压缩与打包


###Linux系统常见的压缩指令

|扩展名|描述|
|--|--|
|*.Z|compress程序压缩的档案|
|*.gz|gzip程序压缩的档案|
|*.bz|bzip2程序压缩的档案|
|*.tar|tar程序打包的数据，并没有压缩过|
|*.tar.gz|tar程序打包的档案，并经过gzip的压缩|
|*.tar.bz2|tar程序打包的档案，并经过bzip2的压缩|

####compress

```
compress [-rcv] 档案或目录   //压缩
uncompress 档案.Z         //解压

-r：可以连同目录下的档案一起压缩
-c：将压缩数据输出成为standard output
-v：可以显示压缩后的档案信息以及压缩过程中的一些档名变化
```

####gzip，zcat

```
gzip [-cdtv#] 档名
zcat 档名.gz

-c：将压缩的数据输出到屏幕上，可透过数据流重导向来处理
-d：解压缩的参数
-t：可以用来检验一个压缩文件的一致性，查看档案有无错误
-v：可以显示出原档案/压缩文件的压缩比等信息
-#：压缩等级，-1最快，但压缩比最差，-9最慢，但是压缩比最好，默认-6
```

####bzip2，bzcat

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

###打包指令：tar

```
tar [-j|-z] [cv] [-f 操作档案] filename...    //打包与压缩
tar [-j|-z] [tv] [-f 操作档案]            //查看档名
tar [-j|-z] [xv] [-f 操作档案] [-C 目录]     //解压缩

-c：建立打包档案，可搭配-v来查看过程中被打包的档名
-t：查看打包档案的内容含有哪些档名
-x：解打包与解压缩的功能，可以搭配-C在特定目录解开
-j：透过bzip2进行压缩/解压，此时档名最好为*.tar.bz2
-z：透过gzip进行压缩/解压，此时档名最好为*.tar.gz
-v：在压缩/解压的过程中，将正在处理的文件名显示出来
-f：后接要被处理的档名，建议-f单独写
-C：后接目录，在此目录解压缩
-p：保留备份数据的原本权限与属性，常用于备份重要的配置文件
-P：保留绝对路径，即允许备份数据中含有根目录存在的意思
--exclude=FILE：在解压过程中，不要将FILE打包
```

###备份工具

####dump

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

####restore

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

###其它常见的压缩与备份工具

####dd

```
dd if="input_file" of="output_file" bs="block_size" count="number"

if：input file，也可以是装置
of：output file，也可以是装置
bs：规划一个block大小，默认512bytes
count：bs个数
```

####cpio

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










