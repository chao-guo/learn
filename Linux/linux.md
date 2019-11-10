# 系统分区
- 硬件设备文件名

| 硬件 | 设备文件名 |
| :-: | :-: |
| IDE硬件 | /dev/hd[a-d] |
| SCSI/SATA/USB硬盘 | /dev/sd[a-p] |
| 光驱 | /dev/cdrom或/dev/sr0 |
| 软盘 | /dev/fd[0-1] |
| 打印机（25针） | /dev/lp[0-2] |
| 打印机（usb） | /dev/usb/lp[0-15] |
| 鼠标 | /dev/mouse |
---
# 学习流程
1. linux环境下的基本操作命令，包括文件操作命令（rm mkdir chmod chown）编辑工具使用（vi vim）linux用户管理（useradd userdel usermod）等
2. linux的各种配置（环境变量配置，网络配置，服务配置）
3. linux下如何搭建对应语言的开发环境（大数据，javaEE，Python等）
4. 能编写shell脚本，对linux服务器进行维护。
5. 能进行安全设置，防止攻击，保障服务器正常运行，能对系统调优。
6. 深入理解linux系统（对内核有研究），熟练掌握大型网站应用架构组成，并熟练各个环节的部署和维护方法。
---
# 网络设置
- 桥接模式：利用计算机真正的网络，但会占用一个同一网段网络ip，出现ip冲突；
- NET模式：使用VMware Network Adapter VMnet8，本机通信和互联网
- HOST-ONLY模式：使用VMware Network Adapter VMnet1，只能和本机通信
## HOST模式：
`ip address` 查询当前网卡信息
`ip address add ip地址/子网掩码 dev [dev]` 设置ip  192.168.233.2
[设置的ip为临时ip，重启机器丢失，linux修改设置需要在文件中修改]

## 桥接模式： 
本机ip地址：192.168.0.103  设置ip为：192.168.0.104
---
# 基本常识
1. linux严格区分大小写，一般命令没有大写的
2. linux中所有内容以文件形式保存，包括硬件
3. 无扩展名
4. 所有的存储设备都必须挂载之后用户才能使用，包括硬盘，光盘，u盘
5. linux各目录的作用

| 目录名 | 目录作用 |
| :-: | :-: |
| /bin/ | 存放系统命令的目录，普通用户和超级用户都可以执行。不过放在/bin下的命令在单用户模式下也可以执行。 |
| /sbin/ | 保存和系统设置相关的命令，只有超级用户可以使用这些命令进行系统环境设置，但是有些命令可以允许普通用户查看 |
| /usr/bin/ | 存放系统命令的目录，普通用户和超级用户都可以执行。这些命令和系统启动无关，在单用户模式下不能执行 |
| /usr/sbin/ | 存放根文件系统不必要的系统管理命令，例如多数服务程序。只有超级用户可以使用。大家其实可以注意到Linux的系统，在所有“sbin”目录中保存的命令只有超级用户可以使用，“bin”目录保存的命令所有用户都可以使用 |
| /boot/ | 系统启动目录，保存系统启动相关的文件，如内核文件和启动引导程序（grub）文件等 |
| /dev/ | 设备文件保存位置。保存所有硬件设备文件的 |
| /etc/ | 配置文件保存位置。系统内所有采用默认安装方式（npm安装)的服务配置文件全部在这个目录当中，如用户账户和密码，服务的启动脚本，常用服务的配置文件等 |
| /home/ | 普通用户的加目录。建立每个用户是，每个用户要有一个默认登录位置，这个位置就是用户的家目录，所有普通用户的家目录就在/home下建立一个和用户名相同的目录。 |
| /lib/ | 系统调用的函数库保存位置 |
| /lost+found/ | 系统意外崩溃或关机，而产生一些文件碎片放在这里。当系统启动的过程中fsck工具会检查这里，并修复已经损坏的文件系统。这个目录只在每个分区中出现，例如/lost+found/就是根分区的备份恢复目录，/boot/lost+found/就是boot分区的备份恢复目录 |
| /meida/ | 挂载目录。系统建议是用来挂载媒体设备的，如软盘光盘 |
| /mnt/ | 挂载目录。早期Linux中只有这一个挂载目录，并没有细分。现在这个目录系统建议挂载额外设备，如U盘，移动硬盘和其他操作系统的分区 |
| /misc/ | 挂载目录。系统建议用来挂载NFS服务的共享目录。我们在刚刚已经解释了挂载，童鞋们应该知道只要是一个已经建立的空目录就可以作为挂载点。那么系统虽然准备了三个默认挂载目录/media、/mnt、/misc，但是到底在哪个目录中挂载什么设备都可以由管理员自己决定。例如超哥接触Linux的时候，默认挂载目录只有/mnt一个，所以养成了在/mnt下建立不同目录挂载不同设备的习惯。如/mnt/cdrom挂载光盘，/mnt/usb挂载U盘，这都是可以的 |
| /opt/ | 第三方安装的软件保存位置。这个目录就是放置和安装其他软件的位置，我手工安装的源码包软件都可以安装到这个目录当中。不过我还是更加习惯把软件放置到/usr/local/目录当中，也就是说/usr/local/目录也可以用来安装软件 |
| /proc/ | 虚拟文件系统，该目录中的数据并不保存到硬盘当中，而是保存到内存当中。主要保存系统的内核，进程，外部设备状态和网络状态灯。如/proc/cpuinfo是保存CPU信息的，/proc/devices是保存设备驱动的列表的，/proc/filesystems是保存文件系统列表的，/proc/net/是保存网络协议信息的 |
| /sys/ | 虚拟文件系统。和/proc目录相似，都是保存在内存当中的，主要是保存于内核相关信息的 |
| /root/ | 超级用户的家目录。普通用户家目录在“/home”下，超级用于家目录直接在“/”下 |
| /srv/ | 服务数据目录。一些系统服务启动之后，可以在这个目录中保存所需要的数据 |
| /tmp/ | 临时目录。系统存放临时文件的目录，该目录下所有用户都可以访问和写入。我们建议此目录中不能保存重要数据，最好每次开机都把该目录清空 |
| /usr/ | 系统软件资源目录。注意usr不是user的缩写，而是“Unix Softwre Resource”的缩写，所以不是存放用户数据，而是存放系统软件资源的目录。系统中安装的软件大多数保存在这里，所以除了/usr/bin/和/usr/sbin/这两个目录，我在介绍几个/usr/下的二级目录 |
| /var/ | 动态数据保存位置。主要保存缓存、日志以及软件运行所产生的文件 |
6. 服务器不允许关机，只能重启
7. 重启时应该关闭服务
8. 不要在服务器访问高峰运行高负载命令
9. 远程配置防火墙时不要把自己踢出服务器
10. 指定合理的密码规范并定期更新
11. 合理分配权限
12. 定期备份重要数据和日志
---
#常用命令
- 文件处理命令
   - 命令格式与目录处理命令 `ls`
      - 命令格式：命令 [-选项] [参数] 例如：`ls -la /etc`
      说明：
         1. 个别命令不遵循此规则
         2. 当有多个选项时，可以写在一起
         3. 简化选项和完整选项 `-a` 等于 `--all`
      - 原意：list
      命令所在路径：/bin/ls
      执行权限：所有用户
      语法：ls 选项[-ald] [文件或目录]
      -a 显示所有文件，包括隐藏文件
      -l 详细信息显示
      -d 查看目录属性
      -h 人性化显示
      ![](/image/linux_1.png)
      ![](/image/linux_2.png)
      第一列 文件引用计数 所有者 所属组 文件大小 最后修改时间 文件名
         - 第一列：-rw-r--r--（10个字符）
         第一个字符表示文件类型（- 二进制文件  d 目录  l 软链接文件）
         其余部分分为三组分别表示
         rw-        r--        r--
         所有者（u） 所属组（g） 其他人（o）
         r 读 w 写 x 执行
   - 目录处理命令`mkdir`
      - 命令英文原意：make directories
      命令所在路径：/bin/mkdir
      执行权限：所有用户
      语法：mkdir -p [目录名]
      功能描述：创建新目录
      -p 递归创建
      范例：`mkdir -p /tmp/Japan/boduo`
      `mkdir /tmp/Japan/longze /tmp/Japan/cangjing`
   - 目录处理命令`cd`
      - 命令英文原意：change directory
      命令所在路径：shell内置命令
      执行权限：所有用户
      语法：cd [目录]
      功能描述：切换目录
      范例：`cd /tmp/Japan/boduo` 切换到指定目录
      `cd ..` 回到上一级目录
   - 目录处理命令`pwd`
      - 命令英文原意：print working directory
      命令所在路径：/bin/pwd
      执行权限：所有用户
      语法：pwd
      功能描述：显示当前目录
      范例：`pwd`
         /tmp/Japan
   - 文件处理命令`rmdir`
      - 命令英文原意：remove empty directories
      命令所在路径：/bin/rmdir
      执行权限：所有用户
      语法：rmdir [目录名]
      功能描述：删除空目录
      范例：`rmdir /tmp/Japan/boduo`
   - 目录处理命令`cp`
      - 命令英文原意：copy
      命令所在路径：/bin/cp
      执行权限：所有用户
      语法：cp -rp [原文件或目录] [目标目录]
      -r 复制目录
      -p 保留文件属性
      功能描述：复制文件或目录
      范例：
      `cp -r /tmp/Japan/cangjing /root`
      将目录/tmp/Japan/cangjing复制到目录/root下
      `cp -rp /tmp/Japan/boduo /tmp/Japan/longze /root`
      将/tmp/Japan目录下的boduo和longze目录复制到/root下，保持目录属性
   - 目录处理命令`mv`
      - 命令英文原意：move
      命令所在路径：/bin/mv
      执行权限：所有用户
      语法：mv [原文件或目录] [目标目录]
      功能描述：剪切文件、改名
   - 目录处理命令`rm`
      - 命令英文原意：remove
      命令所在路径：/bin/rm
      执行权限：所有用户
      语法：rm -rf [文件或目录]
      -r 删除目录
      -f 强制执行
      功能描述：删除文件
   - 文件处理命令`touch`
      - 命令所在路径：/bin/touch
      执行权限：所有用户
      语法：touch [文件名]
      功能描述：创建空文件
      范例： `touch Japanlovestory.list`
   - 文件处理命令`cat`
      - 命令所在路径：/bin/cat
      执行权限：所有用户
      语法：cat [文件名]
      功能描述：显示文件内容
               -n 显示行号
      范例： `cat /etc/issue`
            `cat -n /etc/services`
   - 文件处理命令`tac`
      - 命令所在路径：/usr/bin/tac
      执行权限：所有用户
      语法：tac [文件名]
      功能描述：显示文件内容（反向列示）
      范例： `tac /etc/issue`
   - 文件处理命令`more`
      - 命令所在路径：/bin/more
      执行权限：所有用户
      语法：more [文件名]
      (空格) 或f 翻页
      (Enter) 换行
      q或Q 退出
      功能描述：分页显示文件内容
      范例： `more /etc/services`
   - 文件处理命令`less`
      - 命令所在路径：/usr/bin/less
      执行权限：所有用户
      语法：less [文件名]
      功能描述：分页显示文件内容（可向上翻页）
      范例： `less /etc/services`
   - 文件处理命令`head`
      - 命令所在路径：/usr/bin/head
      执行权限：所有用户
      语法：head [文件名]
      功能描述：显示文件前面几行
      -n 指定行数
      范例： `head -n 20 /etc/services`
   - 文件处理命令`tail`
      - 命令所在路径：/usr/bin/tail
      执行权限：所有用户
      语法：tail [文件名]
      功能描述：显示文件后面几行
      -n 指定行数
      -f 动态显示文件末尾内容
      范例： `tail -n 18 /etc/services`

   - 文件处理命令`ln`
      - 命令英文原意：link
      命令所在路径：/bin/ln
      执行权限：所有用户
      语法：ln -s [原文件] [目标文件]
      -s 创建软链接
      功能描述：生成链接文件
      范例：
      1. `ln -s /etc/issue /tmp/issue.soft`
      创建文件/etc/issue的软链接/tmp/issue.soft
      软链接特征：类似Windows快捷方式
         1. lrwxrwxrwx l 软链接 软链接文件权限都为rwxrwxrwx
         2. 文件大小-只是符号链接
         3. /tmp/issue.soft -> /etc/issue箭头指向原文件
      2. `ln /etc/issue /tmp/issue.hard`
      创建文件/etc/issue的硬链接/tmp/issue.hard
      硬链接特征：
         1. 拷贝cp -p + 同步更新 echo "this is a test" >> /etc/motd
         2. 可通过i节点识别
         3. 不能跨分区
         4. 不能针对目录使用
   - 权限管理命令`chmod`
      - 命令英文原意：change the permissions mode of a file
      命令所在路径：/bin/chmod
      执行权限：所有用户
      语法：chmod [{ugoa}{+-=}{rwx}] [文件或目录]
                  u-所有者 g-所有组 o-其他 a-所有人all
                  [mode=421 ] [文件或目录]
                  4-r 2-w x-1  eg:rwxrw-r--:764
      -R 递归修改
      功能描述：改变文件或目录权限
      范例：`chmod g+w testfile`
      赋予文件testfile所属组写权限
      `chmod -R 777 testdir`
      修改目录testfile及其目录下文件为所有用户具有全部权限
      - 文件目录权限总结

      | 代表字符 | 权限 | 对文件的含义 | 对目录的含义
      | :-: | :-: | :-: | :-: |
      | r | 读权限 | 可以查看文件内容 | 可以列出目录中内容 |
      | w | 写权限 | 可以修改文件内容 | 可以在目录中创建、删除文件 |
      | x | 执行权限 | 可以执行文件 | 可以写入文件 |
   - 权限管理命令`chown`
      - 命令英文原意：change file ownership
      命令所在路径：/bin/chown
      执行权限：所有用户
      语法：chown [用户] [文件或目录]
      功能描述：改变文件或目录的所有者
      范例：`chown shenchao fengjie`
      改变文件fengjie的所有者为shenchao
   - 权限管理命令`chgrp`
      - 命令英文原意：change file group ownership
      命令所在路径：/bin/chgrp
      执行权限：所有用户
      语法：chgrp [用户组] [文件或目录]
      功能描述：改变文件或目录的所属组
      范例：`chgrp lampbrother fengjie`
      改变文件fengjie的所属组为lampbrother
   - 权限管理命令`umask`
      - 命令英文原意：the user file-creation mask
      命令所在路径：Shell内置命令
      执行权限：所有用户
      语法：umask [-S]
      -S 以rwx形式显示新建文件缺省权限
      功能描述：显示、设置文件的缺省权限
      范例： `umask -S`
   - 文件搜索命令`find`
      - 命令所在路径：/bin/find
      执行权限：所有用户
      语法：find [搜索范围] [匹配条件]
      功能描述：文件搜索
      `find /etc -name init`
      `find /etc -iname init` [不区分大小写] 
      *[匹配所有字符] ?[匹配单个字符]
      在目录/etc中查找文件init
      -iname 不区分大小写
      `find / -size +204800`
      在根目录下查找大于100MB的文件
      +n 大于 -n 小于 n 等于
      `find /home -user shenchao`
      在根目录下查找所有者为shenchao的文件
      -group 根据所属组查找
      `find /etc -cmin -5`
      在/etc下查找5分钟内被修改过属性的文件和目录
      -amin 访问时间 access
      -cmin 文件属性 change
      -mmin 文件内容 modify
      `find /etc -size +163840 -a -size -204800` [数据块]
      在/etc下查找大于80MB小于100MB的文件
      -a 两个条件同时满足
      -o 两个条件满足任意一个即可
      `find /etc -name inittab -exec ls -l {} \;`
      在/etc下查找inittab文件并显示其详细信息
      -exec/-ok 命令 {} \; 对搜索结果执行操作
      -type 根据文件类型查找
      f 文件 d 目录 l 软链接文件
      -inum 根据i节点查找
   - 文件搜索命令`locate`
      - 命令所在路径：/usr/bin/locate
      执行权限：所有用户
      语法：locate 文件名
                  -i 不区分大小写
      功能描述：在文件资料库中查找文件
      范例：`locate inittab`
   - 文件搜索命令`which`
      - 命令所在路径：/usr/bin/which
      执行权限：所有用户
      语法：which 命令
      功能描述：搜索命令所在目录及别名信息
      范例：`which ls`
   - 文件搜索命令`whereis`
      - 命令所在路径：/usr/bin/whereis
      执行权限：所有用户
      语法：whereis [命令名称]
      功能描述：搜索命令所在目录及帮助文档路径
      范例：`whereis ls`
   - 文件搜索命令`grep`
      - 命令所在路径：/bin/grep
      执行权限：所有用户
      语法：grep -iv [指定字串] [文件]
      功能描述：在文件中搜寻字串匹配的行并输出
      -i 不区分大小写
      -v 排除指定字串
      范例：`grep mysql /root/install.log`
   - 帮助命令`man`
      - 命令英文原意：manual
      命令所在路径：/usr/bin/man
      执行权限：所有用户
      语法：man [命令或配置文件]
      功能描述：获得帮助信息
      范例： `man ls`
      查看ls命令的帮助信息
      `man services`
      查看配置文件services的帮助信息
   - 帮助命令`help`
      - 命令所在路径：Shell内置命令
      执行权限：所有用户
      语法：help 命令
      功能描述：获得Shell内置命令的帮助信息
      范例：`help umask`
      查看umask命令的帮助信息
   - 用户管理命令`useradd`
      命令所在路径：/usr/sbin/useradd
      执行权限：root
      语法：useradd 用户名
      功能描述：添加新用户
      范例： `useradd yangmi`
   - 用户管理命令`passwd`
      - 命令所在路径：/usr/bin/passwd
      执行权限：所有用户
      语法：passwd 用户名
      功能描述：设置用户密码
      范例：`passwd yangmi`
   - 用户管理命令`who`
      - 命令所在路径：/usr/bin/who
      执行权限：所有用户
      语法：who
      功能描述：查看登录用户信息
      范例：`who`
   - 用户管理命令`w`
      - 命令所在路径：/usr/bin/w
      执行权限：所有用户
      语法：w
      功能描述：查看登录用户详细信息
      范例： `w`
   - 压缩解压命令`gzip`
      - 命令英文原意：GNU zip
      命令所在路径：/bin/gzip
      执行权限：所有用户
      语法：gzip [文件]
      功能描述：压缩文件
      压缩后文件格式：.gz
   - 压缩解压命令`gunzip`
      - 命令英文原意：GNU unzip
      命令所在路径：/bin/gunzip
      执行权限：所有用户
      语法：gunzip [压缩文件]
      功能描述：解压缩.gz的压缩文件
      范例：`gunzip boduo.gz`
   - 压缩解压命令`tar`
      - 命令所在路径：/bin/tar
      执行权限：所有用户
      语法：tar 选项[-zcf] [压缩后文件名] [目录]
      -c 打包
      -v 显示详细信息
      -f 指定文件名
      -z 打包同时压缩
      功能描述：打包目录
      压缩后文件格式：.tar.gz
      范例：`tar -zcf Japan.tar.gz Japan`  将目录Japan打包并压缩为.tar.gz文件
      - tar命令解压缩语法：
      -x 解包
      -v 显示详细信息
      -f 指定解压文件
      -z 解压缩
      范例：$ tar -zxvf Japan.tar.gz
   - 压缩解压命令`zip`
      - 命令所在路径：/usr/bin/zip
      执行权限：所有用户
      语法：
      zip 选项[-r] [压缩后文件名] [文件或目录]
      -r 压缩目录
      功能描述：压缩文件或目录
      压缩后文件格式：.zip
      范例：`zip buduo.zip boduo`压缩文件
      `zip -r Japan.zip Japan`压缩目录
   - 压缩解压命令`unzip`
      - 命令所在路径：/usr/bin/unzip
      执行权限：所有用户
      语法：unzip [压缩文件]
      功能描述：解压.zip的压缩文件
      范例：`unzip test.zip`
   - 压缩解压命令`bzip2`
      - 命令所在路径：/usr/bin/bzip2
      执行权限：所有用户
      语法： bzip2 选项 [-k] [文件]
      -k 产生压缩文件后保留原文件
      功能描述：压缩文件
      压缩后文件格式：.bz2
      范例：`bzip2 -k boduo`
      `tar -cjf Japan.tar.bz2 Japan`
   - 压缩解压命令`bunzip2`
      - 命令所在路径：/usr/bin/bunzip2
      执行权限：所有用户
      语法： bunzip2 选项 [-k] [压缩文件]
      -k 解压缩后保留原文件
      功能描述：解压缩
      范例：`bunzip2 -k boduo.bz2`
      `tar -xjf Japan.tar.bz2`