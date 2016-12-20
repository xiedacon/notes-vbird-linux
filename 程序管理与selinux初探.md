#程序管理与SELinux初探

###程序（process）

####process&program

* program：通常为binary program，以实体档案的形态存在
* process：program被触发后，执行者的权限与属性，程序的程序代码与所需数据等都会被加载到内存中，操作系统给予这个内存内的单元一个标识符（PID）