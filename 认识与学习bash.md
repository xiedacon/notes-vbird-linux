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

###数据流重导向

![](/assets/指令执行过程中的数据传输情况.png)

* standard output：标准输出，指令执行所回传的正确信息
* standard error output：标准错误输出，指令执行失败后，所回传的错误信息
* standard input：标准输入

1. 标准输入（stdin）：代码为0，使用<或<<
2. 标准输出（stdout）：代码为1，使用>或>>
3. 标准错误输出（stderr）：代码为2，使用2>或2>>

* 输出：一个表示覆盖，两个表示累加
* 输入：两个表示结束的输入字符
* 垃圾桶黑洞：/dev/null

####命令执行的判断依据：; && ||

###管线命令（pipe）

```
command1 | command2

使用|这个界定符号，将command1的输出作为command2的输入
```

![](/assets/管线命令的处理示意图.png)

* 管线命令仅会处理standard output，对于standard error output会予以忽略
* 管线命令必须能接受来自前一个指令的数据作为standard input继续处理

####截取命令

cut

```
cut -d '分隔字符' -f fields     //用于由特定分隔字符
cut -c 字符区间                 //用于排列整齐的信息

-d：后接分隔字符，与-f一起使用
-f：依据-d的分隔字符将一段信息分割成数段，用-f取出第几段
-c：以字符的单位取出固定字符区间
```

grep

```
grep [-acinv] [--color=auto] '搜寻字符串' filename

-a：将二进制档案以text档案的方式搜寻数据
-c：计算找到搜寻字符串的次数
-i：忽略大小写
-n：输出行号
-v：反向选择
--color=auto：将找到的关键字部分加上颜色
```

####排序命令

sort

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

uniq

```
uniq [-ic]

-i：忽略大小写字符的不同
-c：进行计数
```

wc

```
wc [-lwm]

-l：仅列出行
-w：仅列出字数
-m：字符数
```

####双向重导向：tee

![](/assets/tee的工作流程示意图.png)

```
tee [-a] file

-a：以累加的方式，将数据加入file中
```

####字符串转换命令

tr

```
tr [-ds] SET1...

-d：删除信息中的SET1这个字符串
-s：取代字符
```

col

```
col [-xb]

-x：将tab键转换成对等的空格键
-b：在文字内有/时，仅保留最后接的那个字符
```

join

```
join [-ti12] file1 file2

-t：设置分隔符，默认为空格符
-i：忽略大小写
-1：代表第一个档案用哪个字段来分 析
-2：代表第二个档案用哪个字段来分析
```

paste

```
paste [-d] file1 file2

-d：后接分隔字符，默认为tab键
- ：表示来自standard input的资料
```

expand

```
expand [-t] file

-t：后接数字，表示一个tab键用几个空格替代
```

####分隔命令：split

```
split [-bl] file PREFIX

-b：后接分割成的档案大小，可加单位，b，k，m等
-l：以行数来进行分割
PREFIX：代表前导符
```

####参数替换：xargs

```
xargs [-Oepn] command

-O：当输入的stdin含有特殊字符时使用
-e：EOF（end of file），后接字符串，当xargs解析到这个字符串时，就会停止工作
-p：在执行每个指令的argument时，都会询问使用者
-n：后接次数，每次command指令执行时，要使用几个参数
```

####-的用途

可用来代替stdin或stdout

