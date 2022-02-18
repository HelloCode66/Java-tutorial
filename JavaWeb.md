# **JavaWeb**

## Linux

### 初识Linux

**操作系统**：管理==计算机硬件==与==软件资源==的计算机程序，同时也是计算机系统的内核与基石。

**主流操作系统**

- 桌面操作系统：Window系列、macOS、Linux
- 服务器操作系统：Linux、Windows Server
- 嵌入式操作系统：Linux
- 移动设备操作系统：Unix（Linux、ios）

**Linux发展历程**

- 1984年Minix（只用于教学）
- 1991年编写驱动程序，年底公开Linux内核源码
- 1994年Linux1.0（Linus Torvalds）
- 至此开始流行起来

**Linux特点**

- Linux是一套==免费==使用和自由传播的类Unix操作系统

- 是一个基于POSIX和Unix的多用户、多任务、支持多线程和多CPU的操作系统
- 它能运行主要的Unix工具软件、应用程序和网络协议。它支持32位和64位硬件
- 继承了Unix以网络为核心的设计思想，是一个性能稳定的多用户网络操作系统
- 两个基本思想
  - 一切都是文件
  - 每个软件都有确定的用途
- 完全兼容POSIX1.0标准
- 多用户、多任务
- 良好的界面
- 支持多种平台

**Linux与其它操作系统的区别**

- 开源情况
- 硬件适用
- 本质不同
- 系统界面
- 驱动程序
- 系统使用
- 软件与支持

> Windows更适用于家庭个人使用
>
> Linux更适用于企业服务器使用

**Linux发行商和常见发行版**

- Redhat公司--------Red Hat Linux（最著名的Linux版本、收费）-----免费的CentOS
- CentOS特点：主流、免费、更新方便

### Linux的安装和使用

先安装虚拟机，再安装Centos

#### Vmware

**Vmware简介**

- 不需要分区或者重开机就能在同一台PC上使用两种以上的操作系统
- 完全隔离并且保护不同操作系统的环境以及所有的软件、资料
- 不同的操作系统之间还可以进行互动操作
- 有复原功能
- 能够设置并且随时修改操作系统的操作环境
- 常见虚拟机软件：VMware workstation、VirtualBox

**Vmware下载**：https://www.vmware.com/cn.html

**CentOS镜像下载**：https://www.centos.org/download/
==高速下载地址==

- http://mirrors.aliyun.com
- http://mirrors.sohu.com
- http://mirrors.163.com
- http://mirrors.cqu.edu.cn/CentOS

#### SecureCRT

简介：SecureCRT是一款支持SSH（SSH1和SSH2）的终端仿真程序，简单地说是Windows下登录Unix或Linux服务器主机的软件。

#### 目录和文件

- Linux没有盘符这个概念，只有一个根目录/，所有文件都在他下面
- etc表示系统中的配置文件
- usr、usr/bin、usr/sbin都表示系统预设执行文件的放置目录
- var/log表示程序运行日志的存放目录
- 切换根目录：`cd /`
- 查看目录内容：`ls -l`

#### 时间同步

![](E:\Typora\学习笔记\images\时间同步.png)

#### 克隆与快照

**克隆**：将原系统完完全全的拷贝一份，原系统丢失后克隆的系统还能正常使用

- 占用空间大
- 原系统不存在，克隆体还能用

**快照**：记录系统当前状态，并不会把系统完整拷贝

- 占用空间小
- 原系统不存在，快照也就无法使用

> 克隆和拍摄快照时都需要关闭虚拟机

### 系统与设置命令

#### 账号管理

> 与用户相关的命令，必须在管理员权限下才能执行
>
> 命令：`su root`

- 创建用户：`useradd (选项) 用户名`
- 用户口令：`passwd (选项) 用户名`
  - 密码不能是一个回文
  - 长度必须大于8位
  - 必须是字母和数字的结合

> 在root权限下切换其它用户可直接切换，无需输入密码

- 修改用户：`usermod 选项 用户名`

![](E:\Typora\学习笔记\images\修改用户.png)

- 删除用户：`userdel (选项) 用户名`

![](E:\Typora\学习笔记\images\用户删除.png)

#### 用户组

将用户分成小组，方便对用户的管理

- 创建用户组：`groupadd (选项) 用户组名`

- 修改用户组：`groupmod (选项) 用户组名`
  ![](E:\Typora\学习笔记\images\修改用户组.png)

- 查询用户所属组：`groups 用户名`

- 删除用户组：`groupdel 用户组名`

- 管理用户组内成员：`gpasswd (可选项) 组名`

  > gpasswd是Linux下的管理工具，用于将一个用户添加到组或者从组中删除

  - -a：添加用户到组
  - -d：从组中删除用户
  - -A：指定管理员
  - -M：指定组员和-A的用途差不多
  - -r：删除密码
  - -R：限制用户登入组，只有组中的成员才可以用newgrp加入该组

![](E:\Typora\学习笔记\images\用户添加到组.png)

#### 系统管理相关命令

- 日期管理：`date [参数选项]`

  参数选项：

  - `-d "字符串"`：显示字符串所指的日期与时间。字符串前后必须加上双引号
  - `-s "字符串"`：根据字符串来设置日期与时间。字符串前后必须加上双引号
  - `-u`：显示GMT（北京时间为CST）
  - `--help`：在线帮助
  - `--version`：显示版本信息

- 显示登陆账号的信息：`logname`

- 切换用户：`su 用户名`

- 查看当前用户详细信息（用户id、群组id、所属组）：`id 用户名`

- 提高普通用户的操作权限：`sudo [参数选项]`

#### 进程相关命令

- 实时显示process的动态：`top`

  > pid:每个进程的id
  >
  > user：进程是属于哪个用户
  >
  > PR：进程的优先级
  >
  > NI：进程优先级（负数为高优先级，正数为低优先级）
  >
  > VIRT：当前进程占用虚拟内存的总量
  >
  > S：当前进程的状态

  - 实时显示所有进程信息（显示完整命令）:`top -c`
  - 实时显示指定进程的信息：`top -p PID`
  - 结束实时监控：`q`

- 查看当前正在运行的进程信息：`ps`
  - 显示系统中所有的进程信息：`ps -A`
  - 显示系统中所有的进程信息（完整信息）：`ps -ef`
  - 显示指定用户的进程信息：`ps -u 用户名`
  
- 中断执行中的程序：`kill PID`
  - 例如：`kill 1111`表示杀死PID为1111的进程
  - `kill -9 PID`：强制杀死指定PID的进程
  - `killall -u 用户名`：杀死这个用户中的所有进程
  - `kill -9 $(ps -ef|grep 用户名)`：杀死指定用户的所有进程
  - `kill -l`：查看对应编号
  
- 关机命令：`shutdown`（延迟关机）

  - `shutdown -h now`：立即关机
  - `shutdown +1 "1分钟以后关机"`：延迟一分钟以后关机，并给出警告信息
  - `shutdown -r +1 "准备重启了"`：延迟一分钟以后重启，并给出警告信息
  - `shutdown -c`：取消关机命令

- 重启命令：`reboot`（立即重启）

- 显示当前登录系统的用户：`who`

  - `who -H`：显示明细（标题）信息

- 校正服务器时间、时区：`timedatectl`

  - 几个小概念

    | 项目                          | 说明                                                         |
    | ----------------------------- | ------------------------------------------------------------ |
    | 时区                          | 因时区不同显示的时间不同，牵扯到夏令时和调整等问题，date命令可查看 |
    | 系统时钟：System Clock        | Linux OS的时间，date命令可查看                               |
    | 硬件时钟：RTC:Real Time Clock | 主板上由电池供电的BIOS时间，hwclock -r可查看                 |
    | NTP:Network Time Protocol     | 本机时间和实际的时间之间的经常会有差别，一般使用NTP服务器进行时间校准 |

  - `timedatectl status`：显示系统的当前时间和日期
  - `timedatectl list-timezones`：查看所有可用的时区
  - `timedatectl set-timezone "Asia/Shanghai"`：设置本地时区
  - `timedatectl set-ntp false`：禁用时间同步
  - `timedatectl set-time "2022-02-22 20:20:00"`：设置时间
  - `timedatectl set-ntp true`：启用时间同步

- 清除屏幕：`clear`

#### 目录管理

| 常见命令 | 作用                                       |
| -------- | ------------------------------------------ |
| ls       | 列出目录                                   |
| cd       | 切换目录                                   |
| pwd      | 显示目前的目录                             |
| mkdir    | 创建新目录                                 |
| rmdir    | 删除空目录                                 |
| cp       | 复制文件或目录                             |
| rm       | 删除文件或目录                             |
| mv       | 移动文件或目录<br />修改文件或者目录的名字 |

- ls命令相当于在Windows系统中打开文件夹，看到的目录以及文件的明细。

  - 语法：`ls [参数选项] 目录名称`
  - `-a`：显示所有文件或目录（包含隐藏）
  - `-d`：仅列出目录本身，而不是列出目录内的文件数据（常用）
  - `-l`：长数据串列出，包含文件的属性与权限等等数据（常用）

  > `ls`：显示不隐藏的文件与文件夹
  > `ls -l`：显示不隐藏的文件与文件夹的详细信息
  > `ls -al`：显示所有文件与文件夹的详细信息

- `pwd -P`：查看当前所在目录
- `cd [相对路径或绝对路径]`：切换目录
  
  - `cd ..`：返回上一级目录

- `mkdir`
  - `mkdir 文件夹的名字`：创建单级目录
  - 创建多级文件夹，使用`mkdir -p aaa/bbb`

- `rmdir`

  - `rmdir 文件夹名字`：删除空目录
  - `rmdir -p aaa/bbb`：删除多级目录（先删bbb，如果删完aaa也为空，则aaa也一起删除）

- `rm`

  - `rm 文件路径`：删除文件

  - `rm -r 目录路径`：删除目录和目录里面所有的内容（单级目录或多级目录都行）

- `touch 文件名.后缀名`：创建一个文件

- `cp`

  - `cp 数据源 目的地`：文件复制（仅文件）
  - `cp -r aaa/* ccc`：将aaa目录中的所有文件及目录拷贝到ccc中（`*`代指所有）

- `mv`

  - `mv 数据源 目的地`：改名(数据源和目的地相同)、移动文件或文件夹
  - `mv 文件名 文件名`：将源文件名改为目标文件名
  - `mv 目录名 目录名`：目标目录已存在，将源目录移动到目标目录；目标目录不存在则改名

#### 文件基本属性

- 文件权限（共10位）

  - 第一位为==d==表示是一个文件夹；是==-==表示是一个文件；==|==表示是一个链接文档（快捷方式）
  - ==r==表示可读；==w==表示可写；==x==表示可执行；==-==表示没有当前权限
  - 2-4位表示属主权限（文件所属的用户可以做的事情）
  - 5-7位表示属组权限（文件所在用户组可以对它做的事）
  - 8-10位表示其它用户权限

- `chgrp`命令（change group）

  - `chgrp [选项参数] [所属群组] [文件或目录...]`：更改所属组
  - `chgrp root aaa`：将aaa文件夹所属组更改为root
  - `chgrp -v root aaa`：将aaa的属组改为root（==-v==会多一句提示语）

- `chown`命令

  - `chown 属主名 文件名`：更改属主
  - `chown [参数选项] 属主名:属组名 文件名`：更改属主和属组
  - ==-R==：处理指定目录以及其子目录下的所有文件

- `chmod`命令

  - 作用：修改属主、属组、其他用户的权限
  - 数字方式语法：`chmod [参数选项] 数字权限 文件或目录`
  - 符号方式语法：`chmod u=rwx,g=rx,o=r a.txt`
  - ==-R==：对目前目录下的所有档案与子目录进行相同的权限变更（即以递回的方式逐个变更）
  
  修改方式：
  
  - 数字方式
  
    - ==r==-----==4==
    - ==w==----==2==
    - ==x==----==1==
    - ==-==----==0==
  
    > 设置时会把三个数字加在一起设置
    > 例如：rwx则为7
  
  - 符号方式
  
    - ==user==属主权限----==u==
    - ==group==属组权限----==g==
    - ==others==其它权限----==o==
    - ==all==全部身份----==a==
  
    - ==+==（加入）、==-==（除去）、=====（设定）
    - ==r==（可读）、==w==（可写）、==x==（可执行）

#### 综合案例

> 需求：一个公司的开发团队有三个用户：Java、erlang、golang
> 有一个文件目录tmp/work供他们开发，如何实现让这三个用户都对其具有写权限

**思路**

- 创建三个用户，并把他们加入到对应的用户组（dev-group）
- 将tmp/work文件夹所属组更改为dev-group
- 修改文件夹所属组的权限

![](E:\Typora\学习笔记\images\权限案例.png)

### 文件管理

#### touch

- 语法：`touch [参数选项] 文件名`

  > 如果文件不存在就创建文件，如果存在就修改时间属性

- `touch a{1..10}.txt`：创建a1.txt一直到a10.txt共10个文件（批量创建空文件）
- `stat a.txt`：查看文件的详细信息

#### vi/vim编辑器

- vi编辑器：只能是编辑文本内容，不能对字体、段落进行排版
  - 不支持鼠标操作
  - 没有菜单
  - 只有命令
- vim编辑器：vim是从vi发展出来的一个文本编辑器。
  - 代码补全、编译及错误跳转等方便编程的功能特别丰富，在程序员中被广泛使用

> 简单来说：
> 	vi是老式的文字处理器，不过功能已经很齐全了，但是还是有可以改进的地方
> 	vim则可以说是程序员开发者的一项很好用的工具

- vi/vim三种模式

  - 阅读模式（命令模式）
  - 编辑模式（编辑模式）
  - 保存模式（末行模式）

  > 命令模式下只能读不能写
  > 在命令模式下输入`i`可以进入编辑模式，在编辑完成之后按下`Esc`又可以退出到命令模式
  > 在命令模式下输入`:`可以进入末行模式，在保存完之后还可以按下两次`Esc`继续回退到命令模式

- 打开和新建文件
  - 语法：`vim 文件名`
  - 如果文件已经存在，会直接打开文件（命令模式）
  - 如果文件不存在，打开一个临时文件，在保存且退出后，就会新建一个文件
- 进入编辑模式

| 命令 | 英文   | 功能                   | 常用   |
| ---- | ------ | ---------------------- | ------ |
| i    | insert | 在当前字符前插入文本   | 常用   |
| I    | insert | 在行首插入文本         | 较常用 |
| a    | append | 在当前字符后添加文本   |        |
| A    | append | 在行末添加文本         | 较常用 |
| o    |        | 在当前行后面插入一空行 | 常用   |
| O    |        | 在当前行前面插入一空行 | 常用   |

- 进入末行模式保存文件

  - `:q`：当vim进入文件没有对文件内容做任何操作可以按“q”退出
  - `:q!`：当vim进入文件对文件内容有操作但不想保存退出
  - `:wq`：正常保存退出
  - `:wq!`：强行保存退出，只针对于root用户或文件所有人

- vim定位行

  - 语法：`vim 文件名 +行数`：查看文件并定位到具体行数
  - `vim a.txt +5`：查看a.txt文件并定位到第5行

- 异常处理

  - 如果vim异常退出，在磁盘上可能会保存有==交换文件==

  > 在修改一个文件时(a.txt)，为保证文件安全，vim不会对源文件进行修改，会产生一个新的文件(a.txt.swp)，并对该文件进行编辑
  > 只有在保存的时候，才会将新文件写回到源文件中
  - 如果有交换文件，在下次使用vim编辑文件时，系统会提示是否对交换文件继续操作（将交换文件删除即可）

#### 文件查看

| 命令               | 功能                       |
| ------------------ | -------------------------- |
| cat 文件名         | 查看小文件内容             |
| less -N 文件名     | 分屏显示大文件内容         |
| head -n 文件名     | 查看文件的前一部分         |
| tail -n 文件名     | 查看文件的最后部分         |
| grep 关键字 文件名 | 根据关键字搜索文本文件内容 |

- `cat -n a.txt`：可以加入参数选项`-n`显示行号
  - 只能阅读小文件
  - 阅读大文件可能显示不完整
- `less 文件名`：查看大文件
  - 加入`-N`可显示行号
  - ctrl + F ：向前移动一屏
  - ctrl + B ：向后移动一屏
  - ctrl + D ：向前移动半屏
  - ctrl + U ：向后移动半屏
  - j ：向前移动一行
  - k ：向后移动一行
  - G：移动到最后一行
  - g：移动到第一行
  - q/ZZ：退出less命令
- `tail 文件名`：默认查看文件最后10行内容
  - `tail -3 b.txt`：查看文件最后3行内容
  - `tail -f b.txt`：动态显示文件最后10行内容（==ctrl + C停止==）
  - `tail -n +2 b.txt`：显示文件b.txt的内容，从第2行至文件末尾
  - `tail -c 45 b.txt`：显示文件最后45个字符
- `head 文件名`：查看文件前10行内容
  - 其它内容和tail类似
- `grep命令`
  - 类似于Windows下打开文件后ctrl+F的查找功能
  - 查找对应的进程
  - 语法：`grep [参数选项] 关键字 文件`：根据关键字，搜索文本文件内容
  - ==-n==：把包含关键字的行号展示出来
  - ==-i==：把包含关键字的行展示出来，搜索时忽略大小写
  - ==-v==：把不包含关键字的行展示出来
  - `ps -ef | grep sshd`：将进程中含有sshd的进程展示出来
  - `ps -ef | grep -c sshd`：将进程中含有sshd的进程的个数展示出来

#### echo命令

- `echo 字符串`：展示文本
- `echo 字符串 > 文件名`：将字符串写到文件中（覆盖文件内容）
- `echo 字符串 >> 文件名`：将字符串写到文件中（不覆盖原内容）
- `cat 不存在的目录 &>> 存在的文件`：将命令的失败结果追加到指定的文件的后面

#### awk命令

- AWK是一种处理文本文件的语言，是一个强大的文本分析工具（名字取自三位创始人名字中的字母）
- 语法：`awk [参数选项] '语法' 文件`
- 过滤：`cat a.txt | awk '/zhang|li/'`：查看a.txt文件中包含zhang或者li的行
- 切割

| 选项         | 含义                     |
| ------------ | ------------------------ |
| `-F ','`     | 使用指定字符分割         |
| `$ + 数字`   | 获取第几段内容           |
| `$0`         | 获取当前行内容           |
| `OFS="字符"` | 向外输出时的段分割字符串 |
| `toupper()`  | 字符转成大写             |
| `tolower()`  | 字符转成小写             |
| `length()`   | 返回字符长度             |

> `cat a.txt | awk -F ' ' '{print $1,$2,$3}'`：将a.txt中的内容按空格分割并打印第1-3列
> `cat a.txt | awk -F ' ' '{print toupper($1),$2,$3}'`：将a.txt中的内容分隔后并将$1中的内容转为大写字符后输出
> `cat a.txt | awk -F '' '{OFS="---"}{print $1,$2,$3}'`：将a.txt中的内容分隔后并用---重新分隔后输出

- 计算

| 命令                                                         | 含义                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| awk<br />BEGIN{初始化操作}<br />{每行都执行}<br />END{结束时操作}<br />文件名 | 固定语法<br />BEGIN{这里面放的是执行前的语句}<br />{这里面放的是处理每一行要执行的语句}<br />END{这里面放的是处理完所有的行后要执行的语句}<br />文件名 |

> `cat a.txt | awk -F' ' 'BEGIN{}{totle=totle+$2}END{print totle}'`：将a.txt分割后把$2的值相加并输出
> `cat a.txt | awk -F' ' 'BEGIN{}{totle=totle+$2}END{print totle}'`：输出totle以及总人数（行数）

#### 软连接

- 类似于Windows里面的快捷方式
- 语法：`ln -s 目标文件路径 快捷方式路径`
- `ln -s aaa/bbb/ccc/ddd/eee/a.txt a.txt`

### 压缩命令

#### 查找命令

- 语法：`find [参数选项] <指定目录> <指定条件> <指定内容>`：在指定目录下查找文件

- 参数选项

  - ==-name filename==：查找名为filename的文件
  - ==-ctime -n或+n==：按时间来查找文件，-n指n天以内，+n指n天以前

- `find . -name "*.txt"`：查找当前目录下所有以txt为后缀的文件

- `find . -ctime -1`：当前文件夹下1天内操作过的文件

  > 将==.==替换为==/==则表示在全盘范围进行查找

#### gzip命令

- 语法：`gzip [参数选项] [文件]`：压缩文件
- `gzip a.txt`：将a.txt文件压缩
- `gzip *`：将当前目录下所有文件都进行压缩（已经压缩过的不能再次被压缩）
- `gzip -dv 文件名`：解压文件并显示详细信息

#### gunzip命令

- 语法：`gunzip [参数] [文件]`：解压文件
- `gunzip 压缩文件`：解压压缩文件
- `gunzip *`：解压当前目录下的所有压缩文件

#### tar命令

- 语法：`tar [必要参数] [选择参数] [文件]`：打包、压缩和解压（文件/文件夹）
- ==注意==：tar本身不具有压缩功能，它是调用压缩功能实现的
- 参数选项
  - ==-c==：建立新的压缩文件
  - ==-v==：显示指令执行过程
  - ==-f <备份文件>==：指定压缩文件
  - ==-z==：通过gzip指令处理压缩文件
  - ==-t==：列出压缩文件中的内容
  - ==-x==：表示解压
- `tar -cvf 打包文件名 文件名`：打包文件并指定打包之后的文件名（仅打包不压缩）
- `tar -zcvf b.gz b.txt`：通过gzip指令将b.txt压缩为b.gz并显示过程（打包压缩）
- `tar -zcvf aaa.gz aaa`：将aaa文件夹压缩为aaa.gz
- `tar -ztvf aaa.gz`：查看压缩文件中的内容
- `tar -zxvf aaa.gz`：解压aaa.gz文件

#### zip命令

- 语法：`zip [必要参数] [选择参数] [文件]`：压缩
- ==注意==：zip是个使用广泛的压缩程序，文件经他压缩后会另外产生具有"==.zip=="扩展名的压缩文件
- 参数选项
  - ==-q==：不显示指令执行过程
  - ==-r==：递归处理，将指定目录下的所有文件和子目录一并处理
- `zip -q -r 压缩文件名 文件/文件夹`：压缩对应的文件/文件夹

#### unzip命令

- 语法：`unzip [必要参数] [选择参数] [文件]`：解压
- ==注意==：只能解压"==.zip=="扩展名的压缩文件
- 参数选项
  - ==-l==：显示压缩文件内所包含的文件
  - ==-d <目录>==：指定文件解压缩后要存储的目录
- `unzip -l aaa.zip`：查看aaa.zip压缩文件所包含的文件
- `unzip -d aaa aaa.zip`：将aaa.zip压缩文件解压到aaa文件夹中（aaa文件夹可以不存在，会自动创建）

#### bzip2命令

- 语法：`bzip2 [参数选项] 文件`：压缩文件
- ==注意==：使用新的压缩算法，和zip相比压缩后的==文件比原来的要小==，但==花费时间变长==
- 若没有加上任何参数，bizp2压缩完文件后会产生bz2的压缩文件，并删除原始文件
- `bzip2 a.txt`：压缩并删除a.txt
- **bunzip2命令**：`bunzip2 [参数选项] 文件`：解压
  - ==-v==：解压文件时，显示详细的信息
  - `bunzip2 -v a.bz2`：解压并显示详细信息

### 网络与磁盘管理

#### 网络管理

- **ifconfig命令**
  - 语法：`ifconfig [参数选项]`：显示或配置网络设备的命令
  - `ifconfig ens37 down`：关闭ens37这张网卡
  - `ifconfig ens37 up`：开启网卡ens37
  - `ifconfig ens37 192.168.23.199`：将ens37网卡的ip更改为192.168.23.199
  - `ifconfig ens37 192.168.23.199 netmask 255.255.255.0`：配置ip地址和子网掩码
- **ping命令**
  - 语法：`ping [参数选项]`：检测是否与主机联通
  - ==-c <完成次数>==：设置完成要求回应的次数
  - `ping -c 2 www.baidu.com`：指定接收包的次数
- **netstat命令**
  - 语法：`netstat [参数选项]`：显示网络状态
  - ==-a==：显示所有连线中的Socket
  - ==-i==：显示网卡列表

#### 磁盘管理

- **lsblk命令**

  - 语法：`lsblk [参数选项]`：列出硬盘的使用情况
  - 理解为：list block的英文缩写
  - `lsblk -f`：显示系统信息

- **df命令**

  - 语法：`df [参数选项]`：显示目前在Linux系统上，磁盘的使用情况
  - ==--total==：显示所有的信息
  - ==-h==：换算成KB，MB，GB等形式进行展示（方便阅读）
  - `df`：显示整个硬盘的使用情况
  - `df 文件夹`：显示文件夹使用情况
  - `df --total`：显示所有的信息
  - `df -h`：将结果变成kb、mb、gb等形式展示，利于阅读

- **mount命令**

  - 语法：`mount [参数选项] 目录`：用于==挂载==Linux系统外的设备
  - 类似与Windows中的U盘，但在Linux中需要手动新建一个文件夹，并把该文件夹和U盘关联起来（挂载点和挂载）

  > 注意：“挂载点”的目录需要以下几个要求：
  >    目录事先存在，可以用mkdir命令新建目录
  >    挂载点目录不可被其它进程使用到
  >    挂载点下原有文件将被隐藏

  - `mount -t auto /dev/cdrom PPP`：将光驱和PPP文件夹挂载
  - `umount PPP`：卸载PPP文件夹所挂载的光驱

#### yum

- 在Linux中，如果我们需要查找、安装、下载或者卸载另外的软件，就需要通过yum来进行操作。英文全称为：Yellow dog Updater,Modified
- **yum常用命令**
  - 列出所有可更新的软件清单命令：`yum check -update`
  - 更新所有软件命令：`yum update`
  - 仅安装指定的软件命令：`yum install <package_name>`
  - 仅更新指定的软件命令：`yum update <package_name>`
  - 列出所有可安装的软件清单命令：`yum list`
  - 删除软件包命令：`yum remove <package_name>`
  - 查找软件包命令：`yum search <keyword>`
  - 清除缓存命令：
    - `yum clean packages`：清除缓存目录下的软件包
    - `yum clean headers`：清除缓存目录下的headers
    - `yum clean oldheaders`：清除缓存目录下旧的headers
    - `yum clean,yum clean all(= yum clean packages;yum clean oldheades)`：清除缓存目录下的软件包及旧的headers
- ==-y==：在安装过程中，如果有选择提示，全部选择==y==
- ==注意==：使用yum必须联网且在root权限下
- `yum -y install tree`：安装tree
- `tree`：执行tree，展示当前目录结构
- `yum remove tree`：移除tree
- `yum list tom*`：查找以tom为开头的软件名称
- **yum源**
  - 在下载软件的时候，都是从yum源中获取的，默认是centos中默认的yum源（在国外，下载速度慢）
  - ==更换国内yum源==
    - `yum -y install wget`：安装一个下载工具
    - `cd /etc/yum.repos.d/`：进入yum的相关文件夹中
    - `mv CentOS-Base.repo CentOS-Base.repo.back`：对原yum文件改名（备份）
    - `wget -O CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo`：下载阿里yum源文件
    - `yum clean all`：清理缓存，并重新加载yum
    - `yum makecache`：为新yum源建立缓存文件
    - `yum search tomcat`：查找软件，验证阿里云的yum源是否可以正常使用

#### rpm

- 在最初，RedHat Linux发行版专门用来管理Linux各种套件的程序
- 和yum的区别
  - rpm只能安装已经下载到本地机器上的rpm包
  - yum能在线下载并安装rpm包，能更新系统，且还能自动处理包与包之间的依赖问题，这个是rpm工具所不具备的

### shell

#### 初识shell

> 在计算机科学中，shell就是一个==命令解释器==
> shell是位于操作系统和应用程序之间，是他们二者最主要的接口。
> shell负责把应用程序的输入命令信息解释给操作系统，将操作系统指令处理后的结果解释给应用程序

**一句话，shell就是在操作系统和应用程序之间的一个命令翻译工具。**



**Windows和Linux中的shell**

- Windows系统：cmd.exe		命令提示字符
- Linux系统：sh / csh / ksh / ==bash==(默认) / ...

**shell的使用方式**

- 手工方式

> 手工敲击键盘，直接输入命令，按Enter后。
> 执行命令，显示命令执行的结果
> ==重点==：逐行输入命令，逐行进行确认执行

- 脚本方式

> 我们把手工执行的命令，写到一个文件中，然后运行这个文件，达到执行命令的效果。
> 这个文件就叫做==脚本文件==

**编写第一个shell脚本**

- 新建一个文件后缀名为sh

- 编写内容

  ```shell
  #! /bin/bash
  #这是临时shell脚本
  echo 'nihao'
  echo 'hello'
  ```

- 执行

#### 注释和变量

**注释**

- 单行注释

```shell
#!/bin/bash
# 这是单行注释
echo 'hello world'
```

- 多行注释

```shell
#!/bin/bash
:<<! 这是多行注释
多行注释
多行注释
!
echo 'hello world'
```

```shell
:<<字符
	注释内容
字符
```

**变量**

- 定义变量

  - 普通变量

    - 方式一：`变量名=变量值`（变量值必须是一个整体，中间没有特殊字符）
    - 方式二：`变量名='变量值'`（单引号中的内容，原样赋值）
    - 方式三：`变量名="变量值"`（如果双引号中有其它变量，会把变量的结果进行拼接，然后赋值）

    > 习惯：数字不加引号，其它默认加双引号

  - 命令变量（将命令的结果赋值给变量）

    - 方式一：==变量名=\`命令\`==(这里是反引号<tab键上方>)
    - 方式二：`变量名=$(命令)`（常用）

- 使用变量

  - 方式一：`$变量名`（非标准写法，图省事）
  - 方式二：`"$变量名"`（非标准写法，图省事）
  - 方式三：`${变量名}`（在双引号里面要使用变量的值）
  - 方式四：`"${变量名}"`（标准使用方式）

- 只读变量：`readonly 变量名`

- 删除变量：`unset 变量名`

#### 数组

| 定义数组         | 数组名=(值1 值2 ... 值n)          | arr=(1 2 3 4 5)             |
| ---------------- | --------------------------------- | --------------------------- |
| 给数组的元素赋值 | 数组名[索引]=值                   | arr[0]=1                    |
| 获取元素         | \${数组名[下标]}                  |${arr[0]}|
| 获取长度         | \${#数组名[\*]}<br />\${#数组名[@]} |${#arr[*]}<br />\${#arr[@]}|

#### 运算符

| 运算符  |    说明     |             举例              |
| :-----: | :---------: | :---------------------------: |
|    +    |    加法     |         expr $a + \$b         |
|    -    |    减法     |         expr \$a - $b         |
|    *    |    乘法     |        expr \$a \\* $b        |
|    /    |    除法     |         expr \$b / $a         |
|    %    |    取余     |         expr \$b % $a         |
|    =    |    赋值     | a=$b （把b变量的值赋给a变量） |
| ++ / -- | 自增 / 自减 |            ((a++))            |

**注意点**

1. 原生的bash不支持简单的数学运算。可以通过其它命令实现：expr
2. 表达式和运算符之间要有空格
3. 完整的表达式要被反引号包含
4. 乘法中不能直接使用*，需要在乘号前加\\转义

举例：==\`expr 2 + 2`==



**字符串运算符**

| 运算符 | 说明                                     | 举例          |
| ------ | ---------------------------------------- | ------------- |
| =      | 检测两个字符串是否相等，相等返回true     | [ \$a = \$b ] |
| !=     | 检测两个字符串是否不相等，不相等返回true | [ \$a != \$b ] |
| -z     | 检测字符串长度是否为0，为0返回true       | [ -z \$a ]    |
| -n     | 检测字符串长度是否不为0，不为0返回true   | [ -n \$a ]    |
| \$     |检测字符串是否为空，不为空返回true|[ \$a ]|

> `[]`与里面的代码命令有个空格隔开，不能贴在一起
>
> `$?`可以获取上一条语句的执行结果
>
> ==在shell中，0为真，1为假==
>
> `${#字符串}`获取字符串长度



**关系运算符**

| 运算符 |                             说明                             |      举例       |
| :----: | :----------------------------------------------------------: | :-------------: |
|  -eq   |          检测两个数是否相等，相等返回true==equals==          | [ \$a -eq \$b ] |
|  -ne   |      检测两个数是否不相等，不相等返回true==not equals==      | [ \$a -ne \$b ] |
|  -gt   | 检测左边的数是否大于右边的，如果是，则返回true==greater than== | [ \$a -gt \$b ] |
|  -lt   |  检测左边的数是否小于右边的，如果是，返回true==less than==   | [ \$a -lt \$b ] |
|  -ge   | 检测左边的数是否大于等于右边的，如果是，则返回true==greater equals== | [ \$a -ge \$b ] |
|  -le   | 检测左边的数是否小于等于右边的，如果是，则返回true==less equals== | [ \$a -le \$b]  |

==关系运算符只支持数字，不支持字符串，除非字符串的值是数字==



**布尔运算符**

| 运算符 |                     说明                     |             举例              |
| :----: | :------------------------------------------: | :---------------------------: |
|   !    |                   取反运算                   |     [ ! false ] 返回true      |
|   -o   | 或运算，有一个表达式为true 则返回true ==or== | [ \$a -lt 20 -o \$b -gt 100 ] |
|   -a   | 与运算，两个表达式都为true 才返回true==and== | [ \$a -lt 20 -a \$b -gt 100 ] |



**逻辑运算符**

| 运算符 | 说明       | 举例                             |
| ------ | ---------- | -------------------------------- |
| &&     | 逻辑的 AND | [[ true && true ]] 返回true      |
| \|\|   | 逻辑的 OR  | [[ false \|\| false ]] 返回false |



#### 选择语句

**if语法**

```shell
if[ 条件 ]
then
	语句体
fi
```

```shell
if [ 条件 ]
then
	语句体
else
	语句体
fi
```

```shell
if [ 条件1 ]
then
	语句体
elif [ 条件2 ]
	语句体
else
	语句体
fi
```

**小练习**

```shell
#!/bin/bash
# if语句

#if的第一种格式：
#查找一个进程，如果进程存在，就打印true
if [ $(ps -ef | grep -c "ssh") -gt 1 ]
then
	echo "true"
fi
```

**case语法**

```shell
case 值 in
模式1 )
	语句体1
	;;
模式2 )
	语句体2
	;;
esac
```

```shell
v="hhxx"
case "${v}" in
"hhxx")
	echo "好好学习"
	;;
"ttxs")
	echo "天天向上"
	;;
esac
```

#### 循环语句

**for循环**

```shell
for 变量 in 范围
do
	循环体
done
```

```shell
for loop in A B C
do
	echo $loop
done
```

**while循环**

```shell
while 条件
do
	循环体
done
```

```shell
a=1
while [ "${a}" -le 10 ]
do
	echo "${a}"
	((a++))
done
```

#### 函数

**无参无返回值**

```shell
函数名(){
	函数体
}
```

```shell
test(){
	echo "函数测试！"
}
echo "==========="
test
echo "============"
```

**有参无返回值**

```shell
method(){
	echo "第一个参数$1"
	echo "第二个参数$2"
}

method a b
```

**有参有返回值**

```shell
method(){
	echo "接收到参数$1和$2"
	return $(($1 + $2))
}

method 10 20
echo $?
```

**小练习**

> `read 变量名`：表示把键盘录入的数据赋值给这个变量

```shell
#!/bin/bash
#在方法中键盘录入两个整数，并返回这两个整数和

method(){
        echo "请录入第一个数："
        read num1
        echo "请录入第二个数："
        read num2
        echo "两个数分别为：${num1},${num2}"
        return $(($num1 + $num2))
}

method
echo "两数之和为：$?"
```

## Nginx

#### 概述

- Nginx是一款服务器软件
- 其核心功能是可以和服务器硬件相结合，从而可以将程序发布到Nginx服务器上，让更多用户浏览

#### 安装

1. 上传压缩包：`put nginx压缩包位置`（CRT中按alt+p键进入sftp）

2. 解压压缩包：`tar -zxvf 压缩包名`

3. 进入解压目录：`cd nginx解压目录`

4. 安装依赖环境

   `yum -y install pcre pcre-devel`

   `yum -y install zlib zlib-devel`

   `yum -y install openssl openssl-devel`
   `yum -y install gcc`

5. 安装nginx
   `./configure`
   `make`
   `make install`(安装完会在/usr/local/下有一个nginx目录)
6. 进入对应目录：`cd /usr/local/nginx/sbin`
7. 启动nginx服务：`./nginx`
   停止：`./nginx -s stop`
   重启：`./nginx -s reload`
8. 查看nginx服务状态：`ps -ef | grep nginx`
9. 测试nginx服务：浏览器打开对应Linux服务器ip地址

> 最后这里在浏览器打开对应ip地址无法访问，解决方法：
> 第一步，对80端口进行防火墙配置：`firewall-cmd --zone=public --add-port=80/tcp --permanent`
> 第二步，重启防火墙服务：`systemctl restart firewalld.service`
> 然后重新在浏览器中访问你的ip，应该就可以访问了。

#### 发布项目

1. 在==/home==下创建一个web目录：`mkdir web`
2. 将项目上传到该目录下：`put web项目压缩包`
3. 解压项目压缩包：`unzip web程序压缩包`
4. 编辑nginx配置文件：`vim /home/nginx-1.18.0/conf/nginx.conf`
   找到server的大括号范围，修改location的路径
   ![](E:\Typora\学习笔记\images\nginx发布项目.png)
5. 进入对应目录：`cd /usr/local/nginx/sbin`
6. 关闭nginx服务：`./nginx -s stop`
7. 启动nginx服务并加载配置文件：`/usr/local/nginx/sbin/nginx -c/home/nginx-1.18.0/conf/nginx.conf`
8. 通过浏览器测试网站

## JavaWeb核心

### 企业开发简介

#### JavaEE规范

- ==JavaEE(Java Enterprise Edition)：Java企业版==
- 它是由SUN公司领导、各个厂家共同制定并得到广泛认可的工业标准。
- JavaEE早期叫做J2EE，但是没有继续采用其命名规则。J2EE的版本从1.0开始到1.4结束。而JavaEE版本是从JavaEE 5 版本开始，目前最新的版本是JavaEE 8。
- JavaEE规范是很多Java开发技术的总称。这些技术规范都是沿用自J2EE的。一共包括了13个技术规范。
- 包括：JDBC, JNDI, EJB, RMI, IDL/CORBA, JSP, Servlet, XML, JMS, JTA, JTS, JavaMail, JAF。

#### WEB概述

**概述**

- WEB在计算机领域中代表的是==网络==。
- 像我们之前所用的WWW，它是World Wide Web 三个单词的缩写，称为：==万维网==
- 网络相关技术的出现是为了让我们在网络的世界中==获取资源==，这些资源的存放之处，我们把它叫做==网站==。
- 我们通过输入网站的地址（网址），就可以访问网站中提供的资源（不区分局域网或广域网）



**资源分类**

- 静态资源
  网站中提供给人们展示的资源是一成不变的，也就是说不同人或者在不同时间，看到的内容都是一样的。
  作为开发者来说，我们编写的HTML, CSS, JavaScript 都属于静态资源。
- 动态资源
  网站中提供给人们展示的资源是由程序产生的，在不同的时间或者不同的人由于身份的不同，所看到的内容是不一样的。
  作为网站开发者来说，我们编写的JSP、Servlet等都属于动态资源。

#### 系统结构

> 在之前的学习中，开发的都是Java工程。这些工程在企业中称之为项目或者产品。都是有系统架构的！

- 基础结构划分
  CS结构：（Client Server）==客户端+服务器==的方式（把不同的应用直接安装在客户端上）
  BS结构：（Browser Server）==浏览器+服务器==的方式
- 技术选型划分
  Model1模型
  Model2模型
  MVC模型
  三层架构 + MVC模型
- 部署方式划分
  一体化结构
  垂直拆分结构
  分布式结构
  微服务结构

### tomcat

#### 服务器

- 服务器是计算机的一种，它比普通计算机运行更快、负载更高、价格更贵。==服务器在网络中为其它客户机（如PC机、智能设备等）提供计算或者应用服务。==服务器具有高速的CPU运算能力、长时间的可靠运行、强大的I/O外部数据吞吐能力以及更好的扩展性。

- 而我们这里所说的服务器，其实是web服务器，或者应用服务器。它本质就是一个软件，通过和硬件相结合，从而达到帮助我们来发布应用的功能，让用户通过客户机访问我们的应用。

- 常用的应用服务器

  | 服务器名称  | 说明                                                |
  | ----------- | --------------------------------------------------- |
  | weblogic    | 实现了JavaEE规范，重量级服务器，又称为JavaEE容器    |
  | websphereAS | 实现了JavaEE规范，重量级服务器                      |
  | JBOSSAS     | 实现了JavaEE规范，重量级服务器，免费的              |
  | Tomcat      | 实现了jsp/servlet规范，是一个轻量级服务器，开源免费 |

#### Tomcat

- Tomcat是Apache软件基金会的Jakarta项目组中的一个核心项目，由Apache、Sun和其它一些公司及个人共同开发而成。由于有了Sun公司的参与和支持，最新的Servlet、JSP规范总能在Tomcat中得到体现。因为Tomcat技术先进、性能稳定，而且免费，所以深受Java爱好者的喜爱并得到了部分软件开发商的认可，成为目前比较流行的Web应用服务器。
- Tomcat官网：https://tomcat.apache.org/
- Tomcat各个版本所需要的支持
  ![](E:\Typora\学习笔记\images\tomcat各个版本所需要的支持.png)

**下载和安装**

- 下载：官网下载
- 安装：直接解压即可
- 目录组成
  - ==bin==：一些二进制可执行文件
  - ==conf==：保存配置文件的路径
  - lib：Tomcat在运行过程中所需要的jar包
  - logs：日志文件
  - temp：临时文件
  - ==webapps==：项目发布目录（一个文件夹代表一个web应用）（ROOT代表根项目）
  - work：工作目录

#### 基本使用

1. 启动
   `startup.bat`：Windows下启动执行文件
   `startup.sh`：Linux下启动执行文件

   > 启动后浏览器访问:http://localhost:8080可以进入欢迎界面（Tomcat默认端口为8080）

2. 停止
   `shutdown.bat`：Windows下关闭执行文件
   `shutdown.sh`：Linux下关闭执行文件
3. 部署项目
   在webapps目录下创建一个文件夹
   将资源放到该文件夹中
   启动tomcat，输入正确路径

**常见问题**

1. 启动问题
   启动窗口一闪而过：没有配置jdk环境变量
   ![](E:\Typora\学习笔记\images\tomcat一闪而过.png)

   java.net.BindException：端口8080被占用

2. 控制台乱码问题解决
   conf-logging.properties
   修改`java.util.logging.ConsoleHandler.encoding = UTF-8`

   > Tomcat默认UTF-8，CMD命令窗口默认GBK，将UTF-8改为GBK即可解决乱码问题

**IDEA集成Tomcat**

1. 点击Run -》 Edit Configurations
2. 点击Defaults -》 Tomcat Servlet -》 Local
3. 点击Configure -》Tomcat Home -》 选择tomcat所在路径

**Linux下的安装**

1. 上传压缩包到/home路径：`put d:/apache-tomcat-9.0.58.tar.gz`
2. 解压压缩包：`tar -zxvf 压缩包名`
3. 进入bin目录下：`cd apache-tomcat-9.0.58/bin`
4. 启动tomcat服务：`./startup.sh`
5. 使用浏览器测试：浏览器打开对应Linux服务器ip地址:8080

#### Java WEB项目

1. 新建项目模型，选择Java Enterprise
   确定JDK版本、Appalication Server版本
2. 右键Add Framework Support...
3. 勾选Web Appalication选项

**项目组成详解**

- src：存放Java源代码
- web：存放项目相关资源（html、css、js、jsp、图片等）
- WEB-INFO：存放相关配置的（web.xml等）

**IDEA发布项目**

1. 点击Run -》 Edit Configurations
2. 点击Tomcat Server -》 Deployment
   Application Context是项目访问路径，/代表默认路径，多个项目中只能有一个默认路径
3. 点击Tomcat Server -》 Server 
   设置关联浏览器
   两个Update resources设置
   设置JDK、端口号
4. 启动Tomcat服务
5. 验证结果（浏览器）

**通过war包发布项目**

1. 在项目的web路径下打war包：`jar -cvf myweb.war .`
2. 将打好的war包剪切到tomcat的webapps路径下
3. 启动tomcat服务，自动解压war包
4. 验证结果

#### 配置文件

**配置默认端口号**

- 主配置文件==server.xml==
  `<Connector>`标签中，port属性代表Tomcat默认端口号(8080)
  ![image-20220212123024799](E:\Typora\学习笔记\images\tomcat端口号.png)

  > http协议默认端口号为80，Tomcat默认端口号与其不一致，所以每次访问网站需要加上端口号
  > 如果是80端口，就不需要加端口号
  > 真正发布网站的时候，都需要将tomcat默认端口号改为80，这样在访问网站的时候就不需要加端口号了

**配置虚拟目录**

- 作用：可以发布任意目录下的项目

1. 编辑==server.xml== 配置文件，找到`<Host>`标签

2. 加入以下内容
   `<Context path="/mytest" docBase="e:/test" />`
   ![image-20220212124231399](E:\Typora\学习笔记\images\tomcat虚拟目录.png)

   > `path`：访问资源的虚拟目录名称（表示在浏览器地址栏中的访问路径）
   > `docBase`表示需要发布的项目的真实路径

**配置虚拟主机**

- 作用：可以指定访问路径的名称

1. 编辑==server.xml== 配置文件，找到`<Engine>`标签
2. 加入以下内容
   ![image-20220212125002395](E:\Typora\学习笔记\images\tomcat配置虚拟主机.png)

> `name`：虚拟主机名称
> `appBase`：项目所保存的根路径
> `unpackWARs`：是否自动解压war包
> `autoDeploy`：是否自动发布
> `Context`：同虚拟目录

3. 修改hosts文件
   绑定IP地址和对应的域名
   文件路径：`c:\Windows\System32\drivers\etc`
   ![image-20220212125816008](E:\Typora\学习笔记\images\tomcat绑定域名.png)

### HTTP协议

#### 概述

- HTTP(Hyper Text Transfer Protocol)：==超文本传输协议==
- HTTP协议是基于 TCP/IP 协议的（安全）
- 超文本：比普通文本更加强大（还有图片、音频等等）
- 传输协议：客户端和服务端的通信规则（握手规则）

**组成部分**

- 请求：客户端发起请求到服务器
- 响应：服务器收到客户端的请求后发起响应给客户端

> 除了手动发起的请求外，JavaScript、CSS、图片等资源会自动发起请求

#### 协议的请求

**请求的组成部分**

1. 请求行：请求方式 提交路径(提交参数) HTTP/版本号

2. 请求头

   | 名称              | 说明                                                   |
   | ----------------- | ------------------------------------------------------ |
   | Accept            | 客户端浏览器所支持的MIME类型                           |
   | Accept-Encoding   | 客户端浏览器所支持的压缩编码格式。最常用的就是gzip压缩 |
   | Accept-Language   | 客户端浏览器所支持的语言。一般都是zh_CN或en_US等       |
   | Referer           | 告知服务器，当前请求的来源                             |
   | Content-Type      | 请求正文所支持的MIME类型                               |
   | Content-Length    | 请求正文的长度                                         |
   | User-Agent        | 浏览器相关信息                                         |
   | Connection        | 连接的状态。Keep-Alive保持连接                         |
   | If-Modified-Since | 客户端浏览器缓存文件的最后修改时间                     |
   | Cookie            | 会话管理相关，非常的重要                               |

3. 请求空行：普通换行，用于区分请求头和请求体

4. 请求体：只有POST提交方式才有请求体，用于显示提交参数

**请求的方式**

- GET
  ![](E:\Typora\学习笔记\images\get请求方式.png)

- POST
  ![](E:\Typora\学习笔记\images\post请求方式.png)

> 只有POST请求方式存在请求体，GET请求方式没有请求体
> get提交的参数在请求行中，post提交的参数在请求体中

#### 协议的响应

**响应的组成部分**

1. 响应行：请求方式 HTTP/版本号 状态码 状态描述
   ==常见状态码==

   | 状态码  | 说明                                 |
   | ------- | ------------------------------------ |
   | 200     | 一切OK                               |
   | 302/307 | 请求重定向，两次请求，地址栏发生变化 |
   | 304     | 请求资源未发生变化，使用缓存         |
   | 404     | 请求资源未找到                       |
   | 500     | 服务器错误                           |

2. 响应头

   | 名称                   | 说明                                       |
   | ---------------------- | ------------------------------------------ |
   | Location               | 请求重定向的地址，常与302，307配合使用     |
   | Server                 | 服务器相关信息                             |
   | Content-Type           | 响应正文的MIME类型                         |
   | Content-Length         | 响应正文的长度                             |
   | Content-Disposition    | 告知客户端浏览器，以下载的方式打开响应正文 |
   | Refresh                | 定时刷新                                   |
   | Last-Modified          | 服务器资源的最后修改时间                   |
   | Set-Cookie             | 会话管理相关，非常的重要                   |
   | Expires:-1             | 服务器资源到客户端浏览器后的缓存时间       |
   | Catch-Control:no-catch | 不要缓存                                   |

3. 响应空行：普通换行，用于区分响应头和响应体

4. 响应体：将资源文件发送给客户端浏览器进行解析

### 发布资源案例

**发布静态资源**

1. 创建一个Java WEB项目

2. 将静态页面所需资源导入到项目的web目录下

3. 修改web.xml配置文件，修改默认主页

   ```xml
   <!--在web.xml中加入-->
   <welcome-file-list>
       <welcome-file>/路径/文件名.html</welcome-file>
   </welcome-file-list>
   ```

4. 将项目部署到tomcat中

5. 启动tomcat服务

6. 打开浏览器查看页面

#### Servlet介绍

- Servlet是运行在Java服务器端的程序，用于接收和响应来自客户端基于HTTP协议的请求。
- 如果想实现Servlet的功能，可以通过实现==javax.servlet.Servlet==接口或者继承它的实现类。
- 核心方法：service()，任何客户端的请求都会经过该方法。

**发布动态资源**

1. 创建一个JavaWEB项目

2. 将静态页面所需资源导入到项目的web目录下

3. 修改web.xml配置文件，修改默认主页

4. 在项目的src路径下编写一个类，实现Servlet接口

5. 重写service方法，输出一句话即可

6. 修改web.xml配置文件，配置servlet相关资源

   ```xml
   <!--Servlet声明-->
   <servlet>
       <servlet-name>自定义名称</servlet-name>
       <servlet-class>java全类名（包名.类名）</servlet-class>
   </servlet>
   
   <!--Servlet映射-->
   <servlet-mapping>
       <servlet-name>和声明中的名称保持一致</servlet-name>
       <url-pattern>/访问路径(浏览器地址栏要输入的访问路径)</url-pattern>
   </servlet-mapping>
   ```

7. 将项目部署到tomcat中

8. 启动tomcat服务

9. 打开浏览器测试功能

**执行流程**

1. 通过浏览器访问到指定的资源路径
2. 通过url-pattern找到对应的name标签
3. 通过name找到对应的Servlet声明
4. 在声明中找到对应的Java实现类
5. 执行service方法

### Servlet

#### 概述

- Servlet是运行在Java服务器端的程序，用于接收和响应来自客户端基于HTTP协议的请求

- 是一个接口(javax.servlet.Servlet)，常用实现类：GenericServlet、HttpServlet
- 所有的客户端请求都会经过service方法进行处理
- 初始化会调用init方法，销毁时会调用destroy方法

#### 执行过程

1. 客户端浏览器向Tomcat服务器发起请求
2. Tomcat服务器解析请求地址(URL)
3. Tomcat根据地址找到对应的项目
4. 找到项目中的web.xml文件
5. 解析请求资源地址(URI)
6. 找到项目的资源(对应的Java类)
7. 执行service方法，响应给客户端浏览器

**关系视图**

![](E:\Typora\学习笔记\images\Servlet关系视图.png)

#### 实现方式

1. 实现==Servlet==接口，实现所有的抽象方法，该方式支持最大程度的自定义
2. 继承==GenericServlet==抽象类，必须重写==service==方法，其他方法可选择重写。该方式让我们开发servlet变得简单。但是这种方式与HTTP协议无关
3. 继承==HttpServlet==抽象类，需要重写==doGet==和==doPost==方法。该方式表示请求和响应都需要和HTTP协议相关

#### 生命周期

- 对象的生命周期，就是对象从出生到死亡的过程。即：出生 =》活着 =》死亡。官方说法是对象创建到销毁的过程
- 出生：请求第一次到达Servlet时，对象就创建出来，并且初始化成功。只出生一次，将对象放到内存中
- 活着：服务器提供服务的整个过程中，该对象一直存在，每次都是执行service方法
- 死亡：当服务器停止时，或者服务器宕机时，对象死亡

> 出生对应的是`init`方法
> 活着对应的是`service`方法(`doGet`和`doPost`方法)
> 死亡对应的是`destroy`方法

**结论：**Servlet对象只会创建一次，销毁一次。所以Servlet对象只有一个实例。如果一个对象实例在应用中是唯一的存在，那么就称他为单例模式

#### 线程安全问题

- 由于Servlet采用的是单例设计模式，也就是整个应用中只有一个实例对象。所以我们需要分析这个唯一的实例对象中的类成员是否线程安全
- 模拟用户登录功能来查看Servlet线程是否安全

**结论：**一个浏览器代表一个线程，多个浏览器代表多个线程。按理说应该是每个浏览器查看的都是自己的信息。但结果浏览器中数据混乱。因此，我们可以认为==Servlet是线程不安全的！==

**解决：**定义类成员要谨慎。如果是共用的，并且只会在初始化时赋值，其它时间都是获取的话，那么是没问题的。如果不是共用的，或者每次使用都有可能对其赋值，那就要考虑线程安全的问题了，可以将其定义到doGet或doPost方法内或者使用同步功能即可

#### 映射方式

1. 具体名称的方式。访问的资源路径必须和映射配置完全相同==【常用】==

   ```xml
   <servlet>
           <servlet-name>Demo</servlet-name>
           <servlet-class>study.servlet.Demo</servlet-class>
       </servlet>
       <servlet-mapping>
           <servlet-name>Demo</servlet-name>
           <url-pattern>/Demo</url-pattern>
       </servlet-mapping>
   ```

2. `/` 开头 + 通配符的方式。只要符合目录结构即可，不用考虑结尾是什么

   ```xml
   <servlet>
           <servlet-name>Demo2</servlet-name>
           <servlet-class>study.servlet.Demo2</servlet-class>
       </servlet>
       <servlet-mapping>
           <servlet-name>Demo2</servlet-name>
           <url-pattern>/Demo2/*</url-pattern>
       </servlet-mapping>
   ```

3. 通配符 + 固定格式结尾的方式。只要符合固定结尾格式即可，不用考虑前面的路径

   ```xml
   <servlet>
           <servlet-name>Demo2</servlet-name>
           <servlet-class>study.servlet.Demo2</servlet-class>
       </servlet>
       <servlet-mapping>
           <servlet-name>Demo2</servlet-name>
           <url-pattern>*.test</url-pattern>
       </servlet-mapping>
   ```

**注意：**优先级问题。越是具体的优先级越高，越是模糊的 优先级越低。==第一种 > 第二种 > 第三种==



**多路径映射**

- 我们可以给一个Servlet配置多个访问映射，从而根据不同的请求路径来实现不同的功能
- 场景分析
  如果访问的资源路径是/vip，商品价格打9折
  如果访问的资源路径是/vvip，商品价格打5折
  如果访问的资源路径是其它，商品价格不打折
- 采用第二种映射方式实现多路径映射(`/` + 通配符)

```java
package study.servlet;

import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.io.PrintWriter;

public class Demo3 extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        // 获取浏览器路径
        String requestURI = req.getRequestURI();
        // 分隔路径
        String path = requestURI.substring(requestURI.lastIndexOf("/"));
        // 路径判断，区分价格
        if(path.equals("/vip")){
            System.out.println("100元");
        }else if(path.equals("/vvip")){
            System.out.println("200元");
        }else System.out.println("300元");
    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        doGet(req,resp);
    }
}
```



#### 创建时机

1. 第一次访问时创建
   - 优势：减少对服务器内存的浪费。提高了服务器启动的效率
   - 弊端：如果有一些要在应用加载时就做的初始化操作无法完成
2. 服务器加载时创建
   - 优势：提前创建好对象，提高了首次执行的效率。可以完成一些应用加载时要完成的初始化操作
   - 弊端：对服务器内存占用较多，影响了服务器启动的效率
3. 修改Servlet创建时机。在`<servlet>`标签中，添加`<load-on-startup>`标签
   `<load-on-startup>1</load-on-startup>`
   ==正整数代表服务器加载时创建，值越小，优先级越高。负整数或不写代表第一次访问时创建==

#### 默认Servlet

- 默认Servlet是由服务器提供的一个Servlet。它配置在 Tomcat 的 conf 目录中的 web.xml 中
  ![image-20220213180659839](E:\Typora\学习笔记\images\默认Servlet.png)

- 它的映射路径是`<url-pattern>/<url-pattern>`。我们在发送请求时，首先会在我们项目中的web.xml 中查找映射配置，找到则执行。但是当找不到对应的Servlet 路径时，就去找默认的 Servlet ，由默认Servlet 处理。所以，一切都是Servlet

### ServletConfig

- ServletConfig 是Servlet 的配置参数对象，在Servlet 的规范中，允许为每一个Servlet 都提供一些 初始化的配置。所以，每个Servlet 都有一个自己的ServletConfig
- 作用：在Servlet 的初始化时，把一些配置信息（键值对的形式）传递给Servlet
- 生命周期：和Servlet 相同

#### 配置方式

- 在`<servlet>`标签中，通过 `<init-param>`标签来配置。有两个子标签

- `<param-name>`：代表初始化参数的key

- `<param-value>`：代表初始化参数的value

  ```xml
  <servlet>
      <servlet-name>servletConfigDemo</servlet-name>
      <servlet-class>study.servlet.servletConfigDemo</servlet-class>
      
      <init-param>
          <param-name>encoding</param-name>
          <param-value>UTF-8</param-value>
      </init-param>
      <init-param>
          <param-name>desc</param-name>
          <param-value>This is ServletConfig</param-value>
      </init-param>
  </servlet>
  ```

#### 常用方法

| 返回值              | 方法名                        | 说明                     |
| ------------------- | ----------------------------- | ------------------------ |
| String              | getInitParameter(String name) | 根据参数名称获取参数的值 |
| Enumeration<String> | getInitParameterNames()       | 获取所有参数名称的枚举   |
| String              | getServletName()              | 获取Servlet的名称        |
| ServletContext      | getServletContext()           | 获取ServletContext对象   |

- 通过init方法，来对ServletConfig对象进行赋值

  ```java
  private ServletConfig config;
  public void init(ServletConfig config) throws ServletException{
      this.config = config;
  }
  ```

- 枚举项遍历

  ```java
  Enumeration<String> keys = config.getInitParameterNames();
  while(keys.hasMoreElements()){
      String key = keys.nextElement();
      String value = config.getInitParameter(key);
      System.out.println(key + "--" + value);
  }
  ```

```java
// ServletConfigDemo测试代码
package study.servlet;

import javax.servlet.ServletConfig;
import javax.servlet.ServletContext;
import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.util.Enumeration;

public class ServletConfigDemo extends HttpServlet {
    private ServletConfig config;
    // 通过init方法对config赋值，获取ServletConfig对象
    @Override
    public void init(ServletConfig config) throws ServletException {
        this.config = config;
    }

    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        // 根据name获取value
        String encoding = config.getInitParameter("encoding");
        System.out.println("encoding:" + encoding);

        // 获取所有name并遍历
        Enumeration<String> names = config.getInitParameterNames();
        while(names.hasMoreElements()){
            String name = names.nextElement();
            String value = config.getInitParameter(name);
            System.out.println(name + "---" + value);
        }
        // 获取Servlet-name
        String sname = config.getServletName();
        System.out.println("Servlet-name：" + sname);
        // 获取ServletContext对象
        ServletContext servletContext = config.getServletContext();
        System.out.println(servletContext);
    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        doGet(req,resp);
    }
}
```

### ServletContext

- ServletContext 是应用上下文对象（应用域对象）。每一个应用中只有一个 ServletContext 对象
- 作用：可以配置和获得应用的全局初始化参数，可以实现Servlet 之间的数据共享
- 生命周期：应用一加载则创建，应用被停止则销毁

#### 域对象

- 域对象指的是对象有作用域，也就是作用范围。域对象可以实现数据的共享。不同作用范围的域对象，共享数据的能力也不一样
- 在Servlet 规范中，一共有4个域对象。ServletContext 就是其中的一个。他也是web 应用中最大的作用域，也叫 application 域。它可以实现整个应用之间的数据共享

#### 配置方式

- 在`<web-app>`标签中，通过`<context-param>`标签来配置。有两个子标签
- `<param-name>`：代表全局初始化参数的key
- `<param-value>`：代表全局初始化参数的value

```xml
<context-param>
	<param-name>globalencoding</param-name>
	<param-value>UTF-8</param-value>
</context-param>
<context-param>
	<param-name>globaldesc</param-name>
	<param-value>This is ServletContext</param-value>
</context-param>
```

#### 常用方法

| 返回值 | 方法名                        | 说明                                   |
| ------ | ----------------------------- | -------------------------------------- |
| String | getInitParameter(String name) | 根据名称获取全局配置的参数             |
| String | getContextPath()              | 获取当前应用的访问虚拟目录             |
| String | getRealPath(String path)      | 根据虚拟目录获取应用部署的磁盘绝对路径 |

> `HttpServlet`类继承自`GenericServlet`类
> `GenericServlet`类中有`getServletContext`方法，可以直接获取`ServletContext`对象

| 返回值 | 方法名                                  | 说明                           |
| ------ | --------------------------------------- | ------------------------------ |
| void   | setAttribute(String name, Object value) | 向应用域对象中存储数据         |
| Object | getAttribute(String name)               | 通过名称获取应用域对象中的数据 |
| void   | removeAttribute(String name)            | 通过名称移除应用域对象中的数据 |

### 注解开发

**Servlet3.0 规范**

- 我们使用的是Tomcat 9版本。JavaEE规范要求是8.对应的Servlet 版本应该是4.x 版本。但是，在企业开发中，稳定要远比追求新版本重要。所以我们会降低版本使用，用的是Servlet 3.1版本。
- 其实我们之前的操作全部是基于 Servlet 2.5版本规范的，也就是借助于配置文件的方式。后来随着软件开发逐步的演变，基于注解的配置开始流行。而Servlet 3.0版本也就开始支持注解开发了
- Servlet 3.0版本既保留了2.5版本的配置方式，同时有支持了全新的注解配置方式。它可以完全不需要 web.xml 配置文件，就能实现 Servlet 的配置，同时还有一些其他的新特性。

#### 自动注解开发

**实现步骤**

1. 创建一个 web 项目
2. 定义一个类，继承HttpServlet
3. 重写 doGet 和 doPost方法
4. 在类上使用@WebServlet 注解并配置Servlet
5. 部署并启动项目
6. 通过浏览器测试

```java
@WebServlet("/servletDemo")
public class ServletDemo extends HttpServlet{
    
}
```

![](E:\Typora\学习笔记\images\注解详解.png)

#### 手动创建容器(了解)

- Servlet 3.0 规范除了使用自动注解的配置方式外，还支持手动创建 Servlet 容器的方式。如果使用必须遵循其编写规范。在3.0 版本加入了一个新的接口：ServletContainerInitializer，需要重写onStartup方法

**步骤**

1. 定义一个类，继承HttpServlet

2. 重写 doGet 和 doPost方法

3. 定义一个类，实现ServletContainerInitializer接口

4. 在src 目录下创建一个META-INF的包

5. 在 META-INF 包下创建一个services 的包

6. 在 services 包下创建一个 javax.servlet.ServletContainerInitializer 的文件

7. 文件中的内容为容器实现类的全类名

8. 在容器实现类中的 onStartup 方法中完成注册 Servlet

   ```java
   public void onStartup(Set<Class<?>> set, ServletContext servletContext){
       // 1.创建ServletDemo类的对象
       ServletDemo servletDemo = new ServletDemo();
       // 2. 在ServletContext 对象中添加Servlet，并得到Servlet的动态配置对象
       ServletRegistration.Dynamic registration = servletContext.addServlet("ServletDemo", servletDemo);
       // 3. 配置Servlet
       registration.addMapping("/servletDemo");	// 映射访问资源的路径
       registration.setLoadOnStartup(1);	// 设置Servlet加载时机
   }
   ```

9. 部署并启动项目

10. 通过浏览器测试

### 学生管理系统

- 需求：添加学生信息到Java服务器中的本地文件

**步骤**

1. 创建一个 web 项目
2. 创建一个用于保存学生信息的html文件
3. 创建一个类，继承HttpServlet
4. 重写doGet 和 doPost 方法
5. 在web.xml 文件中修改默认主页和配置 Servlet
6. 在doGet 方法中接收表单数据保存到文件中，并响应给浏览器结果
7. 部署并启动项目
8. 通过浏览器测试

> 获取表单数据
> `req.getParameter(name值)`：就可以通过HttpServletRequest 对象中的方法 通过表单的name属性获取到对应的表单数据
>
> 响应数据
> `PrintWriter pw = resp.getWriter()`：通过 HttpServletResponse 对象中的方法获取输出流对象
> `pw.println("Save Success")`：将指定内容响应到浏览器中

```html
<!--studentAdd.html-->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>添加学生</title>
</head>
<body>
    <form action="/add" method="get">
        姓名：<input type="text" name="username"> <br>
        年龄：<input type="number" name="age"> <br>
        成绩：<input type="number" name="score">   <br>
        <button type="submit">添加</button>
    </form>
</body>
</html>
```

```xml
<!--web.xml-->
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
         version="4.0">
    <!--配置首页-->
    <welcome-file-list>
        <welcome-file>/studentAdd.html</welcome-file>
    </welcome-file-list>
    <!--Servlet声明-->
    <servlet>
        <servlet-name>StudentServlet</servlet-name>
        <servlet-class>studentServlet.add</servlet-class>
    </servlet>
    <servlet-mapping>
        <servlet-name>StudentServlet</servlet-name>
        <url-pattern>/add</url-pattern>
    </servlet-mapping>
</web-app>
```

```java
// add.java
package studentServlet;

import javax.servlet.ServletException;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.BufferedWriter;
import java.io.FileWriter;
import java.io.IOException;
import java.io.PrintWriter;

public class add extends HttpServlet {
    @Override
    protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        // 获取对应表单内容
        String username = req.getParameter("username");
        String age = req.getParameter("age");
        String score = req.getParameter("score");
        // 保存到本地文件
        BufferedWriter bw = new BufferedWriter(new FileWriter("E:\\Java\\code\\StudentServlet\\stu.txt",true));
        bw.write(username + "," + age + "," + score);
        bw.newLine();
        bw.close();

        // 响应给浏览器
        PrintWriter pw = resp.getWriter();
        pw.println("Save Success!!!");
        pw.close();
    }

    @Override
    protected void doPost(HttpServletRequest req, HttpServletResponse resp) throws ServletException, IOException {
        doGet(req, resp);
    }
}
```

### 请求对象

**请求：**获取资源。在BS架构中，就是客户端浏览器向服务端发出询问。

**请求对象：**就是在项目中用于发送请求的对象(`ServletRequest`和`HttpServletRequest`)

> ServletRequest 和 HttpServletRequest 都是接口，但是Tomcat 服务器会帮我们处理好实现类的赋值等工作，我们不需要关心这些

#### 获取各种路径

| 返回值       | 方法名           | 说明                |
| ------------ | ---------------- | ------------------- |
| String       | getContextPath() | 获取虚拟目录名称    |
| String       | getServletPath() | 获取Servlet映射路径 |
| String       | getRemoteAddr()  | 获取访问者ip地址    |
| String       | getQueryString() | 获取请求的消息数据  |
| String       | getRequestURI()  | 获取统一资源标识符  |
| StringBuffer | getRequestURL()  | 获取统一资源定位符  |

#### 获取请求头

| 返回值              | 方法名                  | 说明                     |
| ------------------- | ----------------------- | ------------------------ |
| String              | getHeader(String name)  | 根据请求头名称获取一个值 |
| Enumeration<String> | getHeaders(String name) | 根据请求头名称获取多个值 |
| Enumeration<String> | getHeaderNames()        | 获取所有请求头名称       |

#### 获取请求参数信息

| 返回值               | 方法名                          | 说明                 |
| -------------------- | ------------------------------- | -------------------- |
| String               | getParameter(String name)       | 根据名称获取数据     |
| String[]             | getParameterValues(String name) | 根据名称获取所有数据 |
| Enumeration<String>  | getParameterNames()             | 获取所有名称         |
| Map<String,String[]> | getParameterMap()               | 获取所有参数的键值对 |

**获取请求参数并封装对象**

1. 手动封装方式
   成员变量名称和参数name属性值保持一致
2. 反射封装方式
   属性描述器：`PropertyDescriptor`(根据名称获取到对象中对应的get和set方法)
3. 工具类封装方式
   `beanutils`工具类，`populate`方法

#### 流对象获取请求信息

| 返回值             | 方法名           | 说明           |
| ------------------ | ---------------- | -------------- |
| BufferedReader     | getReader()      | 获取字符输入流 |
| ServletInputStream | getInputStream() | 获取字节输入流 |

> 用IO流获取请求信息时，不支持get方式，只支持post提交方式
> 获得到的流对象都不是自己new出来的，不需要close释放资源，会由请求对象处理并释放

#### 中文乱码问题

- GET方式
  没有乱码问题，在Tomcat 8 版本后已经解决
- POST方式
  有乱码问题，可以通过 setCharacterEncoding() 方法来解决（编码格式要和页面编码格式一致）

#### 请求域

- 请求域(request域)：可以在一次请求范围内进行共享数据。

- 一般用于请求转发的多个资源中共享数据

- 请求对象操作共享数据方法

  | 返回值 | 方法名                                  | 说明                           |
  | ------ | --------------------------------------- | ------------------------------ |
  | void   | setAttribute(String name, Object value) | 向请求域对象中存储数据         |
  | Object | getAttribute(String name)               | 通过名称获取请求域对象中的数据 |
  | void   | removeAttribute(String name)            | 通过名称移除请求域对象中的数据 |

#### 请求转发

- 请求转发：客户端的一次请求到达以后，发现需要借助其他 Servlet 来实现功能(浏览器请求，A发现做不了，转发给B去做)
- 特点
  - 浏览器地址栏不变
  - 域对象中的数据不丢失
  - 负责转发的Servlet 转发前后的响应正文会丢失
  - 由转发的目的地来响应客户端

| 返回值            | 方法名                                            | 说明                         |
| ----------------- | ------------------------------------------------- | ---------------------------- |
| RequestDispatcher | getRequestDispatcher(String name)                 | 获取请求调度对象             |
| void              | forward(ServletRequest req, ServletResponse resp) | 实现转发(用请求调度对象调用) |

#### 请求包含

- 请求包含：可以合并其他Servlet 中的功能一起响应给客户端(浏览器请求，A只能做一半，另一半让B做)
- 特点
  - 浏览器地址栏不变
  - 域对象中的数据不丢失
  - 被包含的 Servlet 响应头会丢失

| 返回值            | 方法名                                            | 说明             |
| ----------------- | ------------------------------------------------- | ---------------- |
| RequestDispatcher | getRequestDispatcher(String name)                 | 获取请求调度对象 |
| void              | include(ServletRequest req, ServletResponse resp) | 实现包含         |

### 响应对象

- 响应：回馈结果。在 BS 架构中，就是服务器给客户浏览器反馈结果

- 响应对象：就是在项目中用于发送响应的对象
  `ServletResponse`（接口）
  `HttpServletResponse`（继承自ServletResponse，基于http协议的接口）

  > 和请求对象一样，不需要我们去写实现类，在Tomcat 服务器创建好，在执行 `doGet` 或者 `doPost` 方法时，服务器会把相应的实现类对象传递

#### 常见状态码

| 状态码 | 说明                         |
| ------ | ---------------------------- |
| 200    | 成功                         |
| 302    | 重定向                       |
| 304    | 请求资源未改变，使用缓存     |
| 400    | 请求错误，常见于请求参数错误 |
| 404    | 请求资源未找到               |
| 405    | 请求方式不支持               |
| 500    | 服务器错误                   |

#### 字节流响应消息

| 返回值              | 方法名                                    | 说明                               |
| ------------------- | ----------------------------------------- | ---------------------------------- |
| ServletOutputStream | getOutputStream()                         | 获取响应字节输出流对象             |
| void                | setContentType("text/html;charset=UTF-8") | 设置响应内容类型，解决中文乱码问题 |

**步骤：**

1. 获取字节输出流对象
2. 定义一个消息（一个字符串）
3. 通过字节流对象输出

> 获取到的字节输出流对象不需要close释放，会由响应对象处理并释放

#### 字符流响应消息

| 返回值      | 方法名                                    | 说明                               |
| ----------- | ----------------------------------------- | ---------------------------------- |
| PrintWriter | getWriter()                               | 获取响应字符输出流对象             |
| void        | setContentType("text/html;charset=UTF-8") | 设置响应内容类型，解决中文乱码问题 |

> 步骤和上面字节流一样，同样不需要自己close释放资源

#### 响应图片

1. 通过文件的相对路径获取绝对路径(getRealPath)

2. 创建字节输入流对象，关联读取的图片路径

3. 通过响应对象获取字节输出流对象

4. 循环读取和写出图片

#### 设置缓存

- 缓存：对于不经常变化的数据，我们可以设置合理的缓存时间，以避免浏览器频繁请求服务器。以此来提高效率

| 返回值 | 方法名                               | 说明               |
| ------ | ------------------------------------ | ------------------ |
| void   | setDateHeader(String name,long time) | 设置消息头添加缓存 |

> 例：`resp.setDateHeader("Expires",System.currentTimeMillis() + 1*60*60*1000);` 设置一个小时缓存时间
> Expires 就是过期的意思

#### 定时刷新

- 定时刷新：过了指定时间后，页面自动进行跳转

| 返回值 | 方法名                              | 说明               |
| ------ | ----------------------------------- | ------------------ |
| void   | setHeader(String name,String value) | 设置消息头定时刷新 |

> 例：`resp.setHeader("Refresh","3;URL=要跳转的路径")`

#### 请求重定向

- 请求重定向：客户端的一次请求到达后，发现需要借助其他Servlet 来实现功能

- 特点：浏览器地址栏会发生改变，两次请求，请求域对象中不能共享数据，可以重定向到其他服务器

- 重定向实现原理

  1. 设置响应状态码为302：`resp.setStatus(302);`
  2. 设置响应的资源路径(响应到哪里去，通过响应消息头 location 来指定)：`resp.setHeader("location","/response/responseDemo")`

- 响应对象重定向方法

  | 返回值 | 方法名                    | 说明       |
  | ------ | ------------------------- | ---------- |
  | void   | sendRedirect(String name) | 设置重定向 |

#### 文件下载

1. 创建字节输入流，关联读取的文件
2. 设置响应消息头支持的类型：`resp.setHeader("Content-Type","application/octet-stream")`
   Content-Type：消息头名称，代表所支持的类型
   application/octet-stream：消息头参数，代表应用的类型为字节流
3. 设置响应消息头以下载方式打开资源：`resp.setHeader("Content-Disposition","attachment;filename=下载的文件名称")`
   Content-Disposition：消息头名称，代表处理形式
   attachment;filename=xxx：消息头参数，代表附件的形式进行处理，filename代表指定下载文件的名称
4. 通过响应对象获取字节输出流对象
5. 循环读写
6. 释放资源

### Cookie

### Session

### JSP

### EL表达式

### JSTL

### Filter

### Listener

## MYSQL

## JDBC

## Mybatis

## JavaScript

## jQuery

## AJAX

## Vue + Element

## Redis

## Maven基础

## Web项目实战-黑马页面



