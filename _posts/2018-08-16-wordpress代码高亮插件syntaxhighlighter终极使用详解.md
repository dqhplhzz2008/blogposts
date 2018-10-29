---
ID: 3886
post_title: >
  WordPress代码高亮插件SyntaxHighlighter终极使用详解
post_name: 'wordpress%e4%bb%a3%e7%a0%81%e9%ab%98%e4%ba%ae%e6%8f%92%e4%bb%b6syntaxhighlighter%e7%bb%88%e6%9e%81%e4%bd%bf%e7%94%a8%e8%af%a6%e8%a7%a3'
author: 小奥
post_date: 2018-08-16 15:52:35
layout: post
link: >
  http://www.yushuai.me/2018/08/16/3886.html
published: true
tags: [ ]
categories:
  - Wordpress
---
插件名称：SyntaxHighlighter Evolved

插件作者：Viper007Bond, automattic

作者主页：http://www.viper007bond.com/wordpress-plugins/syntaxhighlighter/

插件类型：代码高亮

中文支持：支持

安装环境：WordPress2.7或以上版本，经过我自己的测试，在3.3和3.4上都可以正常运行

下载地址：点击这里下载最新版

SyntaxHighlighter Evolved基于开源的JS核心库：SyntaxHighlighter JavaScript package by Alex Gorbatchev二次开发扩展的。安装后只需简单设置一下，不用修改任何代码即可达到很好的效果。
功能特效

SyntaxHighlighter Evolved的功能特效如下：

代码高亮
支持Eclips、Emacs等多种样式，可搭配不同风格的主题
特色——显示工具条。右上角显示工具条，可以”查看源代码”、”复制源代码”、”打印源代码”。（只有第2版支持）
显示行号
长代码自动换行（只有第2版支持）
可以点击代码中的超文本链接
可以收缩代码框
高亮显示模式—某一行高亮
设置开始行号
自定义样式
<h2>使用方法</h2>
使用方法很简单。在发布文章时，在“HTML”编辑模式下（注意：不是CKEditor等富文本编辑模式；防止让这些富文本编辑器把代码转义了。），使用如下代码，把需要展示的代码包含起来即可：（注意：把前面的@符号去掉。）

[@java]这里写你的代码[/java]

[@css autolinks="false" classname="myclass" collapse="false" firstline="1" gutter="true" highlight="1-3,6,9" htmlscript="false" light="false" padlinenumbers="false" smarttabs="true" tabsize="4" toolbar="true" title="example-filename.php"]这里写你的代码[/css]

[@code lang="js"]这里写你的代码[/code]

[@sourcecode language="plain"]这里写你的代码[/sourcecode]

推荐使用这种方式。这种使用方式，见"最佳实践"

其实，在网上，搜“SyntaxHighlighter 使用方法”就会出现一堆结果，里面大多时对于这些使用方法的罗列。很少去讲解这些配置项的意思和说明。下面，我将针对这些配置进行详细说明。同时，针对这些配置的使用，我总结了SyntaxHighlighter使用方法的最佳实践。如果急于知道结果，可以直接查看“最佳实践”。
<h2>配置详解</h2>
代码样式配置
表-1-SyntaxHighlighter配置参数表
<table border="1">
<tbody>
<tr>
<th scope="col" width="70px">简码</th>
<th scope="col" width="55px">默认值</th>
<th scope="col">含义说明</th>
<th scope="col" width="60px">V2支持</th>
<th scope="col" width="60px">V3支持</th>
</tr>
<tr>
<td>lang</td>
<td>无</td>
<td>说明代码块是哪种语言？</td>
<td>支持</td>
<td>支持</td>
</tr>
<tr>
<td>autolinks</td>
<td>true</td>
<td>Toggle automatic URL linking. 是否自动将网址转换为链接。 默认转换。可以后台管理页面修改默认值。 <a href="http://alexgorbatchev.com/SyntaxHighlighter/manual/demo/auto-links.html" target="_blank" rel="noopener">示例：点击查看</a></td>
<td>支持</td>
<td>支持</td>
</tr>
<tr>
<td>classname</td>
<td>无</td>
<td>Add an additional CSS class to the code box. 允许你添加一个或多个自定义的样式。 默认没有。可以后台管理页面修改默认值。<a href="http://alexgorbatchev.com/SyntaxHighlighter/manual/demo/class-name.html" target="_blank" rel="noopener">示例：点击查看</a></td>
<td>支持</td>
<td>支持</td>
</tr>
<tr>
<td>collapse</td>
<td></td>
<td>Toggle collapsing the code box by default, requiring a click to expand it. Good for large code posts. 是否默认折叠代码段。如果折叠，这需要一个“点击”操作，才能展开。非常适合有大段代码的文章。默认不折叠。可以后台管理页面修改默认值。 <a href="http://alexgorbatchev.com/SyntaxHighlighter/manual/demo/collapse.html" target="_blank" rel="noopener">示例：点击查看</a></td>
<td>支持</td>
<td>支持</td>
</tr>
<tr>
<td>firstline</td>
<td>1</td>
<td>An interger specifying what number the first line should be (for the line numbering). 设置起始行的行号。<a href="http://alexgorbatchev.com/SyntaxHighlighter/manual/demo/first-line.html" target="_blank" rel="noopener">示例：点击查看</a></td>
<td>支持</td>
<td>支持</td>
</tr>
<tr>
<td>gutter</td>
<td></td>
<td>Toggle the left-side line numbering. 是否显示行号。默认显示。可以后台管理页面修改默认值。 <a href="http://alexgorbatchev.com/SyntaxHighlighter/manual/demo/gutter.html" target="_blank" rel="noopener">示例：点击查看</a></td>
<td>支持</td>
<td>支持</td>
</tr>
<tr>
<td>highlight</td>
<td>无</td>
<td>A comma-sperated list of line numbers to highlight. You can also specify a range. Example: 2,5-10,12 需要高亮显示并使用逗号分隔的行号。同时，也支持区间（开始行号-结束行号）。例如：2,5-10,12。 <a href="http://alexgorbatchev.com/SyntaxHighlighter/manual/demo/highlight.html" target="_blank" rel="noopener">示例：点击查看</a></td>
<td>支持</td>
<td>支持</td>
</tr>
<tr>
<td>htmlscript</td>
<td></td>
<td>Toggle highlighting any extra HTML/XML. Good for when you're mixing HTML/XML with another language, such as having PHP inside an HTML web page. The above preview has it enabled for example. This only works with certain languages. 是否高亮显示功能任何额外的HTML / XML。特别适合混合HTML/XML与另一种语言混合的情况下。如在HTML代码中含有部分PHP代码。注意，这仅仅适用于特定的语言。<a href="http://alexgorbatchev.com/SyntaxHighlighter/manual/demo/html-script.html" target="_blank" rel="noopener">示例：点击查看</a></td>
<td>支持</td>
<td>支持</td>
</tr>
<tr>
<td>light</td>
<td>false</td>
<td> Toggle light mode which disables the gutter and toolbar all at once. 是否显示高亮模式。默认是关闭。可以后台管理页面修改默认值。</td>
<td></td>
<td></td>
</tr>
<tr>
<td>padlinenumbers</td>
<td>off</td>
<td>Controls line number padding. 设置行号的格式化，前面是否补零。默认是关闭。可以后台管理页面修改默认值。</td>
<td>支持</td>
<td>支持</td>
</tr>
<tr>
<td>title</td>
<td>无</td>
<td>Sets some text to show up before the code. 设置文本的标题。默认没有。可以后台管理页面修改默认值。</td>
<td>不支持</td>
<td>支持</td>
</tr>
<tr>
<td>toolbar</td>
<td>false</td>
<td> Toggle the toolbar (buttons in v2, the about question mark in v3) 默认不显示。可以后台管理页面修改默认值。 <a href="http://alexgorbatchev.com/SyntaxHighlighter/manual/demo/toolbar.html" target="_blank" rel="noopener">示例：点击查看</a></td>
<td>支持</td>
<td>不支持</td>
</tr>
<tr>
<td>wraplines</td>
<td>false</td>
<td>Toggle line wrapping. 是否开启自动换行。可以后台管理页面修改默认值。</td>
<td>支持</td>
<td>不支持</td>
</tr>
<tr>
<td>smarttabs</td>
<td>true</td>
<td>Allows you to turn smart tabs feature on and off. <a href="http://alexgorbatchev.com/SyntaxHighlighter/manual/demo/smart-tabs.html">Click here</a> for a demo.智能制表符</td>
<td>支持</td>
<td>不支持</td>
</tr>
<tr>
<td>tabsize</td>
<td>4</td>
<td>Allows you to adjust tab size. <a href="http://alexgorbatchev.com/SyntaxHighlighter/manual/demo/tab-size.html">Click here</a> for a demo.制表符的长度。</td>
<td>支持</td>
<td>不支持</td>
</tr>
</tbody>
</table>
<h2>颜色主题</h2>
目前IT行业中，常用的语言有几十种；使用的开发环境也多种多样，比如开发Java的也许用Eclipse的比较多；但是在Linux下做C/C++开发的也许用Emacs等。见过这些开发环境的人都知道，这些开发环境的高亮模式、颜色等都是不一样的。习惯了Eclipse的人很难适应Emacs；反之亦然。SyntaxHighlighter考虑的很周全，她在内部直接继承了大概其中这样的颜色主题来供大家选择。大家可以在后台的管理页面轻松的选择自己喜欢的“颜色主题”来进行显示。“颜色主题”列表如下：（排名部分前后。呵呵）

Default
Django
Eclipse
Emacs
Fade to Grey
Midnight
RDark
None
<h2>语言别名</h2>
从事IT行业的朋友也许都知道，由于历史等原因，一个语言可能有好几个名字。比如JavaScript，微软山寨了个JScript；后来经过ECMA标准化之后，名字又称了ECMAScript；我们大家平时还简称成JS。这就给我们在使用SyntaxHighlighter的语言代号时，造成了一定的困难：不知道到底该用哪个名字才是“正确”的。

其实，这点SyntaxHighlighter也考虑到了。她通过“语言别名”的方式很好的解决了这个问题。
表-2-SyntaxHighlighter中“语言别名”和“语言代码”对应表
<table border="1">
<tbody>
<tr>
<th scope="col" width="26%">语言别名</th>
<th scope="col" width="26%">语言代码</th>
<th scope="col">说明</th>
</tr>
<tr>
<td>as3</td>
<td>as3</td>
<td rowspan="2">不知道是否支持AS2？</td>
</tr>
<tr>
<td>actionscript3</td>
<td>as3</td>
</tr>
<tr>
<td>bash</td>
<td>bash</td>
<td rowspan="2">竟然还支持Shell.</td>
</tr>
<tr>
<td>shell</td>
<td>bash</td>
</tr>
<tr>
<td>coldfusion</td>
<td>coldfusion</td>
<td rowspan="2"></td>
</tr>
<tr>
<td>cf</td>
<td>coldfusion</td>
</tr>
<tr>
<td>clojure</td>
<td>clojure</td>
<td></td>
</tr>
<tr>
<td>clj</td>
<td>clojure</td>
<td></td>
</tr>
<tr>
<td>cpp</td>
<td>cpp</td>
<td></td>
</tr>
<tr>
<td>c</td>
<td>cpp</td>
<td></td>
</tr>
<tr>
<td>c-sharp</td>
<td>csharp</td>
<td rowspan="2"></td>
</tr>
<tr>
<td>csharp</td>
<td>csharp</td>
</tr>
<tr>
<td>css</td>
<td>css</td>
<td></td>
</tr>
<tr>
<td>delphi</td>
<td>delphi</td>
<td rowspan="3">看来Delphi和Pascal确实有一腿啊！</td>
</tr>
<tr>
<td>pas</td>
<td>delphi</td>
</tr>
<tr>
<td>pascal</td>
<td>delphi</td>
</tr>
<tr>
<td>diff</td>
<td>diff</td>
<td></td>
</tr>
<tr>
<td>patch</td>
<td>diff</td>
<td></td>
</tr>
<tr>
<td>erl</td>
<td>erlang</td>
<td></td>
</tr>
<tr>
<td>erlang</td>
<td>erlang</td>
<td></td>
</tr>
<tr>
<td>fsharp</td>
<td>fsharp</td>
<td></td>
</tr>
<tr>
<td>groovy</td>
<td>groovy</td>
<td></td>
</tr>
<tr>
<td>java</td>
<td>java</td>
<td></td>
</tr>
<tr>
<td>jfx</td>
<td>javafx</td>
<td rowspan="2"></td>
</tr>
<tr>
<td>javafx</td>
<td>javafx</td>
</tr>
<tr>
<td>js</td>
<td>jscript</td>
<td rowspan="3">从这里可以看出，针对JavaScript的代码，写js行，写javascript行，甚至是微软的jscript都行。</td>
</tr>
<tr>
<td>jscript</td>
<td>jscript</td>
</tr>
<tr>
<td>javascript</td>
<td>jscript</td>
</tr>
<tr>
<td>latex</td>
<td>latex</td>
<td>Not used as a shortcode</td>
</tr>
<tr>
<td>tex</td>
<td>latex</td>
<td></td>
</tr>
<tr>
<td>matlab</td>
<td>matlabkey</td>
<td></td>
</tr>
<tr>
<td>objc</td>
<td>objc</td>
<td rowspan="2"></td>
</tr>
<tr>
<td>obj-c</td>
<td>objc</td>
</tr>
<tr>
<td>perl</td>
<td>perl</td>
<td rowspan="2"></td>
</tr>
<tr>
<td>pl</td>
<td>perl</td>
</tr>
<tr>
<td>php</td>
<td>php</td>
<td></td>
</tr>
<tr>
<td>plain</td>
<td>plain</td>
<td></td>
</tr>
<tr>
<td>text</td>
<td>plain</td>
<td></td>
</tr>
<tr>
<td>ps</td>
<td>powershell</td>
<td rowspan="2"></td>
</tr>
<tr>
<td>powershell</td>
<td>powershell</td>
</tr>
<tr>
<td>py</td>
<td>python</td>
<td rowspan="2"></td>
</tr>
<tr>
<td>python</td>
<td>python</td>
</tr>
<tr>
<td>r</td>
<td>r</td>
<td>Not used as a shortcode</td>
</tr>
<tr>
<td>splus</td>
<td>r</td>
<td></td>
</tr>
<tr>
<td>rails</td>
<td>ruby</td>
<td rowspan="4">针对Ruby的。</td>
</tr>
<tr>
<td>rb</td>
<td>ruby</td>
</tr>
<tr>
<td>ror</td>
<td>ruby</td>
</tr>
<tr>
<td>ruby</td>
<td>ruby</td>
</tr>
<tr>
<td>scala</td>
<td>scala</td>
<td></td>
</tr>
<tr>
<td>sql</td>
<td>sql</td>
<td></td>
</tr>
<tr>
<td>vb</td>
<td>vb</td>
<td rowspan="2"></td>
</tr>
<tr>
<td>vbnet</td>
<td>vb</td>
</tr>
<tr>
<td>xml</td>
<td>xml</td>
<td rowspan="5">针对XML、HTML以及XHTML等，其实都是按照XML来处理的</td>
</tr>
<tr>
<td>xhtml</td>
<td>xml</td>
</tr>
<tr>
<td>xslt</td>
<td>xml</td>
</tr>
<tr>
<td>html</td>
<td>xml</td>
</tr>
<tr>
<td>xhtml</td>
<td>xml</td>
</tr>
</tbody>
</table>
从这个表中，我们也可以看出SyntaxHighlighter支持的编程语言多达二十五种语言：AppleScript、 ActionScript、 Bash、 ColdFusion、 C /C++、 C#、 CSS、 Delphi、 Diff（不知道这是不是一种编程语言）、 Erlang、 Groovy、 Java、 JavaFX、 JavaScript、 Perl、 PHP、 PowerShell、 Python、 Ruby、 Sass、 Scala、 SQL、 VB、 XML。
最佳实践

经过配置的讲解，我们可以明白，SyntaxHighlighter已经遵循了软件工程中的最佳实践“约定大于配置”。其实，我们并不需要过多地去设定SyntaxHighlighter的配置，只需要设定一些“实在没办法约定”的配置项即可。比如：title、highlight等。另外，经过我自己的实际测试，我还发现了第五种使用方法，其实，我们可以在[代码名称]这个标签中，添加刚刚讲到的配置配置项。当然，lang就没必要了。因为这里已经通过“标签名”指定过了。综上所述，SyntaxHighlighter使用方法的最佳实践如下：（下面以Java代码为例）

[@java title="自定义的文件名" highlight="高亮的行"]　这里写你的代码　[/java]

有时，我们并不需要一定有高亮强调的行，这是highlight就可以省略掉。另外，如果你需要自定义样式，可以添加class属性。不过，我个人觉得必要性不大。

转载自：https://www.cnblogs.com/MrYoodb/p/4260033.html