<html><body><a href="http://vim.sourceforge.net/tip_view.php?tip_id=24">VimTip 24: changing the default syntax highlighting</a>
改变默认语法高亮

     Here are some pointers to the vim documentation.  Notice that the mechanism is different in vim 6.0 and vim 5.x.
    这有一些vim文档的指导。注意其中vim6.0和5.x版本的构架区别。
1. I want *.foo files to be highlighted like HTML files.
1.我希望*.foo 文件按照HTML文件进行语法高亮。
<b>:help new-filetype</b>  http://www.vim.org/html/autocmd.html#new-filetype

2. I want to define a syntax file for *.bar files.  Read the above and also
2. 我希望定义一个*.bar语法高亮文件。请参考上边文件
<b>:help mysyntaxfile</b>  http://www.vim.org/html/syntax.html#mysyntaxfile

3. I want to make a few changes to the existing syntax highlighting.  Depending on the x in 5.x, either read the above and page down a few screens, or you may be able to skip right to
3. 我希望对已有的语法高亮文件进行一些改变。在5.x环境下的x，阅读以上的文件和下文，或者直接跳到
<b>:help mysyntaxfile-add</b>  http://www.vim.org/html/syntax.html#mysyntaxfile-add

4. I want to change some of the colors from their defaults.  Again, read
4.我想改变默认语法高亮的颜色配置。请读：

<b>:help mysyntaxfile </b> http://www.vim.org/html/syntax.html#mysyntaxfile


Technorati Tags: <a href="http://technorati.com/tag/VI" rel="tag">VI</a>, <a href="http://technorati.com/tag/EDITOR" rel="tag">EDITOR</a></body></html>