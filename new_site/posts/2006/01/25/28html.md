<html><body><a href="http://vim.sourceforge.net/tip_view.php?tip_id=14">VimTip 14: Highlighting all the search pattern matches</a>
高亮显示所有搜索匹配项

To highlight all the search pattern matches in a file set the following option:
高亮显示所有搜索的匹配项可以通过命令
    <span style="font-weight:bold;">    :set hlsearch</span>

After this option is set, if you search for a pattern, all the matches in the file will be highlighted in yellow.
这样设定后高亮显示所有搜索的匹配项＃又唐僧了不是？！
To disable the highlighting temporarily, use the command
暂时废除高亮使用命令
<span style="font-weight:bold;">        :nohlsearch</span>

This command will remove the highlighting for the current search.The highlighting will come back for the next search.
命令可以取消当前搜索的高亮。下次搜索还会高亮
To disable the highlighting completely, set the following option:
废除高亮使用命令
     <span style="font-weight:bold;">   :set nohlsearch</span>

By default, the hlsearch option is turned off.
默认高亮搜索是关闭的＃我的是开启的，哈哈
To get more help on this option, use
想知道更多，请查阅帮助

<span style="font-weight:bold;">:help 'hlsearch'</span>
<span style="font-weight:bold;">:help :nohlsearch</span>


Technorati Tags: <a href="http://technorati.com/tag/VI" rel="tag">VI</a></body></html>