<html><body><div><a href="http://vim.sourceforge.net/tip_view.php?tip_id=22">VimTip 22: handle common typos for :commands</a>
命令模式下的等价录入

I frequently hold the shift key for too long when typing, for instance<span style="font-weight:bold;"> :wq</span>, and end up with <span style="font-weight:bold;">:Wq</span>. Vim then whines "<span style="font-weight:bold;">Not an editor command: Wq</span>"
我时常在输入的时候按住shift键，比如:wq当以:Wq录入时，Vim会提示“无<span style="font-weight:bold;">:Wq</span>命令”的错误
In my .vimrc, I have taught vim my common typos:
在我的.vimrc配置中，我讲设置如下等价录入
<span style="font-weight:bold;">command! Q quit</span>
<span style="font-weight:bold;">command! W write</span>
<span style="font-weight:bold;">command! Wq wq</span>
this one won't work, because :X is already a built-in command command<span style="font-weight:bold;">! X xit</span>
如果不生效的话，那是应为:X已然是内置的命令<span style="font-weight:bold;">!X</span> <span style="font-weight:bold;">xit</span>了。


Technorati Tags: <a href="http://technorati.com/tag/VI" rel="tag">VI</a>, <a href="http://technorati.com/tag/EDITOR" rel="tag">EDITOR</a></div></body></html>