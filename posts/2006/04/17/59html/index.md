<html><body><span class="postbody">原本打算使用eclipse，无奈内存有限，所以用vim投身java。以下为摘录:

<big></big><big>配置篇</big>
</span><div style="text-align:left;"><ul><li><span class="postbody">启用或者禁用java在用户输入括号后自动提示参数 </span></li></ul><blockquote><span class="postbody">let g:vjde_cfu_java_para=0 </span>
<span class="postbody"></span></blockquote><ul><li><span class="postbody"> 启用或者禁用 用户在用&lt;c-x&gt; &lt;c-u&gt;时显示预览 </span></li></ul><blockquote><span class="postbody">let g:vjde_show_preview=0 </span>
<span class="postbody"></span></blockquote><ul><li><span class="postbody"> 启用或者禁用 在用户输入 .  时自动提示后面的部分 </span></li></ul><blockquote><span class="postbody">let g:vjde_cfu_java_dot=0 </span>
<span class="postbody"></span></blockquote><ul><li><span class="postbody"> 启用或才禁用 使用一个图形化的提示窗口.(不推荐,太难看) </span></li></ul><blockquote><span class="postbody"> let g:vjde_preview_gui=1 </span>
<span class="postbody"></span></blockquote><ul><li><span class="postbody"> 以下做为c++使用 </span></li></ul><blockquote><span class="postbody"> let g:vjde_iab_exts='.cpp;.c;.vim;.rb' </span>
<span class="postbody"></span></blockquote><span class="postbody">  </span><ul><li><span class="postbody"> 对指定名字的窗口进行调整,如下表示: </span></li><li><span class="postbody"> 对以__Tag_List__为标题的窗口,在垂直方向变化,进入时40宽,离开后变成20宽 </span></li><li><span class="postbody"> 对以.prj为标题的窗口,在垂直方向变化,进入时24宽,离开后变为1 </span></li></ul><blockquote><span class="postbody"> let g:floatingwindows=
"'__Tag_List__',1,40,20;'.prj',1,24,1;'.vimproject',1,24,1;"</span></blockquote>
<div style="text-align:center;">   <p><img src="http://mfrost.typepad.com/photos/uncategorized/hamster_stretch.jpg" alt="Photo"></p>   </div></div><big></big><big>工程创建篇

</big><span class="postbody">在开始写一个java程序的时候,如果是一个简单程序,一切都无所谓.如果是一个比较大的项目.需要工程支持.在vjde的配合下,可以这样做.

</span><ul><li><span class="postbody"> 创建目录 project1 在你的工作目录上. </span></li></ul><ul><li><span class="postbody"> 打开 vim 并切换到 project1 </span></li></ul><blockquote><span class="postbody"> :cd project1 </span>
<span class="postbody"></span></blockquote><span class="postbody">  </span><ul><li><span class="postbody"> 存储一个工程模板</span></li></ul><blockquote><span class="postbody">:Vjdesave .vjde </span>
</blockquote><span class="postbody">  </span><ul><li><span class="postbody">在.vjde里面,会有一个参数,你可自行打开并修改.如我的一个配置文件中，编译时的输出文件夹 </span></li></ul><blockquote><span class="postbody">let g:vjde_out_path='classes' </span>
<span class="postbody"></span></blockquote><ul><li><span class="postbody">源代码目录 </span></li></ul><blockquote><span class="postbody">let g:vjde_src_path='src' </span>
<span class="postbody"></span></blockquote><ul><li><span class="postbody">编译时使用的路径,用于代码补全时类查找,也是编译时使用,最好把输出文件夹加在此处. </span></li></ul><blockquote><span class="postbody">let g:vjde_lib_path='lib/servlet.jar:lib/images.jar:class' </span>
<span class="postbody"></span></blockquote><ul><li><span class="postbody">如果有jsp类型文件,放在这里 </span></li></ul><blockquote><span class="postbody">let g:vjde_web_app='webapps' </span>
<span class="postbody"></span></blockquote><ul><li><span class="postbody">测试源代码路径 </span></li></ul><blockquote><span class="postbody">let g:vjde_test_path='test' </span>
<span class="postbody"></span></blockquote><ul><li><span class="postbody">系统中java命令的命令名字,默认在windows下为javaw,linux下java,理论上可以修改成为jikes </span></li></ul><blockquote><span class="postbody">let g:vjde_java_command='java' </span>
<span class="postbody"></span></blockquote><span class="postbody">  </span><ul><li><span class="postbody">修改完成后,你可以用 </span></li></ul><blockquote><span class="postbody">:Vjdeload .vjde </span>
<span class="postbody"></span></blockquote><ul><li><span class="postbody">或者这样加载</span></li></ul><blockquote><span class="postbody">:source .vjde </span>
</blockquote><div style="text-align:center;">   <p><img src="http://mfrost.typepad.com/photos/uncategorized/akagami4jm.jpg" alt="Photo"></p>   </div><span class="postbody">
<big></big><big>编程开始篇

</big></span><span class="postbody">使用vjde,就可以使用已经存在的模板进行创建你的程序:
在图形界面下,可以从菜单Vim JDE-&gt;Wizard-&gt;New Class(with main) 开始创建一个你自己的类.它还包括一个main 方法.
vjde提供了很多的代码模板可以使用,第一个模板被定义为在当前的位置添加模板的全部内容.
同时,你可以自己定义你自己的模板为你的每一类文件.它们都会被列在 Vim JDE-&gt;Wizzard的子菜里面.
你只需要把自己定义的模板放到 ~/.vim/vjde/java.vjde 即可被当作java类型文件的模板 ~/.vim/vjde/cpp.vjde 即被当作cpp类型文件的模板
关于文件类型,打开一个文件,然后用
:set filetype
即可知道当前文件的类型.


高级技巧: 各类模板是可以互相引用的.但是,我不作递归检查.

</span><blockquote><span class="postbody">if !exists('g:vjde_iab_refs') </span>
<span class="postbody"> let g:vjde_iab_refs={} </span>
<span class="postbody">endif </span>
<span class="postbody">if !has_key(g:vjde_iab_refs,'jsp') </span>
<span class="postbody"> let g:vjde_iab_refs['jsp']=[ 'java', 'html' ] </span>
<span class="postbody">endif </span>
<span class="postbody">if !has_key(g:vjde_iab_refs,'cpp') </span>
<span class="postbody"> let g:vjde_iab_refs['cpp']=[ 'c' ] </span>
<span class="postbody">endif </span>
<span class="postbody"></span></blockquote><span class="postbody">
即是说 jsp引用 java 和 html的模板
cpp引用了c的模板.
当然,也可定义自己的引用.
</span><div style="text-align:center;">   <p><img src="http://mfrost.typepad.com/photos/uncategorized/bunny.jpg" alt="Photo"></p>   </div><span class="postbody"><big></big><big>编程日常工作篇

</big></span><ul><li><span class="postbody">代码补全 </span></li></ul><blockquote><span class="postbody">   在默认的情况下,在gui环境下,用户在任何时候按下&lt;c-space&gt;即可进行代码提示. </span>
<span class="postbody"> </span>
<span class="postbody">   如果要改变这个定义,请定义 g:vjde_completion_key </span>
<span class="postbody">   let g:vjde_completion_key="&lt;c-l&gt;" </span>
<span class="postbody"></span></blockquote><ul><li><span class="postbody">添加引用的包.</span></li></ul><blockquote><span class="postbody">通常,我们编辑的时候,比如,使用了 Vector numbers; </span><span class="postbody"></span>
<span class="postbody">我们已经知道了 Vector 在 java.util里,或者一些类,我们不知道在什么地方,这个时候, 把Shu标话在 Vector 上, 在通常模式下,使用 &lt;leader&gt;ai  </span>
<span class="postbody">在我系统上,是 \ai 这个组合.即可自动添加 java.util.Vector 到你的 文件上. 如果有多个,则提示你选择一个你要使用的. </span>
<span class="postbody">或者使用使用菜单 Vim JDE-&gt;Add import </span>
<span class="postbody"></span></blockquote><span class="postbody"> </span><ul><li><span class="postbody">如果在编译时发现一个错误,就是无法找到一个类的定义,这时,可以使用: </span></li></ul><blockquote><span class="postbody">Vim JDE-&gt;fixerror with import  来把当前这个没有添加的类添加到文件中来. </span>
<span class="postbody">这个,必须使用 :make 或者 :Vjdec 编译时才能使用. </span>
<span class="postbody"></span></blockquote><span class="postbody"> </span><ul><li><span class="postbody">对编译时提示的没有捕获的异常,也可以根据需要来使用 Vim JDE-&gt;fixerror with  try/catch , 这会把当前的错误行包含在一个适当的try-catch块里. </span></li></ul><blockquote><span class="postbody">使用 Vim JDE-&gt;fixerror with throws 则把这个异常定义为 throws ,添加到函数定义上. </span>
<span class="postbody"></span></blockquote><span class="postbody"> </span><ul><li><span class="postbody"> 重载方法 Vim JDE-&gt;Source-&gt;override methods... </span></li></ul><blockquote><span class="postbody">列出父类的方法,选择重载 </span>
<span class="postbody"></span></blockquote><ul><li><span class="postbody"> 实现接口 Vim JDE-&gt;Source-&gt;Implement interfaces... </span></li></ul><blockquote><span class="postbody">列出类的接口中要实现的方法,用户选择实现. </span>
<span class="postbody"></span></blockquote><ul><li><span class="postbody">生成构造函数 Vim JDE-&gt;Soruce-&gt;Generate Con... </span></li></ul><blockquote><span class="postbody">把已经编译过的类中每一个成员变量做为参数,生成一个构造函数. </span>
<span class="postbody"></span></blockquote><ul><li><span class="postbody"> 添加 Singleton 接口 Vim JDE-&gt;Source-&gt;Add single... </span></li></ul><blockquote><span class="postbody">在当前位置为类生成一个Singlton接口.包括一个私有构造函数,一个getInstance()方法,一个实例变量. </span>
<span class="postbody"></span></blockquote><span class="postbody"> </span><ul><li><span class="postbody"> </span><span class="postbody">把变量变成成员变量,局部变量,静态变量的小工具. </span></li></ul><blockquote><span class="postbody">Vim JDE-&gt;Source-&gt;Extract .... </span>
<span class="postbody"></span></blockquote><span class="postbody"> </span><ul><li><span class="postbody">把引用的要排序的包选中,然后,执行此命令</span></li></ul><blockquote><span class="postbody"> Vim JDE-&gt;Source-&gt;Sort import ... </span>
<span class="postbody"></span></blockquote><div style="text-align:center;">   <img src="http://mfrost.typepad.com/photos/uncategorized/tanjaaskani_2.jpg" alt="Photo">  </div>
<span class="postbody">
<big></big><big>编程提高篇
</big></span>
<span class="postbody">通常,在我们写代码的时候,我们会写很多重复的代码,如一个数据循环结构,一个Vector的遍历,一个System.out.println() , 甚至很多很多的,每天都要写很多遍的代码.

怎么办? vjde 提供了一个方法.

vjde 提供了一个iab的扩展.目前,是在输入模式下输入 &lt;c-j&gt;即激活这个功能.

在使用这个功能前.你可以定义好自己的要使用的一个模板:如果要用java 使用,存储为 ~/.vim/vjde/java.iab, 为c++使用,存储为~/.vim/vjde/cpp.iab , 在 .iab 前是文件类型.你可以为你使用的每一种文件类型创建一种模板

如,一个java 的模板按如下定义:
</span><blockquote><span class="postbody">template out ; system out </span>
<span class="postbody">body  </span>
<span class="postbody">System.out.println(|); </span>
<span class="postbody">endt </span>
<span class="postbody">template err; Sysetm.err </span>
<span class="postbody">body </span>
<span class="postbody">System.err.println(|); </span>
<span class="postbody">endt </span>
<span class="postbody">template fa ; for loop for array </span>
<span class="postbody">body </span>
<span class="postbody">for ( int i = 0 ; i &lt; |.length ; i++) { </span>
<span class="postbody">} </span>
<span class="postbody">endt </span>
<span class="postbody"></span></blockquote><span class="postbody">

这样,当你输入
</span><blockquote><span class="postbody">          out&lt;c-J&gt; </span>
<span class="postbody"></span></blockquote><span class="postbody">时,自动把本行展开成为:
</span><blockquote><span class="postbody">          System.out.println(); </span>
<span class="postbody"></span></blockquote><span class="postbody">并把光标放在第一个 | 的位置.

更多的定义和使用,请参考
</span><blockquote><span class="postbody">:h vjde-iabbr</span></blockquote>


Technorati Tags: <a href="http://technorati.com/tag/vi" rel="tag">vi</a>, <a href="http://technorati.com/tag/java" rel="tag">java</a>, <a href="http://technorati.com/tag/jde" rel="tag">jde</a>, <a href="http://technorati.com/tag/vjde" rel="tag">vjde</a>, <a href="http://technorati.com/tag/note" rel="tag">note</a></body></html>