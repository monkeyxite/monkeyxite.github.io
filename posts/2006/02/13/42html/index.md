<html><body><a href="http://vim.sourceforge.net/tip_view.php?tip_id=31">VimTip 31: Find and Replace</a>
查找替换

To find and replace one or more occurences of a given text pattern with a new text string, use the s[ubstitute] command.
为了查找替换文中出现过的一个或多个文本串，使用s命令
There are a variety of options, but these are what you most probably want:
有很多可选的变量，看看什么是你最需要的：
<b>:%s/foo/bar/g   </b>        find each occurance of 'foo' and replace it with 'bar' without asking for confirmation
<b>                                      </b>不确认替换每一个foo为bar<b>
:%s/foo/bar/gc  </b>        find each occurance of 'foo' and replace it with 'bar' asking for confirmation first
                                                首次向用户确认并替换每一个foo为bar
<b>:%s//bar/gc  </b>    find (match exact word only) and replace each occurance of 'foo' with 'bar'
                                               将一个词foo替换为bar
<b>:%s/foo/bar/gci </b>        find (case insensitive) and replace each occurance of 'foo' with 'bar'
                                                大小写不敏感替换foo为bar
<b>:%s/foo/bar/gcI  </b>       find (case sensitive) and replace each occurance of 'foo' with 'bar'
                                                大小写敏感替换foo为bar

NB: Without the 'g' flag, replacement occurs only for the first occurrence in each line.
NB: 没有g选项的话，仅仅替换每行的第一个匹配项
For a full description and some more interesting examples of the substitute command refer to
想知道替换详细的解释和一些有趣的例子请参考
<b>:help substitute</b>

See also:
或者：
<b>:help cmdline-ranges
:help pattern
:help gdefault</b>


Technorati Tags: <a href="http://technorati.com/tag/VI" rel="tag">VI</a>, <a href="http://technorati.com/tag/EDITOR" rel="tag">EDITOR</a></body></html>