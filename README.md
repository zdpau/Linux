# Linux

一、

在终端，你有一个被称为shell的东西,这是操作系统的一部分，它定义了终端的行为方式，并为您查找运行（或执行）命令。有各种各样的shell，但最常见的一种是称为bash的代表Bourne again shell。(This is a part of the operating system that defines how the terminal will behave and looks after running (or executing) commands for you.) 如果你想知道你在使用哪个shell，你可以使用一个名为echo的命令来显示一个系统变量来描述当前shell。回声是用来显示消息的命令。echo $shell

二、

pwd which stands for Print Working Directory:显示当前路径

三、

ls （short for list）

四、

drwxr-xr-x  2 ryan users 4096 May 05 17:25 alsa.d

-rwxr-xr-x 18 root root 78 Feb 17 09:12 aliases

First character indicates whether it is a normal file ( - ) or directory ( d )

Next 9 characters are permissions for the file or directory (we'll learn more about them in section 6).

The next file is the number of blocks (don't worry too much about this).

The next field is the owner of the file or directory (ryan in this case).

The next field is the group the file or directory belongs to (users in this case).

Following this is the file size.

Next up is the file modification time.

Finally we have the actual name of the file or directory.

五、

相对路径、绝对路径

绝对路径指定与根目录相关的位置（文件或目录）。您可以很容易地识别它们，因为它们总是以前斜杠（/）开头。

相对路径指定与当前系统所在位置相关的位置（文件或目录）。他们不会以斜线开始。

~ (tilde) - home directory的快捷方式，我的是/Users/zhangduo，比如要去/Users/zhangduo/Document，可以直接输入~/Dpcument

.（DOT）-这是对当前目录的引用。ls ~/Documents也可以写成ls ./Documents

..（dotdot）-这是父目录。如果你在/home/ryan 你可以运行 ls ../../ and this would do a listing of the root directory.

六、

cd which stands for change directory

cd / 代表进入根目录， ls / 代表查看根目录的文件

七、

/etc - Stores config files for the system.（存储系统的配置文件）

/var/log - Stores log files for various system programs.（为各种系统程序存储日志文件。）（可能没有权限查看目录中的所有内容）

/bin - The location of several commonly used programs（几个常用程序的位置）

/usr/bin - Another location for programs on the system.（另一个位置的程序系统。）



