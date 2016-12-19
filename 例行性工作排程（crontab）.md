#例行性工作排程（crontab）

###Linux工作排程的种类：at，cron

* at：at是个可以处理仅执行一次就结束排程的指令，执行时，必须要有atd这个服务的支持
* crontab：crontab这个指令所设定的工作会循环执行下去

###仅执行一次的工作排程

####atd的启动与at运作的方式

```
/etc/init.d/atd restart
```

* at的运作方式

1. 先寻找/etc/at.allow，判断使用者是否具有权限
2. 如果/etc/at.allow不存在，就寻找/etc/at.deny
3. 如果两个档案都不存在，则只有root能执行

####单一工作排程

```
at [-mldv] TIME
at -c 工作号码

-m：完成后，使用email通知使用者
-l：相当于atq，列出系统上的所有该用户的at排程
-d：相当于atm，可以取消一个在at排程中的工作
-v：时间格式
-c：列出后接的该项工作的实际指令内容
TIME：时间格式
```

* at的工作管理

```
atq                     //查询系统上有多少at工作排程
atrm [jobnumber]        //移除某个工作排程
```

* batch：系统有空时才进行背景任务

###例行性工作排程

####使用者设定

* /etc/cron.allow
* /etc/cron.deny

```
crontab [-u username] [-l|-e|-r]

-u：只有root才能进行这个任务
-e：编辑crontab的工作内容
-l：查看crontab的工作内容
-r：移除所有crontab的工作内容
```

####系统配置文件：/etc/crontab

###可唤醒停机期间的工作任务

####anacron

####anacron与/etc/anacrontab

```
anacron [-sfn] [job] ...
anacron -u [job] ...

-s：开始一连续的执行各项工作 (job)，会依据时间记录文件的数据判断是否进行
-f：强制
-n：立即执行未进行的任务
-u：仅更新时间记录文件的时间戳，不进行任何操作
job：由/etc/anacrontab定义的各项工作名称
```









