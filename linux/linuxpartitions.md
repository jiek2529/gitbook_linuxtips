#linux partitions 分区表说明

reference: http://linuxcommand.org/lts0040.php

1. ## /
The root directory where the file system begins. In most cases the root directory only contains subdirectories.
**`译：root目录是文件系统的开始。所有子目录都包含在root目录中。`**

+ ## /boot
This is where the Linux kernel and boot loader files are kept. The kernel is a file called vmlinuz.
**`译：linux的内核和启动加载文件存放位置，kernel内核是名为vmlinuz的文件。`**

+ ## /etc
The /etc directory contains the configuration files for the system. All of the files in /etc should be text files. Points of interest:
**`译：此目录包含系统配置文件，所有文件都得是文本文件，有意思点：`**

    1. ### /etc/passwd
The passwd file contains the essential information for each user. It is here that users are defined.
**`译：passwd文件包含每个用户的基本信息，用户都注册在这里。`**

    + ### /etc/fstab
The fstab file contains a table of devices that get mounted when your system boots. This file defines your disk drives.
**`译：fstab文件包含在系统引导时安装的设备表，此文件定义你的磁盘驱动器。`**  ::启动时mount -a命令(在/etc/rc 或等效的启动文件中)自动mount的文件系统列表.Linux下，也包括用swapon -a启用的swap区的信息.

    + ### /etc/hosts
This file lists the network host names and IP addresses that are intrinsically known to the system.
**`译：此文件是本地系统知道的网络host名与ip地址映射系统表。`**

    + ### /etc/init.d
This directory contains the scripts that start various system services typically at boot time.
**`译：此目录下包含通常在系统引导时启动各种系统服务的脚本。`**

    + ### /etc/rc   or/etc/rc.d   or/etc/rc*.d  
　　启动、或改变运行级时运行的scripts或scripts的目录. 

    + ### /etc/fdprm  
　　软盘参数表.说明不同的软盘格式.用setfdprm 设置.

    + ### /etc/group  
　　类似/etc/passwd ，但说明的不是用户而是组. 

    + ### /etc/inittab  
　　init 的配置文件. 

    + ### /etc/issue  
　　getty在登录提示符前的输出信息.通常包括系统的一段短说明或欢迎信息.内容由系统管理员确定. 

    + ### /etc/magic  
　　file 的配置文件.包含不同文件格式的说明，file 基于它猜测文件类型.

    + ### /etc/motd  
　　Message Of TheDay，成功登录后自动输出.内容由系统管理员确定.经常用于通告信息，如计划关机时间的警告. 

    + ### /etc/mtab  
　　当前安装的文件系统列表.由scripts初始化，并由mount 命令自动更新.需要一个当前安装的文件系统的列表时使用，例如df命令. 

    + ### /etc/shadow  
　　在安装了影子口令软件的系统上的影子口令文件.影子口令文件将/etc/passwd 文件中的加密口令移动到/etc/shadow中，而后者只对root可读.这使破译口令更困难. 

    + ### /etc/login.defs  
　　login 命令的配置文件. 

    + ### /etc/printcap  
　　类似/etc/termcap ，但针对打印机.语法不同. 

    + ### /etc/profile , /etc/csh.login ,/etc/csh.cshrc  
　　登录或启动时Bourne或Cshells执行的文件.这允许系统管理员为所有用户建立全局缺省环境.
<pre>alias la='ls -la'//添加命令别名到环境；这是当前shell下有效
如想在登陆用户下有都有效，把它添加到 .profile里
如想在机器的所有用户都有效，添加到/etc/profile或/etc/profile.d/下建的文件中</pre>

    + ### /etc/securetty  
　　确认安全终端，即哪个终端允许root登录.一般只列出虚拟控制台，这样就不可能(至少很困难)通过modem或网络闯入系统并得到超级用户特权. 

    + ### /etc/shells  
　　列出可信任的shell.chsh 命令允许用户在本文件指定范围内改变登录shell.提供一台机器FTP服务的服务进程ftpd检查用户shell是否列在 /etc/shells 文件中，如果不是将不允许该用户登录. 

+ ## /bin, /usr/bin
These two directories contain most of the programs for the system. The /bin directory has the essential programs that the system requires to operate, while /usr/bin contains applications for the system's users.
**`译：这两个目录包含大部分的系统程序。/bin 目录有系统需要操作的基本程序，而/usr/bin包含系统用户下的应用程序`**

+ ## /sbin, /usr/sbin
The sbin directories contain programs for system administration, mostly for use by the superuser.
**`译：/sbin目录包含系统管理程序，主要是给超级用户使用的。`**

+ ## /usr
The /usr directory contains a variety of things that support user applications. Some highlights:
**`译：/usr目录包含有用的用户支持应用程序。更多特色`**

    1. ### /usr/share/X11
Support files for the X Window system
**`译：X Window系统支持文件`**

    + ### /usr/share/dict
Dictionaries for the spelling checker. Bet you didn't know that Linux had a spelling checker. See **_look_** and **_ispell_**.
**`译：拼写检查程序的字典，打赌你不知道linux有个拼写检查器。详情查看look和ispell命令。`**

    + ### /usr/share/doc
Various documentation files in a variety of formats.
**`译：各种文档文件各种格式。`**

    + ### /usr/share/man
The man pages are kept here.
**`译：man手册的文档页都放在这里。`**

    + ### /usr/src
Source code files. If you installed the kernel source code package, you will find the entire Linux kernel source code here.
**`译：原码文件。当你安装了内核原码包时，你会发现全部Linux内核原代码码都在这里`**

    + ### /usr/local
/usr/local and its subdirectories are used for the installation of software and other files for use on the local machine. What this really means is that software that is not part of the official distribution (which usually goes in /usr/bin) goes here. When you find interesting programs to install on your system, they should be installed in one of the /usr/local directories. Most often, the directory of choice is /usr/local/bin.
**`译：/usr/local 和它的子目录e和来安装软件和其它文件用于本机器。真实的含义是部分的官方分发的软件都在这里（通常放在/usr/bin）。当你发现有趣的程序安装在你的系统上，它会需要先安装到/usr/local目录里。通常目录选择是/usr/local/bin。`**

+ ## /var
The /var directory contains files that change as the system is running. This includes:
**`译：/var目录包含系统运行时的改变文件。这里包含：`**

    1. ### /var/log
Directory that contains log files. These are updated as the system runs. You should view the files in this directory from time to time, to monitor the health of your system.
**`译：目录里放日志文件，它们会在系统运行时去更新的。你可以时时看到这些文件在这个目录里，去检测你的系统运行的健康。`**

    + ### /var/spool
This directory is used to hold files that are queued for some process, such as mail messages and print jobs. When a user's mail first arrives on the local system (assuming you have local mail), the messages are first stored in /var/spool/mail
**`译：这个目录用来存放些某些进程的队列文件，相邮件消息和打印工作。当一封用户邮件第一时间到达本系统时（假设你有一封本地邮件），消息首选放在/var/spool/mail里。`**

+ ## /lib
The shared libraries (similar to DLLs in that other operating system) are kept here.
**`译：共享的函数库（类似DDL在其它操作系统）放在这里。`**

+ ## /home
/home is where users keep their personal work. In general, this is the only place users are allowed to write files. This keeps things nice and clean :-)
**`译：/home是用户保存自己的工作。这是唯一用户自己允许写的文件，这保持整洁。`**

+ ## /root
This is the superuser's home directory.
**`译：超级用户root的家主目录`**

+ ## /tmp
/tmp is a directory in which programs can write their temporary files.
**`译：/tmp目录里存放话程序可写的临时文件。`**

+ ## /dev
The /dev directory is a special directory, since it does not really contain files in the usual sense. Rather, it contains devices that are available to the system. In Linux (like Unix), devices are treated like files. You can read and write devices as though they were files. For example /dev/fd0 is the first floppy disk drive, /dev/sda (/dev/hda on older systems) is the first IDE hard drive. All the devices that the kernel understands are represented here.
**`译：/dev目录是个特别的目录，它不能包含通常意义上的文件。但，它包含系统可用设备。在linux(类unix)里，设备都视为文件。你能读写它们。例如/dev/fd0是个第一软盘驱动器，/dev/sda(较老系统里是/dev/hda)是第一硬盘驱动器。内核理解的所有设备都在这里。`**

+ ## /proc
The /proc directory is also special. This directory does not contain files. In fact, this directory does not really exist at all. It is entirely virtual. The /proc directory contains little peep holes into the kernel itself. There are a group of numbered entries in this directory that correspond to all the processes running on the system. In addition, there are a number of named entries that permit access to the current configuration of the system. Many of these entries can be viewed. Try viewing /proc/cpuinfo. This entry will tell you what the kernel thinks of your CPU.
**`译：/proc目录也很特别。它里不包含文件。事实上，这个目录关不总是存在。它是完全虚拟的。这里包含小的窥视内核自己的句柄。它们是一组编号条目，组合着系统中所有进程运行。另外，还有许多命名条目允许访问系统的当前配置，可以查看这里的许多条目。尝试查看/proc/cpuinfo。这些条目将告诉你内核对CPU的看法。`**

+ ## /media,/mnt
Finally, we come to /media, a normal directory which is used in a special way. The /media directory is used for mount points. As we learned in the second lesson, the different physical storage devices (like hard disk drives) are attached to the file system tree in various places. This process of attaching a device to the tree is called mounting. For a device to be available, it must first be mounted.
**`译：最后，我们到了/media,一个常规目录在特别的地方使用到。这个目录是安装点。同我们学习第二课，不同的物理存储设备（如硬盘驱动器）在各种位置附接到文件系统树。附接设备到树的过程叫安装挂载。要使设备可用，它必须先挂载。`**

`When your system boots, it reads a list of mounting instructions in the file /etc/fstab, which describes which device is mounted at which mount point in the directory tree. This takes care of the hard drives, but you may also have devices that are considered temporary, such as CD-ROMs and floppy disks. Since these are removable, they do not stay mounted all the time. The /media directory is used by the automatic device mounting mechanisms found in modern desktop oriented Linux distributions. On systems that require manual mounting of removable devices, the /mnt directory provides a convenient place for mounting these temporary devices. You will often see the directories /mnt/floppy and /mnt/cdrom. To see what devices and mount points are used, type mount.`
**`译：系统引导时，它读取文件/etc/fstab中挂载设备指令列表，其中描述了哪些设备安装到目录树的哪个挂载点。这里小心硬件驱动器，但是它也可能被认为是临时设备，如SD-ROM和软盘。由于糨们是可移除的，它们不是一直保持挂载的。/media目录是现代面向桌面系统的Linux发行版中的自动设备挂载机制使用。在需要手动加载可移除设备的系统上，/mnt目录为挂载临时这些设备提供了一个方便的地方。你常见的是/mnt/floppy /mnt/cdrom.查看哪些挂载点被使用了，输入 > mount.`**