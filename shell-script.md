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
|---|---|
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

###条件判断式

####if...then

```
单层简单条件判断式
if [条件判断式]; then
        当条件判断式成立时，执行
fi

多重复杂条件判断式
if [条件判断式]; then
        当条件判断式成立时，执行
else
        当条件判断式不成立时，执行
fi

if [条件判断式1]; then
        当条件判断式1成立时，执行
elif [条件判断式2]; then
        当条件判断式2成立时，执行
else
        当条件判断式1、2都不成立时，执行
fi
```

####case...esac

```
case $变量名称 in
 "第一个变量内容")
    程序段
    ;;
 "第二个变量内容")
    程序段
    ;;
 *)               //最后一个变量内容会用*来代表所有值
    程序段
    ;;
esac
```

####function

```
function fname() {
    程序段
}
```

###循环

####while do done,until do done

```
while [condition]
do
    程序段
done

until [condition]
do
    程序段
done
```

####for...do...done

```
for var in con1 con2 ...
do
    程序段
done

for ((初始值;限制值;执行步阶))
do
    程序段
done
```

###shell script的追踪于debug

```
sh [-nvx] script.sh

-n：不执行script，仅检查语法
-v：执行script之前，先把script的内容输出到屏幕上
-x：将使用到的script内容显示到屏幕上
```









