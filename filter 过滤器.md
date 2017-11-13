二十三、filter

在Linux命令行上下文中的过滤器是一个程序，它接受文本数据，然后以特定的方式转换它。过滤器是一种获取原始数据的方法，它是由另一个程序生成的，或者存储在一个文件中，并以一种更适合我们所追求的方式进行操作。

这些过滤器通常有各种命令行选项来修改它们的行为，因此检查过滤器的man页面总是可以看到可用的。

在下面的例子中，我们将通过一个文件向这些程序提供输入，但在管道和重定向部分，我们将看到我们可以通过其他方法提供输入，从而增加更多的能量。这个示例文件包含一个内容列表，纯粹是为了使示例更易于理解，但要知道它们与其他任何文本数据都是相同的。另外，记住文件实际上是指定一个路径，所以你可以使用绝对路径和相对路径和通配符。

例子文件如下

cat mysampledata.txt

Fred apples 20

Susy oranges 5

Mark watermellons 12

Robert pears 4

Terry oranges 9

Lisa peaches 7

Susy oranges 12

Mark grapes 39

Anne mangoes 7

Greg pineapples 3

Oliver rockmellons 2

Betty limes 14

①   Head是一个程序，它打印输入的第一个这么多的行。默认情况下，它会打印前10行，但我们可以用命令行参数来修改。

head [-number of lines to print] [path]

head -4 mysampledata.txt

Fred apples 20

Susy oranges 5

Mark watermellons 12

Robert pears 4

②   tail是head的反面。tail是一个打印输入的最后那么多行的程序。默认情况下，它会打印最后10行，但我们可以用命令行参数来修改。

tail [-number of lines to print] [path]

tail -3 mysampledata.txt

Greg pineapples 3

Oliver rockmellons 2

Betty limes 14

③   sort将排序它的输入。默认情况下，它将按字母顺序排序，但有许多选项可用于修改排序机制。一定要查看manu页面，看看它可能做的一切。

sort [-options] [path]

sort mysampledata.txt

Anne mangoes 7

Betty limes 14

Fred apples 20

Greg pineapples 3

Lisa peaches 7

Mark grapes 39

Mark watermellons 12

④   nl stands for number lines 单纯就是在前面添加行号

nl [-options] [path]

nl mysampledata.txt

1 Fred apples 20

2 Susy oranges 5

3 Mark watermellons 12

4 Robert pears 4

5 Terry oranges 9

6 Lisa peaches 7

nl -s '. ' -w 10 mysampledata.txt

第一个-s指定在数字之后应该打印什么，而第二个-w指定在数字之前要填充多少个填充。具体代码演示见https://ryanstutorials.net/linuxtutorial/filters.php#nl  -s行号后面加. -w意味在行号前面空多少格

⑤   wc stands for word count

wc [-options] [path] 

-l will give us lines only, -w will give us words and -m will give us characters.

wc mysampledata.txt

12 36 195 mysampledata.txt

12代表有12行，36代表有36个单词（words），195代表有多少个字母（character）

wc -lw mysampledata.txt

12 36 mysampledata.txt

※※※ ⑥   如果你的内容被分割成字段（列），你只需要某些字段，那么cut是一个不错的小程序。

cut [-options] [path]    

默认使用tab作为分隔符来标识字段。但在我们的文件中，我们使用的是一个空格，所以我们需要告诉cut使用空格而不是tab。分隔符可以是您喜欢的任何内容，例如在CSV文件中，分隔符通常是逗号（，）。这就是D选项的作用（我们包括单引号中的空格，所以它知道这是参数的一部分）。F选项允许我们指定我们想要的字段或字段。如果我们想要2个或多个字段，那么我们用逗号分隔它们如下。下面，-f 1 代表选择第一列， -d '' 代表使用空格进行剪切？

cut -f 1 -d ' ' mysampledata.txt        

Fred

Susy

Mark

Robert

Terry

cut -f 1,2 -d ' ' mysampledata.txt

Fred apples

Susy oranges

Mark watermellons

Robert pears

Terry oranges

Lisa peaches

⑦   sed stands for Stream Editor  它有效地使我们能够搜索和替换我们的数据。

sed <expression> [path]
  
A basic expression is of the following format:

s/search/replace/g

第一个s代表替代，并指定要执行的操作（还有其他的，但现在我们将保持简单），然后是第一个/和第二个/之间的内容代表我们要找的地方，第二个斜线与第三个斜线之间代表的是要取代的内容。末尾的g代表全局，是可选的。如果我们省略它，那么它只会替换每行上的第一个搜索实例。使用G选项，我们将替换每行上的每一个搜索实例。

sed 's/oranges/bananas/g' mysampledata.txt

Fred apples 20

Susy bananas 5 原来是oranges

Mark watermellons 12

Robert pears 4

Terry bananas 9   原来是oranges

Lisa peaches 7

Susy bananas 12   原来是oranges

需要注意的是，SED并不识别单词，而是字符串。可以用es替换oranges，你会明白我的意思。搜索词实际上也被称为正则表达式，它是定义模式的一种方法。（类似于通配符我们看7节）。

还要注意，我们的表达式包含在单引号中。我们这样做是为了使它包含在命令行中具有特殊含义的任何字符不受命令行的解释和执行，而是传递给SED。
 
⑧   uniq stands for unique  它的工作是从数据中删除重复的行。然而，一个限制是这些行必须相邻（即一个接一个）。（有时情况并非如此，但我们会看到一种方法，我们可以在第11节管道和重定向）中解决这个问题。

uniq [options] [path]

我们的示例文件在软件更新后有一些错误的输出，所以使用uniq来进行修复

cat mysampledata.txt

Fred apples 20

Susy oranges 5

Susy oranges 5

Susy oranges 5

Mark watermellons 12

使用uniq mysampledata.txt

Fred apples 20

Susy oranges 5

Mark watermellons 12

⑨  tac实际上是反向的cat。作用是给定的数据将打印最后一行，直到第一行。

tac mysampledata.txt

Betty limes 14

Oliver rockmellons 2

Greg pineapples 3

Anne mangoes 7

Mark grapes 39

Susy oranges 12

Lisa peaches 7
