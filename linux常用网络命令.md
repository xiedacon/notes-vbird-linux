#Linux常用网络命令

###网络参数设定使用的指令

* ifconfig：查询、设定网络卡与IP网域等相关信息
* ifup，ifdown：本身为script，可以更简单的启动网络接口
* route：查询、设定路由表（route table）
* ip：复合式指令，能代替上述功能

####手动/自动设定与启动/关闭IP参数：ifconfig，ifup，ifdown

* ifconfig

```
ifconfig [interface] [up|down]  //观察与启动接口
ifconfig [interface] [options]  //设定与修改接口

interface：网络卡接口代号
options：
  up，down：启动或关闭该网络接口
  mtu：可以设定不同的MTU数值
  netmask：子屏蔽wangluo
  broadcast：广播地址
```

* ifup、ifdown

```
ifup [interface]
ifdown [interface]
```

####路由修改：route

```
route [-nee]
route add [-net|-host] [网络或主机] netmask [mask]
route del [-net|-host] [网络或主机] netmask [mask]

-n：不使用通讯协议或主机名，直接使用IP或port number
-ee：使用更详细的信息来显示
-net：后接路由为一个网域
-host：后接路由为一个主机
netmask：与网域有关，可以设定netmask决定网域的大小
gw：gateway，后接IP
dev：指定由哪一块网络卡联机出去
```

####网络参数综合指令：ip

```
ip [option] [动作] [指令]

option：
  -s：显示出该装置的统计数据
  
ip [-s] link show

show：仅显示出这个装置的相关内容
set：可以设定的项目
  device：界面代号
  动作：
    up|down：启动或关闭某个接口
    address：可以用来修改MAC，如果装置允许
    name：给予装置名字
    mtu：最大传输单元
    
ip address show
ip address [add|del] [IP 参数] [dev 装置名] [相关参数]

show：显示IP信息
add|del：增加或删除相关参数
dev：IP参数所要设定的接口
相关参数：
  broadcast：设定广播地址
  label：装置别名
  scope：
    global：允许所有来源的联机
    site：仅支持IPv6，仅允许本主机的联机
    link：仅允许本装置自我联机
    host：仅允许本主机内部联机
    
ip route show
iproute [add|del] [IP或网域] [via gateway] [dev 装置]

show：单纯显示路由表，也可以使用list
add|del：增加或删除路由
via：由后接gateway出去，不一定需要
dev：由后接装置出去，需要
mtu：最大传输单元
```

####无线网络：iwlist，iwconfig

* iwlist：利用无线网卡进行无线AP的侦测与取得相关的数据
* iwconfig：设定无线网卡的相关参数

####手动使用DHCP自动取得IP参数：dhclient

```
dhclient xxx  //用后接网络卡以dhcp协议获取IP
```

###网络侦错与观察指令

####两主机两点沟通：ping，用ping追踪路径中的最大MTU数值

```
ping [选项与参数] IP

-c 数值：后接执行ping的次数
-n：输出数据时不进行IP与主机名反查，直接使用IP输出
-s 数值：发送出去的ICMP封包大小，默认56bytes
-t 数值：TTL数值，默认255，每经过一个节点少一
-W 数值：等待响应的秒数
-M [do|dont]：主要再侦测网络的MTU数值大小
  do：代表传送一个DF（Dont't Fragment）旗标，让封包不能重新拆包与打包
  dont：代表不传送，封包可以在其他主机上拆包与打包
```

####两主机间各节点分析：traceroute

```
traceroute [选项与参数] IP

-n：使用IP，不需要进行域名解析
-U：使用UDP来进行侦测，默认
-I：使用ICMP来进行侦测
-T：使用TCP来进行侦测
-w：最大未响应的秒数
-p：端口号
-i 装置：使用在比较复杂的环境
-g 路由：与-i相似，后接gateway的IP
```

####查看本机的网络联机与后门：netstat

```
netstat -[rn]       //与路由有关的参数
netstat -[antulpc]  //与网络接口有关的参数

-r：列出路由表
-n：不使用主机名与服务名，使用IP与port number
-a：列出所有的联机状态
-t：仅列出TCP封包的联机
-u：仅列出UDP封包的联机
-l：仅列出在Listen的服务的网络状态
-p：列出PID与程序档名
-c：更新频率
```

####侦测主机名与IP对应：host，nslookup

* host

```
host [-a] hostname [server]

-a：列出该主机详细的各项主机名设定数据
```

* nslookup

```
nslookup [-query=[type]] [hostname|IP]

-query=type：查询的类型
```

###远程联机指令

####终端机与BBS联机：telnet

```
telnet [host|IP [port]]
```

####FTP联机软件：ftp，lftp

* ftp

```
ftp [host|IP] [port]
```

* lftp

```
lftp [-p port] [-u user[, pass]] [host|IP]
```

###文字接口网页浏览

####文字浏览器：links

```
links [options] [URL]

-anonymous [0|1]：是否使用匿名登录的意思
-dump [0|1]：是否将网页的数据直接输出到过standard out而非links软件功能
-dump_charset：后接要透过dump输出到屏幕的编码
```

####文字接口下载器：wget

```
wget [option] [网址]

当联机网站需要提供账号密码时可以利用以下两个参数：
--http-user=username
--http=password=password
--quiet：不显示wget在抓取数据时显示的信息
```

###封包截取功能

####文字接口封包截取器：tcpdump

```
tcpdump [-AennqX] [-i 接口] [-w 储存档名] [-c 次数] [-r 档案] [所欲截取的封包数据格式]

-A：封包的内容以ASCII显示，通常用来抓取WWW的网页资料
-e：使用资料连接层的MAC封包数据来显示
-nn：直接以IP及port number显示，而非主机名与服务名称
-q：仅列出较为简短的封包信息
-X：可以列出16进制以及ASCII的封包内容，对于监听封包内容有用
-i：后接要监听的网络接口
-w：后接档名，将监听的数据储存下来
-r：从后接档案将封包数据读出，由-w制作
-c：监听的封包数
```

####图形接口封包截取器：wireshark

####任意启动TCp/UDP封包的端口联机：nc，netcat

```
nc [-u] [IP|host] [port]
nc -l [IP|host] [port]

-l：开启一个port来监听用户的联机
-u：不使用TCP而是使用UDP作为联机的封包协议
```