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

```
make vmlinux
make modules
make bzImage
make all
make clean
make bzImage
make 
```
















