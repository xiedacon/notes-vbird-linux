#Linux账号管理与ACL权限设定

###Linux的账号与群组

####使用者账号

* /etc/passwd档案结构

1. 账号名称
2. 密码（早期放在这，后来被移动到/etc/shadow中）
3. UID（0：系统管理员，1-499：系统账号，500-65535：可登入账号）
4. 
5. GID
6. 用户信息说明栏
7. 家目录
8. shell

* /etc/shadow档案结构

1. 账号名称
2. 密码（加密后）
3. 最近修改密码日期
4. 密码不可被修改的天数
5. 密码需要重新变更的天数
6. 密码需要变更期限前的警告天数
7. 密码过期后的账号宽限事件
8. 账号失效日期
9. 保留

####有效与初始群组

* /etc/group档案结构

1. 组名
2. 群组密码（群组管理员使用，已经移动到/etc/gshadow中）
3. GID
4. 群组支持的账号名称

* groups：观察有效与支持群组

```
groups
```

* newgrp：有效群组的切换

```
newgrp 组名
```

* /etc/gshadow档案结构

1. 组名
2. 密码（!开头表示无合法密码，无群组管理员）
3. 群组管理员账号
4. 群组支持的账号名称

###账号管理

####新增与移除使用者

* useradd

```
useradd [-u UID] [-g 初始群组] [-G 次要群组] [-mM] [-c 说明档] [-d 家目录绝对路径] [-s shell] 使用者账号名

-u：后接UID
-g：后接组名
-G：后接组名
-M：强制不建立用户家目录（系统账号默认值）
-m：强制建立用户家目录（一般账号默认值）
-c：后接说明
-d：指定某个目录成为家目录，而不使用默认值
-r：建立一个系统账号
```

* useradd参考档：/etc/default/useradd

|设定|意义|
|--|--|
|GROUP=100|新建账号的初始群组GID为100|
|HOME=/home|用户家目录的基准目录|
|INACTIVE=-1|密码过期后是否会失效|
|EXPIRE=|账号失效日期|
|SHELL=/bin/bash|默认使用的shell程序文件名|
|SKEL=/etc/skel|用户家目录参考基准目录|
|CREATE_MAIL_SPOOL=yes|建立使用者的mailbox|

* passwd

```
passwd [--stdin]  //所有人都可以用来修改自己的密码
passwd [-l] [-u] [--stdin] [-S] [-n 天数] [-x 天数] [-w 天数] [-i 日期] 账号  //root专用

--stdin：可以通过管线来作为密码输入
-l：lock，会将/etc/shadow第二栏加上!使密码失效
-u：unlock
-S：列出密码相关参数
-n：后接天数，shadow的第4字段，不可修改密码天数
-x：后接天数，shadow的第5字段，必须改动密码天数
-w：后接天数，shadow的第6字段，密码过去前警告天数
-i：后接日期，shadow的第7字段，密码失效日期
```

* chage

```
chage [-ldEImMW] 账号名

-l：列出该账号的详细密码参数
-d：后接日期，shadow第3字段，最近一次修改密码日期
-E：后接日期，shadow第8字段，账号失效日期
-I：后接天数，shadow第7字段，密码失效日期
-m：后接天数，shadow第4字段，密码最短保留天数
-M：后接天数，shadow第5字段，密码多久需要进行修改
-W：后接天数，shadow第6字段，密码过期前警告日期
```

* usermod

```
usermod [-cdegGlsuLU] username

-c：后接账号说明
-d：后接账号家目录
-e：后接日期
-f：后接天数
-g：后接初始群组
-G：后接次要群组
-a：于-G合用，增加次要群组支持
-l：后接账号名称，即修改账号名称
-s：后接shell档案
-u：后接UID
-L：将用户密码冻结，使其无法登入
-U：解冻用户
```

* userdel

```
userdel [-r] username

-r：连同用户的家目录也一起删除
```

####用户功能

* finger

```
finger [-s] username

-s：仅列出用户的账号、全名、终端机代号与登入时间等等
-m：列出与后接的掌柜你好相同者
```

* chfn

```
chfn [-foph] [账号名]

-f：后接完成名称
-o：办公室房间号？
-p：办公室电话号码？？
-h：家庭电话号码？？？
```

* chsh

```
chsh [-ls]

-l：列出目前系统上可用的shell，即/etc/shells的内容
-s：修改shell
```

* id

```
id [username]
```

####新增与移除群组

* groupadd

```
groupadd [-g gid] [-r] 组名

-g：后接GID
-r：建立系统群组
```

* groupmod

```
groupmod [-g gid] [-n group_name] 群组名

-g：修改已有的GID
-n：修改已有的组名
```

* groupdel

```
groupdel [groupname]
```

* gpasswd：群组管理员功能

```
gpasswd groupname
gpasswd [-A user1,..] [-M user2,..] groupname
gpasswd [-rR] groupname

无参数：代表给予groupname一个密码
-A：后接用户名，即群组管理员
-M：后接用户名，即加入的群组成员
-r：将groupname的密码移除
-R：使groupname的密码失效

群组管理员可执行动作：
gpasswd [-ad] user groupname

-a：将使用者加入群组
-d：将使用者移除群组
```

###主机细部权限规划：ACL的使用

####ACL（Access Control List）

* 使用者：可针对使用者来设定权限
* 群组：可针对群组来设定权限
* 默认属性：可针对在该目录下建立档案/目录使，规范新数据的默认权限

####ACL的设定

* setfacl：设定某个档案/目录的ACL范围

```
setfacl [-bkRd] [{-m|-x} acl参数] 目标文件名

-m：设定后续的acl参数给档案使用
-x：删除后续的acl参数
-b：移除所有的acl参数
-k：移除预设的acl参数
-R：递归
-d：设定预设acl参数
```

* getfacl

```
getfacl filename

选项与setfacli相同
```

###使用者身份切换

####su

```
su [-lm] [-c 指令] [username]

-：单纯使用-代表使用login-shell的变量档案读取方式来登入系统
-l：后接欲切换的使用者账号，也是login-shell的方式
-m：代表使用目前的环境设定，而不读取新使用者的配置文件
-c：仅进行一次指令
```

####sudo

```
sudo [-b] [-u 新使用者账号]

-b：将后续指令放到背景中去执行
-u：后接欲切换的使用者，默认root
```

###用户的特殊shell与PAM模块

####特殊的shell，/sbin/nologin

####PAM模块

![](/assets/PAM模块与其它程序的相关性.png)

####PAM模块设定语法

1. 用户开始执行/usr/bin/passwd这个程序，并输入密码
2. passwd呼叫PAM模块进行验证
3. PAM模块会到/etc/pam.d/寻找与程序同名的配置文件
4. 依据/etc/pam.d/passwd内的设定，引用相关的PAM模块逐步进行验证分析
5. 将验证结果回传给passwd程序
6. passwd程序回根据PAM回传的结果决定下一个动作

###Linux主机上的用户信息传递

####查询使用者：w,who,last,lastlog

####使用者对话：write,mesg,wall

```
writer 使用者账号 [用户所在终端接口]
mesg n  //拒绝接受任何信息
wall 信息  //全员广播
```













