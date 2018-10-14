<html><body><a href="http://vim.sourceforge.net/tip_view.php?tip_id=6">VimTip 6: Using the % key</a>
使用％

The % key can be used
%是很有用的！

<ol><li>To jump to a matching opening or closing parenthesis, square bracket or a curly brace i.e. ([{}])</li><li>To jump to start or end of a C-style comment /* */.  </li><li>To jump to a matching #if, #ifdef, #else, #elif, #endif C  preprocessor conditionals.</li></ol><ol><li>找到匹配得括号</li><li>找到匹配得c语言风格注释/**/</li><li>找到匹配得c语言预处理块#if, #ifdef,#else, #elif, #endif </li></ol>To get more information about this, do
想知道更多，请查阅帮助：
          <span style="font-weight:bold;"> :help %</span>

The % key can be extended to support other matching pairs by modifying the "matchpairs" option.  Read the help on
当然，％也可以通过扩展来增加对其他匹配对得匹配查找，想知道请：
       <span style="font-weight:bold;">    :help matchpairs

</span> <div class="tags">My del.icio.us Tags<ul><li><a href="http://del.icio.us/monkeyatblogger" rel="tag">vi</a></li> </ul></div></body></html>