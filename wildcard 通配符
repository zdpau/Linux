使用一组文件的方法。wildcards（通配符）

通配符是一套积木（building blocks），允许你创建一个模式定义一组文件或目录。如您所记得的，每当我们在命令行中引用文件或目录时，我们实际上指的是一条路径。当我们提及一个路径，我们也可以在路径中使用通配符来把它变成一个设置文件或目录。

represents zero or more characters
? - represents a single character

[] - represents a range of characters

例子1：

ls b*  查看首字母是b的文件，* 表示后面是什么无所谓

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

ls [0-9]

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
