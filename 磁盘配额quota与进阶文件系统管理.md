#磁盘配额(Quota)与进阶文件系统管理

###磁盘配额(Quota)

####一般用途

* 限制某一群组所能使用的最大磁盘配额
* 限制某一用户的最大磁盘配额
* 以link的方式，来使邮件可以作为限制的配额

####使用限制

* 仅能针对整个filesystem
* 核心必须支持quota
* quota的记录文件
* 只对一般身份使用者有效

####规范设定项目

* 容量限制或档案数量（inode与block）
* 柔性规定与硬性规定
* 倒数宽限时间

###Quota使用范例

####文件系统支援

* 手动加入；mount -o remount,usrquota,grpquota /home
* 开机加入：修改/etc/fstab

####建立quota记录文件

* quotacheck：扫描文件系统并建立quota的记录文件

```
quotacheck [-avugfM] [/mount_point]

-a：扫描所有在/etc/mtab内，含有quota支持的filesystem
-u：针对用户扫描档案与目录的使用情况，会建立aquota.user
-g：针对群组扫描档案与目录的使用情况，会建立aquota.group
-v：显示扫描过程
-f：强制扫描文件系统，并写入新的quota配置文件中
-M：强制以读写的方式扫描文件系统
```

####quota启动、关闭与限制值设定

* quotaon：启动quota服务

```
quotaon [-avug]
quotaon [-vug] [/mount_point]

-u：针对使用者启动quota（aquota.user）
-g：针对群组启动quota（aquota.group）
-v：显示启动过程
-a：根据/etc/mtab内的filesystem设定启动有关的quota
```

* quotaoff：关闭quota服务

```
quotaoff [-a]
quotaoff [-ug] [/mount_point]

-a：关闭全部
-u：仅针对后接的mount_point关闭user quota
-g：仅针对后接的mount_point关闭group quota
```

* edquota：编辑账号/群组的限制与宽限时间

```
edquota [-u username] [-g groupname]
edquota -t  //修改宽限时间
edquota -p 范本账号 -u 新账号

-u：后接账号名称
-g：后接组名
-t：后接修改宽限时间
-p：复制范本
```

####quota限制值报表

* quota：单一用户的quota报表

```
quota [-uvs] [username]
quota [-gvs] [groupname]

-u：后接username
-g：后接groupname
-v：显示每个用户在filesystem的quota值
-s：使用1024位倍数来指定单位
```

* repquota：针对文件系统的限额做报表

```
requota -a [-vugs]

-a：直接到/etc/mtab搜寻具有quota标志的filesystem，并报告quota结果
-v：输出的数据将含有filesystem相关的详细信息
-u：显示用户的quota限值（默认值）
-g：显示群组的quota限值
-s：使用M，G为单位显示结果
```

####测试与管理

* warnquota：对超过限额者发出警告信

* setquota：直接设定quota配额

```
setquota [-u|-g] 名称 block(soft) block(hard) inode(soft) inode(hard) 文件系统
```

####不改动已有系统的quota

###软件磁盘阵列（software RAID）

####RAID

磁盘阵列可以通过一个技术，将多个小磁盘整合成大磁盘

* RAID-0（等量模式，stripe）：性能最佳

![](/assets/RAID-0的磁盘写入示意图.png)

* RAID-1（镜像模式，mirror）：完整备份

![](/assets/RAID-1的磁盘写入示意图.png)

* RAID 0+1

![](/assets/RAID-0+1的磁盘写入示意图.png)

* RAID 5：性能与数据备份的均衡考虑

![](/assets/RAID-5的·磁盘写入示意图.png)

####软件磁盘阵列

```
mdadm --detail /dev/md0
mdadm --create --auto=yes /dev/md[0-9] --raid-devices=N --level=[015] --spare-devices=N /dev/sdx /dev/hdx..

--create：建立RAID选项
--auto=yes：后接建立软件磁盘阵列的装置
--raid-devices=N：使用多个磁盘作为磁盘阵列装置
--spare-devices=N：使用多个磁盘作为备用装置
--level=[015]：设定这组磁盘阵列的等级
--detail：后接磁盘阵列的详细信息
```

####仿真RAID错误的救援模式

```
mdadm --manage /dev/md[0-9] [--add 装置] [--remove 装置] [--fail 装置]

--add：将后接装置加入md
--remove：将后接装置移出md
--fail：将后接装置设定为fail状态
```

####开机自动启动RAID并自动挂载

/etc/mdadm.conf

####关闭软件RAID

```
1. 先卸除再删除配置文件
umount /dev/md0
/etc/fstab

2. 直接关闭/dev/md0
mdadm --stop /dev/md0
```

###逻辑滚动条管理员（Logical Volume Manager）

####LVM：PV,PE,VG,LV

* Physical Volume,PV,实体滚动条
* Volume Group,VG,滚动条群组
* Physical Extend,PE,实体延伸区块
* Logical Volume,LV,逻辑滚动条

![](/assets/LVM各组件的实现流程图示.png)

* 线性模式（linear）：当一个硬盘使用完后才会使用下一个
* 交错模式（triped）：将一笔数据分成多份写入不同的硬盘

####LVM使用流程

* PV阶段

```
pvcreate：将实体硬盘建立成为PV
pvcreate /dev/hda{6,7,8}

pvscan：查询系统内的PV
pvdisplay：显示处目前系统上的PV状态
pvremove：将PV属性移除
```

* VG阶段

```
vgcreate：建立VG
vgcreate [-s N[mgt]] VG名称 PV名称

-s：后接PE大小，单位可以是m，g，t

vgscan：查询系统内的VG
vgdisplay：显示系统上的VG状态
vgextend：在VG内增加PV
vgreduce：在VG内移除PV
vgchange：设定VG是否启动
vgremove：删除VG
```

* LV阶段

```
lvcreate：建立LV
lvcreate [-s N[mgt]] VG名称 PV名称


lvscan：查询系统内的LV
lvdisplay：显示系统上的LV状态
lvextend：在LV内增加容量
lvreduce：在LV内减少容量
lvremove：删除LV
lvresize：调整LV
```

