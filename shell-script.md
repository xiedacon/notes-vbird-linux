#Shell Scripts

shell script的良好习惯：

在每个script文件头处记录

* script的功能
* script的版本信息
* script的作者与联系方式
* script的版权宣告方式
* script的历史纪录
* script内较特殊的命令
* script运行是需要的环境变量与设定

###script的执行方式差异（source,sh script,./script）

####直接执行script

![](/assets/在子程序中运行.png)

####利用source来执行脚本

![](/assets/在父程序中运行.png)

###善用判断式

####利用test指令的测试功能

```
test 标志 档名
```

|标志|意义|
|--|--|
|-e|该档名是否存在（常用）|
|-f|该档名是否存在且为档案（常用）|
|-d|该档名是否存在且为目录（常用）|
|-b|该档名是否存在且为一个block device|
|-c|该档名是否存在且为一个character device|
|-S|该档名是否存在且为一个Socket档案|
|-p|该档名是否存在且为一个FIFO档案|
|-L|该档名是否存在且为一个链接档|
|-r|检测该档名是否存在且具有可读权限|
|-w|检测该档名是否存在且具有可写权限|
|-x|检测该档名是否存在且具有可执行权限|
|-u|检测该档名是否存在且具有SUID属性|
|-g|检测该档名是否存在且具有SGID属性|
|-k|检测该档名是否存在且具有Sticky bit属性|
|-s|检测该档名是否存在且为非空白档案|
|示例|test file1 -nt file2|
|-nt|(newer than)判断file1是否比file2新|
|-ot|(older than)判断file1是否比file2旧|
|-ef|判断file1与file2是否为同一档案|
|示例|test n1 -eq n2|
|-eq|两数值相等|
|-ne|两数值不等|
|-gt|n1大于n2|
|-lt|n1小于n2|
|-ge|n1大于等于n2|
|-le|n1小于等于n2|
|test -z string|判断字符串是否为空，为空返回true|
|test -n string|判断字符串是否非空，为空返回false|
|test str1=str2|判断str1是否等于str2，相等返回true|
|test str1!=str2|判断str1是否等于str2，相等返回false|
|示例|test -r filename -a -a filename|
|-a|and，两情况同时成立返回true|
|-o|or，两情况任何一个成立返回true|
|!|反向|

####利用判断符号[]

```
[-z "$HOME"];echo $?
[ $"HOME" == "$MAIL" ]
```

####shell script的默认变量($0,$1...)

```
/xx/scriptname opt1 opt2 opt3...
$0             $1   $2   $3  ...

$#：代表参数个数
$@：代表所有参数
$*：代表"$1c$2c$3"，c为分隔符号，默认为空格键
```

shift：变量号码偏移

```
shift n

代表拿掉最前面的n个参数，n默认为1
```





















