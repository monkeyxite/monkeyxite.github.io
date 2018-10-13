<html><body><div><br><a href="http://vim.sourceforge.net/tip_view.php?tip_id=3">VimTip 3: use vim to quickly compile java files</a><br>＃快速编译java<br><br>For a number of years I used vim on an SGI box.<br>#老外的电脑品种那叫个多啊，这里的SGI box也是其中的一种<br>When I left my job at SGI I went to a company that developed on PCs. <br>＃PC基本上是大白菜级别的玩意<br>For 2 years I used IDEs. I was unhappy. I was <span style="text-decoration:underline;">frustrated. ＃失落，挫败</span>，怎么还没记住这词啊？<br>I couldn't figure out why. (Beyond my machine crashing twice a day.)<br>＃大白菜老是要坏，整的特郁闷<br>Finally I upgraded to windows 2000 (kind of stable!) and started using vim as an IDE. All was good.<br>＃还好，用了稳定的win2000。译者注：m$里算是稳定的win2000，艾，帮他加个<br> is how you use vim to compile your java:<br>＃配置开发java的环境<br>1.While
I'm sure this works with javac, javac is slow slow slow. So download
the Jikes complier first. (Jikes is from ibm, search on google for
jikes and you will find it..available on most platforms.)<br>#javac太烂了，用ibm的jikes吧～<br>2.Add the following to your vimrc: <br> set makeprg=jikes -nowarn -Xstdout +E <br> set errorformat=%f:%l:%c:%*\d:%*\d:%*\s%m <br>＃加上边两行进vimrc<br>3.
When you are editing a java file type :make and it will compile the
current file and jump you to the first error in the file (if any). Read
":help quickfix" for how to move between errors.<br>＃当你编辑一个java文件时，:make 会编译当前文件，并且跳转到第一个错误的地方。想知道怎#么在错误中跳来跳去嘛？看:help quicktext<br>To
setup your classpath environment either launch gvim from a shell that
has your classpath/path setup or use the "let" command to configure it
in your vimrc.<br>#设定classpath环境……<br><br>其实java俺不懂，有空汇报一下我的python在vim中的设定<br><br><br></div></body></html>