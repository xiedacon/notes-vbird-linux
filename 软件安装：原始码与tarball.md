#软件安装：原始码与Tarball

###开放源码的软件安装与升级简介

####开放源码、编译程序与可执行文件

![](/assets/利用gcc编译程序进行程序的编译流程示意图.png)

* 开放源码：就是程序代码，写给人看的程序语言，但机器并不认识，所以无法执行
* 编译程序：将程序代码编译成机器看得懂的语言
* 可执行文件：经过编译程序变成二进制程序后的可执行档案

####函式库

![](/assets/程序执行时引用外部动态函式库示意图.png)

类似于子程序的角色，可以被呼叫来执行的一段功能函数

####make与configure

![](/assets/透过configure与make进行编译示意图.png)

####Tarball的软件

* 源代码档案
* 检测程序档案（configure或config）
* 本软件的简易说明与安装说明（INSTALL或README）

####安装与升级软件

* 直接以原始码透过编译来安装与升级
* 直接以编译好的二进制文件来安装与升级

###用make进行宏编译

###Tarbakk的管理与建议

####Tarbakk安装的基本步骤

* 大多数软件安装的基础动作

1. 取得原始码：将tarball档案在/usr/local/src目录下解压
2. 取得步骤流程：进入新建目录下，查阅INSTALL与README
3. 相依属性软件安装
4. 建立makefile：使用configure或config建立makefile
5. 编译：使用make进行编译或其它动作
6. 安装：以make install安装

* 指令下达

1. ./configure
2. make clean
3. make
4. make install

####利用patch更新原始码

###函式库管理

####动态与静态函式库

####ldconfig与/etc/ld.so.conf

```
ldconfig [-f conf] [-C cache]
ldconfig [-p]

-f conf：使用指定的conf作为函式库取得路径，而不以/etc/ld.so.cof为默认值
-C cache：使用cache作为快取暂存的函式库资料，而不以/etc/ld.so.cache为默认值
-p：列出目前所有的函式库资料
```

####程序的动态函式库解析：ldd

```
ldd [-vdr] [filename]

-v：列出所有内容信息
-d：显示资料有遗失的link点
-r：显示ELF有关的错误内容
```

###检验软件的正确性

####md5sum/sha1sum

```
md5sum/sha1sum [-bct] filename
md5sum/sha1sum [--status|--warn] --check filename

-b：使用二进制的读档方式，默认为windows/dos档案形态的读取方式
-c：检验档案指纹
-t：以文字形态来读取档案指纹
```










