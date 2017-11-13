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

Kyle 20 Stan 11 Kenny 37

在Linux系统中，通常只有2个人可以更改文件或目录的权限。文件或目录的所有者和根用户。root用户是超级用户谁可以对系统做任何事。通常，系统的管理员将是唯一能够访问root帐户并使用它维护系统的管理员。一般来说，普通用户大多只访问他们的主目录中的文件和目录，可能还有其他一些共享和协作工作的目的，这有助于维护系统的安全性和稳定性。

通常，为了获得最佳的安全性，您不应该给组或其他人write access访问您的主目录的权限，但是不读的执行有时会很方便。这允许人们进入您的主目录，但不让他们看到有什么。使用此示例的一个例子是针对个人网页。

这是一个典型的系统中运行的服务器，让用户都有自己的网站空间。一个常见的设置，如果你将一个目录在你的家目录称为public_html然后服务器将读取并显示它的内容。服务器运行一个不同的用户给你但是默认情况下不会有获得和读取这些文件。在这种情况下，有必要将你的家目录下执行，服务器的用户可以访问所需的资源。
