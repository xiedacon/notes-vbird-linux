#认识系统服务（daemons）

###daemon与服务

####daemon的主要分类

* stand_alone：此daemon可以自行单独启动服务

* super daemon：一支特殊的daemon来统一管理

![](/assets/super daemon的运作示意图.png)

####服务与端口的对应

/etc/services

####daemon的启动脚本与启动方式

* /etc/init.d/*：启动脚本放置处

* /etc/sysconfig/*：各服务的初始化环境配置文件

* /etc/xinetd.conf,/etc/xinetd.d/*：super daemon配置文件

* /etc/*：各服务各自的配置文件

* /var/lib/*：各服务产生的数据库

* /var/run/*：各服务的程序PID记录处

###系统开启的服务

####chkconfig：管理系统服务默认开机启动与否

```
chkconfig --list [服务名称]
chkconfig [--level [0123456]] [服务名称] [on|off]
chkconfig [--add|--del] [服务名称]

--list：将目前各项服务状态列出来
--level：设定某个服务在该level下启动或关闭
--add：增加一个服务各chkconfig管理，该服务必须在/etc/init.d/内
--del：删除一个交给chkconfig管理的任务
```


















