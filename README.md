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

八、

Everything is a File (Even directories.)

Linux is an Extensionless System。在linux下，原本是图像文件，你就是改了扩展名，打开还是图像。

使用file [path]看出是什么文件(obtain information about what type of file a file or directory is.)

Linux is Case Sensitive。

例如：FILE1.txt File1.txt file1.TXT

Linux将这些都视为不同的和独立的文件。

file Documents/file1.txt

Documents/file1.txt: ERROR: cannot open 'file1.txt' (No such file or directory)

九、

cd Holiday Photos, 想进入Holiday Photos这个目录输入这个是不行的，因为Holiday Photos被视为两个命令行参数。CD移动到第一个命令行参数指定的目录中。为了解决这个问题，我们需要确定终端，我们希望假日照片被看作是一个单一的命令行参数。有两种方法可以做到这一点，无论哪种方式都是有效的。

第一种：Quotes 引号

cd 'Holiday Photos'

第二种：Escape Characters 转义字符，反斜杠backslash （\）

cd Holiday\ Photos

在上面的例子中，假日和照片之间的空间通常有一个特殊的意义，就是把它们分隔成不同的命令行参数。因为我们放置一个反斜杠在它前面，那特殊的意义被删除。

如果您在遇到目录名中的空格之前使用它，那么终端将自动为您取消名称中的空格。？？？？？

如果文件或目录的名称以 . (full stop) 然后它被认为是隐藏的。

要使文件或目录隐藏起来，您所需要做的就是创建文件或目录名称为.或者重命名为.  同样，您可以重命名隐藏文件以删除“.”
它将成为公开的。

我们可以使用ls -a 来查看隐藏文件








