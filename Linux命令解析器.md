# Linux命令基础

### 命令解析器

​	shell - Unix操作系统

​	bash - Linux操作系统 （bonn again shell）

本质：根据命令的名字，调用对应的可执行程序。

### Linux快捷键

 * ctrl + P  = 向上

 * ctrl + N  = 向下
 * ctrl + B  = 光标向前移动
 * ctrl + F = 光标向后移动
 * ctrl + A = 光标直接跳到行首
 * ctrl + E = 光标移动到行尾

删除

* ctrl + H = 删除光标前面的字符
* ctrl + D = 删除光标后面的字符（光标后面的字符）
* CTRL + U = 删除光标前面的所有字符

自动提示快捷键

* Tab   自动填充命令/路径

### Linux系统目录结构

![img](https://img-blog.csdn.net/20151001105801791?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)

1. 根目录

   1. /bin    bin是Binary的缩写，存放二进制可执行文件(ls,cat,mkdir等)，常用命令一般都在这里。

   2. /root

   3. /dev     Device的缩写，存放Linux的外部设备，在Linux下一切皆为文文件，访问设备和访问文件一样。

   4. /boot     存放用于系统引导时使用的各种文件，存放linux的核心文件（开机。。）

   5. /etc       存放系统管理的配置文件

   6. /home    存放所有用户文件的根目录，是用户主目录的基点，比如用户user的主目录就是/home/user，可以用~user表示

       ![1555314439232](C:\Users\蓝云甫\AppData\Roaming\Typora\typora-user-images\1555314439232.png)

   7. /lib     存放跟文件系统中的程序运行所需要的共享库及内核模块。共享库又叫动态链接共享库，作用类似windows里的.dll文件，存放了根文件系统程序运行所需的共享文件。

   8. /media    linux系统会自动识别一些设备，例如U盘，光驱，当识别以后，linux会把识别的设备挂载到这个目录之下。

   9. /root      该目录为系统管理员，也成为超级权限用户目录

   10. /sbin     Super Binary    超级管理命令，这里存放的是系统管理员使用的管理程序

   11. /usr      user software resource

       用于存放系统应用程序，比较重要的目录/usr/local 本地系统管理员软件安装目录（安装系统级的应用）。这是最庞大的目录，要用到的应用程序和文件几乎都在这个目录。

       /usr/x11r6 存放x window的目录

       /usr/bin 众多的应用程序  

       /usr/sbin 超级用户的一些管理程序  

       /usr/doc [Linux](http://lib.csdn.net/base/linux)文档  

       /usr/include linux下开发和编译应用程序所需要的头文件  

       /usr/lib 常用的动态链接库和软件包的配置文件  

       /usr/man 帮助文档  

       /usr/src 源代码，linux内核的源代码就放在/usr/src/linux里  

       /usr/local/bin 本地增加的命令  

       /usr/local/lib 本地增加的库 

   ### 用户目录

   1. 绝对路径    从根目录开始写/home/lucas/ss

   2. 相对路径    bb    相对于当前目录而言

      ​		.     当前目录

      ​		..     当前目录的上一级目录

      ​		-      在临近的两个目录之间进行切换  cd -

      ​		![1555315712215](C:\Users\蓝云甫\AppData\Roaming\Typora\typora-user-images\1555315712215.png)

   3. [root@hadoop01 home]

      root:   当前登录用户

      @：    at 在

      hadoop01    主机名

      $  普通用户

      ‘#’    超级用户

      ![1555316212144](C:\Users\蓝云甫\AppData\Roaming\Typora\typora-user-images\1555316212144.png)

      ~： 用户的家目录（宿主目录）



---

### 文件和目录操作

1. 查看我的资产（目录）

   1. tree      --必须手动安装该软件
   2. ls -a      查看所有文件（包括隐藏的文件）

   ![1555317547945](C:\Users\蓝云甫\AppData\Roaming\Typora\typora-user-images\1555317547945.png)

   图中带 . 的开头的文件就是隐藏文件。

   3. ls -l	 列出文件的所有信息（不可以看到隐藏文件）

   ![1555317654942](C:\Users\蓝云甫\AppData\Roaming\Typora\typora-user-images\1555317654942.png)

   ![1_ls -l](C:\Users\蓝云甫\Desktop\材料\语言学习笔记\Linux\课件\第一天\2-其他资料\1_ls -l.png)

   所有者权限： r - read

   ​			w - write

   ​			x - execute

   同组用户权限：r - read

   ​			   - -  没有该权限

   其他人权限

2. 回到主目录的三种方式

   cd /home/lucas

   cd  ~

   cd 

3. 查看当前路径

   pwd

4. 创建目录

   一套小房子   mkdir 目录名

   一套别墅	(嵌套目录)      mkdir  dir1/dir2/dir3 -p

5. 删除目录/文件

   rmdir XXX   			删除空目录（不常用）

   rm     XXX   -r		删除非空目录(递归删除)

   rm  -ri   XXX	        删除前会提示是否删除

   ![1555330596787](C:\Users\蓝云甫\AppData\Roaming\Typora\typora-user-images\1555330596787.png)

6. 创建文件

   touch    XXX				文件名不存在，创建新文件；文件名存在，更新文件时间为当前时间

7. 复制文件

   cp   源文件     目的文件

   ![1555330970602](C:\Users\蓝云甫\AppData\Roaming\Typora\typora-user-images\1555330970602.png)

   目的文件不存在-->新建同名目的文件

   目的文件存在 --> 擦除目的文件原有内容，将源文件内容写入

   复制目录 

   cp   源目录  目的目录   -r       (递归拷贝)

   如果目的目录存在，不会删除目的目录，而是会把源目录放到目的目录里面

8. 查看文件内容（了解，一般会使用vi操作）

   cat  文件名    （将文件内容输出到命令窗口内）

   more  文件名   （先显示一整个屏幕能放下的内容，回车多显示一行，空格翻页，但只能往后翻页） 按q退出

   less    文件名      （能够往前往后翻页ctrl + B/P/N/F）

   head   -n   文件名      (显示文件前n行，如果不加n，默认显示文件前10行)

   tail       -n   文件名

9. 文件重命名/移动文件

   mv     原文件名	新文件名

   如果‘新文件名’是一个已经存在的文件夹的名字，那就执行移动操作，如果是一个不存在的名字，那就执行改名操作。

   ![1555411720926](C:\Users\蓝云甫\AppData\Roaming\Typora\typora-user-images\1555411720926.png)

---

### 文件硬链接/软链接

文件硬链接并没有对文件进行拷贝，并没有占用新的磁盘空间。

ln  hello.c  hello.hard

每创建一个硬链接，文件的文件信息硬链接计数加一。

软链接是一个快捷方式。

可以给目录创建软链接，对于文件，只能创建硬链接。



Linux 系统中有软链接和硬链接两种特殊的“文件”。

软链接可以看作是Windows中的快捷方式，可以让你快速链接到目标档案或目录。

硬链接则透过文件系统的inode来产生新档名，而不是产生新档案。

**创建方法都很简单：**

1. 软链接（符号链接） ln -s   source  target 
2. 硬链接 （实体链接）ln       source  target

硬链接和软链接的区别：https://www.cnblogs.com/crazylqy/p/5821105.html

**建立软链接就是建立了一个新文件**。当访问链接文件时，系统就会发现他是个链接文件，它读取链接文件找到真正要访问的文件。

---

### 其它命令

which   ls    				显示我们使用的（外部）命令在哪一个目录下

无法查找内部命令  比如cd

---

### 查看和修改文件的权限

1. 查看当前登录的用户   			whoami

2. 修改文件权限

   1. 文字设定法：     chmod     who     +|-|= 	   mode     filename

      who:

      ​	文件所有者： u

      ​	文件所属组： g

      ​	其他人：         o

      ​	所有人：         a

      +:   增加权限

      -：删减权限

      =：覆盖

      mode:

      ​	r:   读

      ​	w:   写

      ​	x:  执行

      样例： ![1555471981425](C:\Users\蓝云甫\AppData\Roaming\Typora\typora-user-images\1555471981425.png)表示给temp文件/其他人/添加/写权限

      ![1555472088387](C:\Users\蓝云甫\AppData\Roaming\Typora\typora-user-images\1555472088387.png)

      2. 数字设定法：

         -： 没有权限

         r:    对应数字4

         w:   对应数字2

         x:   对应数字1

         所以： 3 = w+x   5 = r+x   7=r+w+x   6=r+w

         765

         7 --rwx ---文件所有者

         6 --rw   ---同组者

         5 --rw   ---其他人

         ![1555472474273](C:\Users\蓝云甫\AppData\Roaming\Typora\typora-user-images\1555472474273.png)

         权限覆盖   chmod 777 temp

         权限删减   chmod  -001 temp        对其它用户删减他的执行权限x

         权限增加   chmod + 001 temp

         ![1555472735701](C:\Users\蓝云甫\AppData\Roaming\Typora\typora-user-images\1555472735701.png)

      ---

      ### 修改文件所属用户/所属组

      sudo chown  新的所有者：新的所属组  文件名                   //sudo使用管理员权限

      sudo  chgrp   新的所属组      文件名		



---

### 文件的查找和检索

1. 按文件属性查找：

   1. 文件名：find  查找目录   -name   “文件名称“

   ![1555473908258](C:\Users\蓝云甫\AppData\Roaming\Typora\typora-user-images\1555473908258.png)

   ​	如果文件具体名称不太清楚，可以使用通配符，*代表所有字符，?代表一个字符

   ​	搜索的文件名尽量用引号引起来。

   2. 文件大小：find 查找目录  -size  +/-容量大小

      1. ![1555474201330](C:\Users\蓝云甫\AppData\Roaming\Typora\typora-user-images\1555474201330.png)

      如果想要查找文件容量处于某一个范围的文件，可以使用两遍-size

      ![1555474307399](C:\Users\蓝云甫\AppData\Roaming\Typora\typora-user-images\1555474307399.png)

   3. 文件类型： find  查找目录  -type  /d/t/f/b/l/p

   ![1555474563861](C:\Users\蓝云甫\AppData\Roaming\Typora\typora-user-images\1555474563861.png)

2. 按文件内容查找

   ​	grep -r  "查找的内容"  查找的路径



### Linux软件安装

#### Ubuntu系统

在线安装
​	apt-get
​		安装：sudo apt-get install tree -- 在线下载安装
​		移除：sudo apt-get remove tree
​		更新：sudo apt-get update -- 更新软件列表
​		清理所有软件安装包: sudo apt-get clean
​			实际清理的是: /var/cache/apt/archives 目录下的 .deb 文件
​	aptitude
​		安装：sudo aptitude install tree
​		重新安装：sudo aptitude reinstall tree
​		更新：sudo apt-get update
​		移除：sudo aptitude remove tree
​		显示状态：sudo aptitude show tree

#### CentOS系统

在线安装

yum:

​	 yum install         //全部安装
​	 yum install package1       //安装指定的包package1
​	 yum remove package1        //卸载指定的包package1
​	 yum update         //全部更新
​	 yum update package1         //更新指定的包package1

