# Linux

https://www.tutorialspoint.com/unix/unix-vi-editor.htm
https://ryanstutorials.net/linuxtutorial/vi.php

Linux中的许多事情不是直接完成的，而是通过了解系统的某些命令和方面的行为，并以创造性的方式使用它们来达到预期的结果。请记住，在介绍中，我们讨论了命令行，为您提供了一系列构建块。您可以随意使用这些构建块，但如果您了解它们是如何发挥功能的，那么您就可以真正有效地完成这些功能。（Many things in Linux are not done directly but by knowing the behaviour of certain commands and aspects of the system and using them in creative ways to achieve the desired outcome.Remember in the introduction we talked about the command line as providing you with a series of building blocks. You are free to use these building blocks in any way you like but you can really only do this effectively if you understand how they do their function as well as why.）

每当我们在命令行引用一个文件或目录时，它实际上是一条路径。因此，它可以被指定为绝对路径或相对路径。

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

十、

man <command to look up>

man ls

Name

  3、  ls - list directory contents
    
 
Synopsis

  6、  ls [option] ... [file] ...
 
Description

  9、  List information about the FILEs (the current directory by default). Sort entries alphabetically if none of -cftuvSUX nor --sort is specified.
 
  11、  Mandatory arguments to long options are mandatory for short options too.
 
    -a, --all
    
        do not ignore entries starting with .
 
    -A, --almost-all
    
        do not list implied . and ..
        
第3行告诉我们实际的命令，后面是对函数简单的一行描述。

第6行是所谓的大纲。这只是对命令应该如何运行的一个快速概述。方括号（[]）表示某物是可选的。（这一行的选项指的是下面描述的命令行选项）

第9行向我们提供了对命令的更详细的描述。

11行在下面描述的病房都会列出所有的命令行选项的命令都是可用的。

“”“”“To exit the man pages press 'q' for quit.“”“”

man -k <search term> （Do a keyword search for all manual pages containing the given search term.）  
  
对包含给定搜索词的所有手册页进行关键字搜索。
  
man -k后跟要搜寻的关键词。例如man -k ad则显示man手册中所有包含ad的命令或说明文件并列条显示
  
如果您想在手册页中搜索，这也是可能的。要做到这一点，当你在特定的手册页，你想搜索按下斜线' / '，然后输入搜索的术语，并点击'enter',如果这个词出现多次，你可以循环通过他们按' N '按钮下一个。

长命令行选项以两个破折号（-）开始，短选项从一个破折号（-）开始。当我们使用单个破折号时，我们可以在破折号之后放置代表这些选项的所有字母来调用几个选项。

eg:ls -l ; ls --all ; ls -alh

十一、创建目录

mkdir which is short for Make Directory.

mkdir [options] <Directory> 
  

第一个是-p，它告诉mkdir根据需要make父目录。

mkdir -p a/b/c 

在当前目录下建立一个a/b/c的文件路径

第二个是-v，这使得mkdir告诉我们它在做什么

mkdir -pv linuxtutorialwork/foo/bar

mkdir: created directory 'linuxtutorialwork/foo'

mkdir: created directory 'linuxtutorialwork/foo/bar'

十二、删除目录

rmdir [options] <Directory>
  
rmdir支持与mkdir类似的-v和-p选项。其次，一个目录必须是空的，然后再删除它。

十三、创建空白文件

touch [options] <filename>

touch实际上是一个命令，我们可以用来修改文件上的访问和修改时间.

十四、复制文件或目录

cp [options] <source> <destination>
  
当我们使用CP时，目的地可以是文件或目录的路径。如果它是一个文件，那么它将创建源的副本(copy)，但将副本指定为目的地指定的文件名。如果我们提供一个目录作为目的地，那么它将把文件复制到该目录中，副本将具有与源相同的名称。

eg:

ls
example1 foo
cp example1 barney
ls
barney example1 foo
  
cp -r

在它的默认行为CP将只复制一个文件（有一个方法来复制几个文件一气呵成，但我们将在第6节。通配符wildcards）。使用R选项，它代表递归，我们可以复制目录。递归是指我们要看一个目录，所有的文件和目录和子目录，在它的内部，去做同样的事情，继续这样做。
  
例如：

ls
barney example1 foo
cp foo foo2
cp: omitting directory 'foo'
cp -r foo foo2
ls
barney example1 foo foo2

十五、移动、重命名文件或目录

mv which is short for move。它以类似于cp的方式运行。一个优点是我们可以移动目录而不必提供-r选项。

mv [options] <source> <destination>
  
eg:

ls
barney example1 foo foo2
mkdir backups
mv foo2 backups/foo3
mv barney backups/
ls
backups example1 foo

第3行我们创建了一个名为backups的新目录。 
第4行我们将目录foo2移动到目录备份中，并将其重命名为foo3 
第7行我们将文件barney移动到备份中。由于我们没有提供目的地名称，它保持相同的名称。

重命名：

现在，如果我们将目的地指定为与源相同的目录，但使用不同的名称，那么我们已经有效地使用mv重命名文件或目录。

ls
backups example1 foo
mv foo foo3
ls
backups example1 foo3
cd ..
mkdir linuxtutorialwork/testdir
mv linuxtutorialwork/testdir /home/ryan/linuxtutorialwork/fred
ls linuxtutorialwork
backups example1 foo3 fred

第3行我们重命名文件foo为foo3（两条路径都是相对的）。
第6行我们移动到父目录。这样做只是在下一行我们可以说明我们可以在文件和目录上运行命令，即使我们当前不在他们所在的目录中。
第8行我们重命名目录testdir为fred（源路径是相对路径和目的地是一个绝对路径）。

十六、删除文件（和非空目录）

rm [options] <file>

-r 它代表递归。当使用R选项运行RM时，它允许我们删除目录和包含在其中的所有文件和目录。

与R相结合的一个很好的选择是代表交互的i。此选项将在删除每个文件和目录之前提示您，并提供取消命令的选项。

十七、Vi

在VI中有两种模式：插入（或输入）模式和编辑模式。在输入模式下，您可以输入或输入内容到文件中。在编辑模式中，可以移动文件，执行删除、复制、搜索和替换、保存等操作。

vi 文件名， 运行此命令时，它会打开文件。如果文件不存在，那么它将为您创建它，然后打开它。

你总是从编辑模式开始，所以我们要做的第一件事就是按i来切换到插入模式。你可以告诉你什么时候插入模式，因为左下角会告诉你。按Esc键，这将使您回到编辑模式。
如果您不确定是否处于编辑模式，则可以查看左下角。只要它不是INSERT就好。或者你可以直接按Esc确定。如果您已经处于编辑模式，则按ESC键不做任何操作，这样就不会造成任何伤害。

ZZ（注意：大写字母） - 保存并退出 
:q! - 丢弃所有更改，自上次保存并退出
:w  - 保存文件但不退出 
:wq - 再次保存并退出

十八、除了Vi，另外两个查看文件的命令：cat和less。

cat 文件名 

第一个是cat，其实是串联(concatenate)。它的主要目的是将文件连接在一起，但最基本的形式只是查看文件。

如果您运行命令cat，给它一个命令行参数，将看到文件的内容显示在屏幕上，然后是提示符。如果你无意中运行cat,而不给它一个命令行参数，你会注意到光标移动到下一行，然后什么也没有发生。因为我们没有指定一个文件，而是从一个名为STDIN的东西中读取，我们将在“管道和重定向”部分中了解到这是默认的键盘。如果键入一些内容，然后按<enter>，您将看到镜像您的输入到屏幕。要离开这里，您可以按[Ctrl] + c，这是Linux中取消的通用信号。
  
当我们有一个小文件来查看时，cat这个命令是不错的，但是如果文件很大，那么大部分的内容将会跨越屏幕，我们只会看到最后一页的内容。对于较大的文件，有一个更适合的命令less。

less <file> 
  less允许您使用箭头键在文件内上下移动。您可以使用SpaceBar前进整个页面，或者按b返回页面。完成后，您可以按q退出。

十九、

在插入模式下的一些操作

移动按键：
Arrow keys - move the cursor around 移动光标

j, k, h, l - move the cursor down, up, left and right (similar to the arrow keys) 跟箭头键作用一样

^ (caret) - move cursor to beginning of current line  移动光标到当前行的开头

$ - move cursor to end of the current line   移动光标到当前行的结尾

nG - move to the nth line (eg 5G moves to 5th line)   移动到第n行（例如5G移动到第五行）

G - move to the last line    移动到最后一行

w - move to the beginning of the next word  移动到下一个单词的开头

nw - move forward n word (eg 2w moves two words forwards)   向前移动n个单词（如：2w 向前移动两个单词)

b - move to the beginning of the previous word   移动到前一个单词的开头

nb - move back n word     向后移动n个单词

{ - move backward one paragraph  向后移动一段

} - move forward one paragraph   向前移动一段

如果你在编辑模式下输入：set nu， 它将启用行号。

删除、撤销按键：

x - delete a single character 

nx - delete n characters (eg 5x deletes five characters)

dd - delete the current line

dn - d followed by a movement command. Delete to where the movement command would have taken you. (eg d5w means delete 5 words)？？？

u - Undo the last action (you may keep pressing u to keep undoing)

U (Note: capital) - Undo all changes to the current line

二十、使用一组文件的方法。wildcards（通配符）

通配符是一套积木（building blocks），允许你创建一个模式定义一组文件或目录。如您所记得的，每当我们在命令行中引用文件或目录时，我们实际上指的是一条路径。当我们提及一个路径，我们也可以在路径中使用通配符来把它变成一个设置文件或目录。

* - represents zero or more characters

? - represents a single character

[] - represents a range of characters

例子1：

ls b*  查看首字母是b的文件，* 表示后面是什么无所谓

barry.txt blah.txt bob

乍一看，您可能假定上面的命令（ls）接收参数b，然后继续将其转换为所需的匹配项。它实际上是一个提供命令行接口的程序，为我们翻译。 When we offer it this command it sees that we have used wildcards and so, before running the command ( in this case ls ) it replaces the pattern with every file or directory (ie path) that matches that pattern.

We issue the command:

ls b*

Then the system translates this into:

ls barry.txt blah.txt bob

and then executes the program.程序永远不会看到通配符和不知道我们使用他们。

例子2：

ls /home/ryan/linuxtutorialwork/*.txt

/home/ryan/linuxtutorialwork/barry.txt /home/ryan/linuxtutorialwork/blah.txt

例子3：the ? operator. In this example we are looking for each file whose second letter is i.

ls ?i*

firstfile video.mpeg

例子4： how about every file with a three letter extension.

ls *.???

barry.txt blah.txt example.png frog.png

例子5： the range operator ( [ ] ). 与前面指定任何字符的2个通配符不同，范围运算符允许限制为字符的子集。在这个例子中，我们正在寻找名称以s或v开头的每个文件。

ls [sv]*

secondfile video.mpeg

例子6： 有了范围，我们也可以使用连字符（hyphen）来包含一个集合。例如，如果我们想要找到名称中包含数字的每个文件，我们可以执行以下操作：

ls *[0-9]*

foo1 foo2 foo3

例子7： 我们也可以使用脱字符caret（^）来反转一个范围，这意味着查找任何不属于以下任何一个字符的字符。

ls [^a-k]*

secondfile thirdfile video.mpeg

通配符的另外的功能：

查找目录中每个文件的文件类型:

file /home/ryan/*

bin: directory

Documents: directory

frog.png: PNG image data

public_html: directory

将所有类型的文件JPG或PNG（图像文件）移到另一个目录中:

mv public_html/*.??g public_html/images/

找出在每个用户的主目录bash_history文件的大小和修改时间。（.bash_history是一个典型的用户主目录保存命令，用户在命令行输入的历史文件。）

ls -lh /home/*/.bash_history

-rw------- 1 harry users 2.7K Jan 4 07:32 /home/harry/.bash_history

-rw------- 1 ryan users 3.1K Jun 12 21:16 /home/ryan/.bash_history



如何在文件和目录上设置Linux权限

二十一、permission 

Linux permissions dictate 3 things you may do with a file, read, write and execute. They are referred to in Linux by a single letter each.Linux权限决定了你可以用文件，读，写和执行三件事情。它们在Linux中由每个单独的字母引用。

r read - you may view the contents of the file.

w write - you may change the contents of the file.

x execute - you may execute or run the file if it is a program or script.

For every file we define 3 sets of people for whom we may specify permissions.对于每个文件，我们定义了3组我们可以指定权限的人员。

owner - a single person who owns the file. (typically the person who created the file but ownership may be granted to some one else by certain users) 拥有文件的单个人。（通常是创建文件的人，但某些用户可以将所有权授予其他人）

group - every file belongs to a single group.每个文件属于单个组。

others - everyone else who is not in the group or the owner.不属于团队或所有者的其他人。

-rwxr----x：

第一个字符标识文件类型。如果是破折号（-），那么它是一个普通文件。如果是d，那么它是一个目录。

以下3个字符代表所有者的权限。字母表示权限的存在，破折号表示未获得许可。在本例中，所有者拥有所有权限（读、写和执行）。

以下3个字符代表组的权限。在这个示例中，组具有读但不写或执行的能力。注意，权限顺序总是被读取，然后写入然后执行。

最后，最后3个字符代表其他人（或其他人）的权限。在这个示例中，它们只具有执行权限。

二十二、 设置权限 chmod It stands for change file mode bits

chmod [permissions] [path]

chmod具有由3个组件组成的权限参数：

我们要给谁改变权限？[ ugoa ]：user (or owner), group, others, all

我们授予或撤销（ granting or revoking）许可—用加（+）或负（-）表示。

我们设置了什么权限？-读（r），写（w）或执行（x）

例子：授予该组的执行权限。然后删除所有者的写权限：

ls -l frog.png

-rwxr----x 1 harry users 2.7K Jan 4 07:32 frog.png

chmod g+x frog.png

ls -l frog.png

-rwxr-x--x 1 harry users 2.7K Jan 4 07:32 frog.png

chmod u-w frog.png

ls -l frog.png

-r-xr-x--x 1 harry users 2.7K Jan 4 07:32 frog.png

不想单独分配权限？我们可以一次分配多个权限。

ls -l frog.png

-rwxr----x 1 harry users 2.7K Jan 4 07:32 frog.png

chmod g+wx frog.png

ls -l frog.png

-rwxrwx--x 1 harry users 2.7K Jan 4 07:32 frog.png

chmod go-x frog.png

ls -l frog.png

-rwxrw---- 1 harry users 2.7K Jan 4 07:32 frog.png

看起来奇怪的是，作为文件的所有者，我们可以删除我们读取，写入和执行文件的能力，但是我们可能希望这样做。也许我们有一个包含数据的文件，我们不希望不小心改变。虽然我们可能会删除这些权限，但我们可能不会删除我们设置这些权限的权限，因此我们始终可以控制我们所有权下的每个文件。

上面概述的方法对设置权限来说不是太难，但是如果我们有一套特定的权限，我们可以定期应用到特定的文件（例如我们将在第13节中看到的脚本），那么可能会有些单调乏味。幸运的是，有一个简单的方法来指定权限，这使得这很容易。就是用数字 r=4,w=2 ,x=1. 例如，755或750常用于脚本。

ls -l frog.png

-rw-r----x 1 harry users 2.7K Jan 4 07:32 frog.png

chmod 751 frog.png

ls -l frog.png

-rwxr-x--x 1 harry users 2.7K Jan 4 07:32 frog.png

chmod 240 frog.png

ls -l frog.png

--w-r----- 1 harry users 2.7K Jan 4 07:32 frog.png

目录可以使用同一系列的权限，但是它们的行为稍有不同。

r -你有能力读取目录的内容（例如ls）☆☆☆

w -您有能力写入目录（即创建文件和目录）☆☆☆

X -你有能力进入那个目录（如CD）。☆☆☆

ls testdir

file1 file2 file3

chmod 400 testdir

ls -ld testdir

-r-------- 1 ryan users 2.7K Jan 4 07:32 testdir

cd testdir

cd: testdir: Permission denied

ls testdir

file1 file2 file3

chmod 100 testdir

ls -ld testdir

---x------ 1 ryan users 2.7K Jan 4 07:32 testdir

cd testdir

ls testdir

ls: cannot open directory testdir/: Permission denied

注意：：：当我们运行ls时，使用了ls -ld xxx，它代表目录。通常情况下，如果我们给ls一个参数，它是一个目录，它将列出该目录的内容。但在这种情况下，我们直接对目录的权限感兴趣，而d选项允许我们获得该权限。

例如，您可能有一个目录，您没有读权限。它里面可能有文件，你有读权限。只要您知道文件存在和它的名称，您仍然可以读取文件。

ls -ld testdir

--x------- 1 ryan users 2.7K Jan 4 07:32 testdir

cd testdir

ls testdir

ls: cannot open directory .: Permission denied

cat samplefile.txt

Kyle 20
Stan 11
Kenny 37

在Linux系统中，通常只有2个人可以更改文件或目录的权限。文件或目录的所有者和根用户。root用户是超级用户谁可以对系统做任何事。通常，系统的管理员将是唯一能够访问root帐户并使用它维护系统的管理员。一般来说，普通用户大多只访问他们的主目录中的文件和目录，可能还有其他一些共享和协作工作的目的，这有助于维护系统的安全性和稳定性。

通常，为了获得最佳的安全性，您不应该给组或其他人write access访问您的主目录的权限，但是不读的执行有时会很方便。这允许人们进入您的主目录，但不让他们看到有什么。使用此示例的一个例子是针对个人网页。

这是一个典型的系统中运行的服务器，让用户都有自己的网站空间。一个常见的设置，如果你将一个目录在你的家目录称为public_html然后服务器将读取并显示它的内容。服务器运行一个不同的用户给你但是默认情况下不会有获得和读取这些文件。在这种情况下，有必要将你的家目录下执行，服务器的用户可以访问所需的资源。










