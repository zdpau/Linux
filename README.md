# Linux

在终端，你有一个被称为shell的东西,这是操作系统的一部分，它定义了终端的行为方式，并为您查找运行（或执行）命令。有各种各样的shell，但最常见的一种是称为bash的代表Bourne再次壳。(This is a part of the operating system that defines how the terminal will behave and looks after running (or executing) commands for you.) 如果你想知道你在使用哪个shell，你可以使用一个名为echo的命令来显示一个系统变量来描述当前shell。回声是用来显示消息的命令。echo $shell

pwd which stands for Print Working Directory:显示当前路径

ls （short for list）

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
