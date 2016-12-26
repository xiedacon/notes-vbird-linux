#Linux备份策略

###备份要点

####具有备份意义的数据

* 操作系统本身需要备份的档案

  * /etc/整个目录
  * /home整个目录
  * /var/spool/mail
  * /boot
  * /root
  * /usr/local 或 /opt
  
* 网络服务的数据库方面

  * 软件本身的配置文件，例如：/etc/整个目录，/usr/local/整个目录
  * 软件服务提供的数据
  * Linux主机上的其他服务的数据库档案
  
* 推荐需要备份的目录

  * /boot
  * /etc
  * /home
  * /root
  * /usr/local
  * /var
  
* 不需要备份的目录

  * /dev
  * /proc
  * /mnt与/media
  * /tmp
  
###备份的种类、频率与工具的原则

####完整备份：累积备份

![](/assets/累积备份操作示意图.png)

####完整备份：差异备份

![](/assets/差异备份操作示意图.png)

```
rsync -av 来源目录 目标目录
```

####关键数据备份

















