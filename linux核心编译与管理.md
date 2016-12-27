#Linux核心编译与管理

###核心编译的前处理与核心功能选择

####保持干净原始码：make mrproper

```
第一次：
make mrproper

其余时刻：
make clean
```

####挑选核心功能：make XXconfig

* make menuconfig

  最常使用的，是文本模式下可以显示类似图形接口的方式，不需要启动X Window就可以挑选核心功能选单
  
* make oldconfig

  透过使用已存在的./.config档案，将档案内容作为默认值，只将新版本核心内的新功能选项列出供用户选择
  
* make xconfig

  使用Qt作为图形接口显示，需要X Window支持
  
* make gconfig

  使用Gtk作为图形接口显示，需要X Window支持
  
* make config

  最旧式的功能挑选方法，将每个项目都列出来
  
###核心的编译与安装

####编译核心与核心模块

* 基本功能

```
make vmlinux    //未经压缩的核心
make modules    //仅核心模块
make bzImage    //经压缩过的核心（默认）
make all        //进行上述三个动作
```

* 执行顺序

```
make clean      //先清除暂存档
make bzImage    //再编译核心
make modules    //再编译模块
```

####实际安装模块

```
make modules_install
```

####开始安装新核心与多重核心选单（grub）

* 移动核心到/boot且保留旧核心档案

```
cp /usr/src/kernels/linux-xxxx/boot/bzImage /boot/vmlinux-xxxx  //实际核心
cp /usr/src/kernels/linux-xxxx/.config /boot/config-xxxx        //最好将配置文件也复制备份
```

* 建立相对应的Initial Ram Disk

```
mkinitrd -v /boot/initrd-xxxx.img xxxx
```

* 编辑开机选单（grub）

* 以新核心开机、测试、修改

###单一核心模块编译

####单一模块编译

```
vi README           
make clean modules
make install
depmod -a
```







