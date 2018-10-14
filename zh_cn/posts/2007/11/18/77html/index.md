<html><body><div><span style="font-weight:bold;">友好的界面</span><span style="font-weight:bold;">设计</span>方法

因为写的模板是标准的 XHTML，所以我们可以直接用浏览器打开 Kid/Genshi 模板文件。这很重要而且很有用，可以保证你的模板在浏览器中看起来美观。

你可以从中观查你的样式表、JavaScript脚本、以及应该出现动态内容的部分，是不是同你设想的一样。

有时候，当你直接浏览模板文件或执行后的模板文件时，它们可能不能正确的链接到它们的样式表文件。要避免这个，你可以使用 href 标识要浏览的模板、使用 py:attrs 处理执行后的页面。例如：

<blockquote></blockquote>

这样再在浏览器中查看模板的话，浏览器只会去查找 href 属性，这样的话样式表就会正确的被载入了。</div></body></html>