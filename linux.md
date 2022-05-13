# linux 

## 1 文件系统
linux 文件系统是目录树结构，从根目录开始，根目录下一般有14个子目录。

- **/	根目录**

1. bin	二进制可执行文件（ls, cat, mkdir 等）

2. boot	系统引导文件	

3. dev	设备文件

4. etc	系统配置文件

5. home	用户文件的根目录

6. lib	文件系统中的程序运行所需要的共享库及内核模块

7. mnt	系统管理员安装临时文件系统的安装点

8. opt	额外安装的可选应用程序包

9. proc	虚拟文件系统，存放当前内存的映射

10. root	超级用户目录

11. sbin	二进制可执行文件，只有root才能访问

12. tmp	各种临时文件

13. usr	系统应用程序，/usr/local 存放本地管理员安装的软件

14. var	运行时需要改变数据的文件

**文件类型**
1. -	普通文件
2. d	目录
3. l	符号链接
4. c	字符设备文件
5. b	块设备文件
6. s	套接字
7. p	命名管道

## 2 命令格式

**cmd [options] [arguments]	选项和参数用空格隔开，选项全称前用--，简称用-**

可执行文件分为：
1. 内置命令	构造在 Shell 内部
2. 外置命令	存放在 /bin, /sbin 目录
3. 实用程序	存放在 /usr/bin, /usr/sbin, /usr/share, /usr/local/bin 等目录
4. 用户程序	用户程序经编译生成可执行文件后，可作为 Shell 命令运行
5. Shell 脚本	Shell 语言编写的批处理文件，可作为 Shell 命令运行

通配符如下：

\*	匹配任何字符和任何数目的字符
?	匹配单一数目的任何字符
[ ]	匹配 [ ] 内的任意一个字符
[! ]	匹配除了 [! ] 之外的任意一个字符

**常用命令**

- pwd	查看用户的当前目录
- cd	切换目录
- .	当前目录
- ..	当前目录的父目录
- \-	cd 切换前的目录
- ~	用户主目录的绝对路径名
- ls	显示文件/目录信息
- mkdir	创建目录
- rmdir	删除空目录，目录被删之前必须是空的
- touch	生成一个空文件或更改文件的时间戳
- cp	复制
- mv	移动/重命名
- rm	删除
- ln	建立链接
- find	查找文件
- file/stat	查看文件类型或文件属性信息
- cat	查看文本文件内容
- more	分页查看
- less	分页查看，操作更多
- tail -10	查看文件尾部 10 行
- head -20	查看文件头部 20 行
- echo	输出字符串
- alias	起别名
- |	管道命令
- \>	重定向，采用覆盖模式，而 >> 是追加模式

**打包/压缩命令**
打包是将一堆文件/目录变成一个总文件，压缩则是将大文件通过算法变成小文件。在 linux 中，很多压缩程序只能针对一个文件进行压缩，因此往往需要先打包。

- tar	文件打包工具 .tar
- gzip	流行的 GNU gzip 压缩/解压程序 .gz
- bzip2	免费的数据压缩软件 .bz2
- rar	与 WinRAR 兼容的压缩/解压工具 .rar
- zip/unzip	与 WinZIP 兼容的压缩/解压工具 .zip 

比如 tar -czvf myfile，会将 myfile 打包压缩为 myfile.tar.gz

而 tar -xzvf myfile.tar.gz，会将该文件还原为 myfile 

（-c 压缩	-x 解压	-z 支持 gzip	-v 显示操作信息	-f 指定文件）

**正则 grep 命令**
格式：grep [options] Pattern [files]
Pattern 是查找条件，通常用单引号括起来，files 是需查找的文件，可以是多个。

## 3 Shell 变量/环境

Shell 变量分为：
1. 内部变量	由系统提供，用户只能使用，无法修改，如 ？GROUPS
2. 环境变量	这些变量决定了用户工作的环境，它们不需要用户定义，可以在 Shell 中直接使用，其中某些变量用户可以修改
3. 用户变量	由用户建立和修改，Shell 脚本编写中经常使用，如定义变量 varName=Value export  varName= Value, 引用变量 $varName
Shell 用环境变量确定查找路径，注册目录，终端类型，终端名称，用户名等，所有环境变量都是全局变量，并可以由用户重新设置。

**常见 Shell 环境变量**

1. HOME	用户主目录
2. LOGNAME	登录名
3. USER	用户名，与登录名相同
4. PWD	当前工作目录
5. MAIL	用户的邮箱路径名
6. HOSTNAME	计算机的主机名
7. INPUTRC	默认的键盘映像
8. SHELL	用户所使用的 Shell 的路径名
9. LANG	默认语言
10. HISTSIZE	history 记住命令的最多个数
11. PATH	Shell 查找用户输入命令的路径列表
12. PS1、PS2	Shell 一级、二级命令提示符

显示所有变量和函数	set

显示所有环境变量	env

显示某个变量的值	echo $NAME

取消变量的声明或赋值	unset NAME

## 新学命令备忘
history -c	清除命令历史