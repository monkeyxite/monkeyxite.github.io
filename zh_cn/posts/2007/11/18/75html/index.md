<html><body><div><big></big><big>介绍：</big>
<ul><li>ipython是什么？</li><li>为什么要用它？</li></ul><big>标准的python interpreter</big>
标准的python interpreter对于python guy来说一定是特有分量的一个常备工具，因为：
<ul><li>用户可以马上输入代码看到结果</li><li>自省
</li><li>尽管很有用可是在实际的使用中还是有些地方可以改进！</li></ul><big>ipython 的目标：</big>
<ol><li>提供一个更好用的python interactive shell</li><li>可嵌入的interpreter
</li><li>提供一个框架可以在不同操作系统将pythono作为一个底层语言的基本环境
</li></ol><big></big><big>Magic命令系统
</big>
使ipyothon与众不同的特性
<ul><li>以%开头的行认为恶事magic命令</li><li>一般的shell比如ls，mkdir等均为magic命令</li><li>%alias 命令可以建新的别名</li><li>automagic模式打开后，%都不需要。在把名利提交给python interpreter都会自动分析是否是在magic命令的list中</li><li>%magic 看 关于magic命令的更多信息</li></ul>Tab补全
很有用，很多场合都能调用此功能
<ul><li>命令补全</li><li>变量名补全</li><li>object. 可以对象属性补全</li><li>一些场合可以自动补全文件或目录</li></ul>不仅如此，egular and menu completion modes are supported. The default    is regular, but can easily be changed in the config file
历史
<ul><li>不同session 和每个用户配置文件都有</li><li>%hist显示最近历史</li><li>-n 选项可以上翻n条历史</li><li>可以告诉%hist显示特定行</li></ul>一些有用的细节
<ul><li>历史一般都存储在 In 的list里</li><li>输出 存储在 Out 的list里</li><li>最后3个命令 分别为 _i,_ii,_iii</li><li>最后3个输出 分别为 _, __, ___<script type="text/javascript" src="http://ei.appspot.com/tinymce/themes/advanced/langs/zh.js"></script><script type="text/javascript" src="http://ei.appspot.com/tinymce/plugins/wordpress/langs/zh.js"></script></li></ul><blockquote>看看例子：
In [1]: True == False
Out[1]: False

In [2]: print "hello world"
hello world

In [3]: %hi
%hist     %history

In [3]: %hist
1: True == False

2: print "hello world"

In [4]: In
Out[4]: ['\n', 'True == False\n', 'print "hello world"\n',
       'ipmagic("%hist ")\n', 'In\n']

In [5]: Out
Out[5]:
{1: False,
4: ['\n', 'True == False\n', 'print "hello world"\n',
       'ipmagic("%hist ")\n', 'In\n', 'Out\n'],
5: }

In [6]: print _i, _ii, _iii, _, __, ___
Out
In
ipmagic("%hist ")
{1: False, 4: ['\n', 'True == False\n', 'print "hello world"\n',
        'ipmagic("%hist ")\n', 'In\n', 'Out\n',
        'print _i, _ii, _iii, _, __, ___\n'], 5: {...}} ['\n',
        'True == False\n', 'print "hello world"\n',
        'ipmagic("%hist ")\n', 'In\n', 'Out\n',
        'print _i, _ii, _iii, _, __, ___\n'] False

</blockquote>编辑
<ul><li>支持行编辑，默认为vi键绑定。可以按 ESC 允许行被编辑</li><li>允许方便编辑所以代码</li><li>%edit调出 环境变量EDITOR定义的编辑器</li><li>%edit star stop 可以对某一区域编辑</li></ul>编辑例子
<blockquote> In [4]: hist
   1:
   class A:
       def __init__(self, start, end):
           """Some comment here."""

   2: a = 1
   3: b = 2
   4: c = 0
</blockquote>


<span style="font-weight:bold;">%edit</span>
   Will open up an empty editor
<span style="font-weight:bold;">%edit 2 4</span>
   Will open an editor containing lines 2 and 4
<span style="font-weight:bold;">%edit 1</span>
   Will open up the class definition
<span style="font-weight:bold;">%edit 1:4</span>
w
   Will open up the editor with lines 1, 2 and 3


会话和日志
每次使用后会话都有记录。并且可以重放会话快速恢复到上次会话的最后状态

开始记录日志可以使用 -log 或 -logfile  在命令行或者使用%logstart在interpreter。%logstate可以显示当前log的状态

%logoff可以暂停记录，%logon恢复

继续某次会话可以通过命令行使用 -logfile 

对象自省
自省可以像标准python那样
？是个快捷键
例子
<blockquote>In [2]: sys.path?
Type:           list
Base Class:     
String Form:    ['', '/usr/bin', '/disk2/ag/common',
                '/usr/lib/python24.zip', '/usr/lib/python2.4',
                '/usr/lib/pyt &amp;lt;...&amp;gt; 2.4/site-packages/Numeric',
                '/usr/lib/python2.4/site-packages/gtk-2.0',
                '/home/dstanek/.ipython']
Namespace:      Interactive
Length:         13
Docstring:
    list() -&amp;gt; new list
    list(sequence) -&amp;gt; new list initialized from sequence's items
</blockquote>
<blockquote>In [1]: class C(object):
   ...:     a = "a string"
   ...:     def f(self, name, value):
   ...:         """my docstring here"""
   ...: 

In [2]: C.a?
Type:           str
Base Class:     
String Form:    a string
Namespace:      Interactive
Length:         8
Docstring:
    str(object) -&amp;gt; string

    Return a nice string representation of the object.
    If the argument is a string, the return value is the
    same object.


In [3]: ?C.f
Type:           instancemethod
Base Class:     
String Form:    
Namespace:      Interactive
File:           /mnt/home/dstanek/
Definition:     C.f(self, name, value)
Docstring:
   my docstring here

</blockquote>
其他技巧
<ul><li>集成调试器</li><li>集成profiler</li><li>Python jobs can be run in the background in a thread.</li><li>支持配置文件</li></ul>结论

<p><b>It's a good thing</b> and is available at
   http://ipython.scipy.org/</p><p>A sprint to add other cool things may be a useful exercise.</p><b>To set ipython to be the default:</b><p>Python honors the environment variable PYTHONSTARTUP and will execute
   at startup the file referenced by this variable. If you put at the end
   of this file the following two lines of code:</p><pre>    import IPython
   IPython.Shell.IPShell().mainloop(sys_exit=1)
   </pre>

</div></body></html>