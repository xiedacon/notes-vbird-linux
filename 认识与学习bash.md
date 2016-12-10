# 学习与认识BASH

### Bash shell的功能

* 命令行编辑能力（history）
* 命令与档案补全功能（tab键）
* 命令别名设定功能（alias）
* 工作控制、前景背景控制（job contrpl，foreground，background）
* 程序化脚本（shell script）
* 通配符（wildcard）

#### Bash shell的内建命令：type

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

### Shell的变量功能

#### 变量的取用与设定

变量的取用：echo

```
echo $variable
```

取消变量：unset

    unset name``

#### 环境变量的功能

* env：观察环境变量
* set：观察所有变量
* export：将自定义变量转成环境变量

#### 变量键盘读取、数组与宣告：read、array、declare

read

```
read [-pt] variable

-p：后接提示字符
-t：后接等待秒数
```

declare

```
declare [-aixr] variable

-a：将后接变量定义为数组
-i：将后接变量定义为整型数字
-x：将后接变量导出为环境变量
-r：将后接变量定义为readonly类型，不能修改，也不能unset
```

#### 限制用户的系统资源使用量：ulimit

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

#### 变量内容的删除、取代与替换

变量内容的删除与取代

| 变量设定方式 | 说明 |
| --- | --- |
| ${变量\#关键词} | 从头开始，将符合关键词的最短数据删除 |
| ${变量\#\#关键词} | 从头开始，将符合关键词的最长数据删除 |
| ${变量%关键词} | 从尾开始，将符合关键词的最短数据删除 |
| ${变量%%关键词} | 从尾开始，将符合关键词的最长数据删除 |
| ${变量/旧字符串/新字符串} | 将第一个匹配的旧字符串替换成新字符串 |
| ${变量//旧字符串/新字符串} | 将全部匹配的旧字符串替换成新字符串 |

变量的测试与内容替换

| 变量设定方式 | str没有设定 | str为空字符串 | str已设定非为空字符串 |
| :--- | :--- | :--- | :--- |
| var=${str-expr} | var=expr | var= | var=$str |
| var=${str:-expr} | var=expr | var=expr | var=$str |
| var=${str+expr} | var= | var=expr | var=expr |
| var=${str:+expr} | var= | var= | var=expr |
| var=${str=expr} | str=expr,var=expr | str不变,var= | str不变,var=$str |
| var=${str:=expr} | str=expr,var=expr | str=expr,var=expr | str不变,var=$str |
| var=${str?expr} | expr输出至stderr | var= | var=$str |
| var=${str:?expr} | expr输出至stderr | expr输出至stderr | var=$str |

### 命令别名与历史命令

#### 命令别名设定

```
alias xx='xxx'
unalias xx
```

#### 历史命令：history

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

### Bash Shell的操作环境

#### 路径与指令搜寻顺序

1. 以相对/绝对路径执行指令
2. 由alias找到指令并执行
3. 由bash内建指令执行
4. 透过$PATH这个变量的顺序搜寻到的第一个指令来执行

#### bash进站与欢迎信息：/etc/issue

#### bash的环境配置文件

* login shell：取得bash时需要完整的登入流程的称为login shell

* non-login shell：取得bash接口的方法不需要重复登入的举动


login shell会读取的档案：

1. /etc/profile：系统整体的设定
2. ~/.bash\_profile或~/.bash\_login或~/.profile：属于使用者个人设定

#### 读入环境配置文件的指令：source

```
source 配置文件档名
```

#### 终端机环境设定：stty，set

```
stty [-a]

-a：将目前所有的stty参数列出来
```

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

#### 通配符与特殊符号

通配符

| 符号 | 意义 |
| --- | --- |
| \* | 0到无穷多个 |
| ? | 一定有一个 |
| \[\] | 一定有一个在括号内 |
| \[-\] | 在编码顺序内的所有字符 |
| [^] | 反向选择 |

特殊符号

| 符号 | 内容 |
| --- | --- |
| \# | 批注符号 |
| \ | 跳脱符号 |
| \| | 管线命令 |
|;|连续指令下达分隔符|
|~|用户的家目录|
|$|取用变量前导符|
|&|工作控制|
|!|逻辑非|
|/|目录符号|
|>,>>|数据流重导向，输出导向|
|<,<<|数据流重导向，输入导向|
|''|单引号，不具备变量置换的功能|
|""|具有变量置换的功能|
|``|中间为可以先执行的指令，亦可使用${}|
|()|在中间为子shell的起始与结束|
|{}|在中间为命令区块的组合|

