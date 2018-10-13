<html><body><div><a href="http://vim.sourceforge.net/tip_view.php?tip_id=2">VimTip 2: easy edit of files in the same directory</a>
<span style="font-style:italic;">＃如何方便的编辑相同文件夹下的文件</span>
It was often<span style="text-decoration:underline;"> frustrating ＃挫败</span>
when I would open a file deep in the code tree and then realize I wanted to open another file in that same directory.<span style="font-style:italic;">
＃如果这样的话的确很烦 </span>
Douglas Potts taught me a nice way to do this. Add the following snipit to your vimrc:
<span style="font-style:italic;">＃Douglas高手指点说：</span>

" Edit another file in the same directory as the current file
" uses expression to extract path from current file's path
" (thanks Douglas Potts)
if has("unix")
map ,e :e  . "/"  /&gt;else
map ,e :e  . "\"  /&gt;endif
<span style="font-style:italic;">#在配置文件里加这么一段</span>

Then when you type ,e in normal mode you can use tab to complete to the file. You can also expand this to allow for spitting, etc. Very very nice.
<span style="font-style:italic;">#当你敲“,e”的时候，就可以用Tab来选你想编辑的文章咯</span>

<span style="font-weight:bold;">p.s. </span>为什么不用类似filetree或者winmanager这样的plugin呢？方便的很啊!另外vim官方网站本条tip下的评论还是有点意思的～感兴趣自己刨哈！


</div></body></html>