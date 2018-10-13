<html><body><a href="http://vim.sourceforge.net/tip_view.php?tip_id=32">VimTip 32: Write your own vim function(scripts)</a>
编写自己的vim函数

compare to C and shell(bash), herein is some vim specifics about vim-script:
相对于C和shell（bash）编程，这里有些vim脚本的细节要注意：
1. A function name must be capitalized.
1. 函数名必须大写
  hex2dec is invalid
  Hex2dec is valid
  hex2dex是非法的
  Hex2dec是合法的
  while in c and shell(bash), both lowercase and uppercase is allowed.
  但是在C或bash shell中，无论大小写都是可以的。
2. how to reference the parameters
2.如何传递参数
<blockquote>   fu! Hex2dec(var1, var2)
   let str=a:var1
   let str2=a:var2
</blockquote>   you must prefix the parameter name with "a:", and a:var1 itself is read-only
  你必须在参数前加前缀a:，并且a:var1是只读的
  in c, you reference the parameter directly and the parameter is writable.
  在C中，你直接调用参数并且参数是可读的
3. how to implement variable parameter
3. 如何执行变量
<blockquote>   fu! Hex2dec(fixpara, ...)
</blockquote>     a:0 is the real number of the variable parameter when you invoke the function, with <span style="font-weight:bold;">:Hex2dec("asdf", 4,5,6), a:0=3, and a:1=4 a:2=5 a:3=6</span>
    当调用函数，a:0 是实数变量
  you can combine "a:" and the number to get the value
  你可以混合“a:"和数字来取得函数值
<blockquote>   while i
     exe "let num=a:".i
     let i=i+1
   endwhile
</blockquote>  in c, the function get the real number by checking the additional parameter such as printf family, or by checking the special value such as NULL
  c中，函数取值是通过检验额外得参数比如printf族，或者检测特定得值是否为空
4. where is the vim-library
4.vim的库在哪？
 yes, vim has its own function-library, just like *.a in c
 <span style="font-weight:bold;">:help functions</span>
 是的，vim有它自己的函数库，就像c语言中的*.a文件
 <span style="font-weight:bold;">:help functions</span>
5. can I use += or ++ operator?
5.我可以使用+=或者++这样的操作符吗？
 Nop, += and ++ (and -=, -- and so on)operator gone away in vim.
 遗憾的是vim没有类似+=和＋＋这样的操作符（-=,--这些也是）
6. How can I assign a value to a variables and fetch its value?
6.如何分配变量置并取取其值呢？
<blockquote><a>   let var_Name=value</a>
<a>   let var1=var2</a>
<a></a></blockquote><a>   like it does in c, except you must use <span style="font-weight:bold;">let</span> keyword
 除了必须用关键字<span style="font-weight:bold;">let</span>以外，就像在c中做的一样。
7. Can I use any ex-mode command in a function?
7. 我可以在ex模式下调用函数吗？
 As I know, yes, just use it directly, as if every line you type appears in the familar <span style="font-weight:bold;">: </span>
 据我所知，是的，可以直接用，就像每行都是你在熟悉的<span style="font-weight:bold;">：</span>后输入的一样
8. Can I call a function recurse?
8. 可以使用递归调用吗？
 Yes, but use it carefully to avoid infinte call.
 可以，但是要小心，避免无穷调用！
9. Can I call another function in a function?
9. 可以在函数中调用函数吗？
 Course, like C does.
 当然，就像C一样
10. Must I compile the function?
10. 我必须编译函数吗？
  No, you needn't and you can't, just <span style="font-weight:bold;">:so script_name</span>, after this you can call the function freely.
  不，你没必要也不能，仅仅<span style="font-weight:bold;">:so script_name</span>，之后就可以自由调用该函数了
11. Is it has integer and char or float data type?
11. 有整型，字符，浮点这样的数据类型吗？
  No, like perl, vim script justify the variable type depend upon the context
  没有，就像perl，vim脚本自动根据变量值调整变量类型
</a><blockquote><a>   :let a=1</a>
<a>   :let a=a."asdf"</a>
<a>   :echo a</a>
<a></a></blockquote><a>   you'll get `1asdf'
  将得到 </a>`1asdf'<blockquote><a>   :let a=1</a>
<a>   :let a=a+2</a>
<a>   :echo a</a>
<a></a></blockquote><a>   you'll get 3
  </a>将得到 3
<a>   But it differs from perl.
  但是它和perl有区别
12. Must I append a <span style="font-weight:bold;">`;'</span> in every statement?
  必须在每一句后边加<span style="font-weight:bold;">';'</span>吗？
  No, never do that.
  不，没必要
  ; is required in C, and optional in shell for each statement in a alone line.
  ；在C是必须的，在shell中一行中的每一句是可选的
  But is forbidden in vim.
  但是在vim是禁止的
  if you want combine servals statement in one single line, use <span style="font-weight:bold;">`|'</span>.
  如果想在单行里边写多句，使用<span style="font-weight:bold;">‘|'</span>
  Take your mind that every statement appears in function should be valid in ex-mode(except for some special statement).
  谨记除少数特殊声明外，函数中每一句都可以在ex模式下合法可用
</a>

Technorati Tags: <a href="http://technorati.com/tag/vi" rel="tag">vi</a>, <a href="http://technorati.com/tag/editor" rel="tag">editor</a>
<a href="http://technorati.com/tag/editor" rel="tag"></a></body></html>