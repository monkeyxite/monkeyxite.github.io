<html><body><div class="tags"><a href="http://vim.sourceforge.net/tip_view.php?tip_id=5">VimTip 5: Quickly searching for a word</a>
快速单词搜索技巧

To search for a word under the cursor in the current file you can use either the "*" or "#" keys.
可以用“*”或“#”来搜索光标下的单词
The
"*" key will search for the word from the current cursor position to
the end of the file. The "#" key will search for the word from the
current cursor position to the top of the file.
“*”是下文搜索，“#”是上文搜索。
Note that the above two keys will search for the whole word and not the<span style="text-decoration:underline;"> partial </span>word. This is equivalent to using the  pattern in the search commands (/ and ?).
注意以上*和#两种用法同/ 和?的用法都是，用来查找整词而不是检索词是被包含在其中单词

To search for partial matches, you can use the "g*" and "g#" keysequence.
找检索词被包含在检索结果中单词 可以用g*和g＃

You can also use the mouse to search for a word.
同样可以用鼠标来搜索单词
This will only work in the GUI version of VIM (gvim) or a console version of VIM in an xterm which accepts a mouse.
当然实在gvim或支持鼠标的xterm类似的终端环境下
Also, the 'mousemodel' should be set to 'extend'. Add the following line to your .vimrc:
想用的话当然得扩展一下 。在配置文件中加：

<span style="font-weight:bold;">set mousemodel=extend</span>

To
search for a word under the cursor from the current cursor position to
the end of the file, press the shift key and click on the word using
the left mouse button. To search in the opposite direction, press the
shift key and click on the word using the the right mouse button.
这样就可以使用shift＋左键来搜索下文中光标下得单词咯，上文搜索是shift＋右键


To get more help on these, use
想多知道得话查帮助吧！
<span style="font-weight:bold;">:help *</span> <span style="font-weight:bold;">:help #</span> <span style="font-weight:bold;">:help g*</span> <span style="font-weight:bold;">:help g#</span> <span style="font-weight:bold;">:help <s></s></span> <span style="font-weight:bold;">:help <s></s></span>

My del.icio.us Tags
<ul><li><a href="http://del.icio.us/monkeyatblogger" rel="tag">vi</a></li> </ul></div></body></html>