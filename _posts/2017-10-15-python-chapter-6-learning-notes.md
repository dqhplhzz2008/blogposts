---
ID: 3477
post_title: Python chapter 6 learning notes
post_name: python-chapter-6-learning-notes
author: 小奥
post_date: 2017-10-15 14:07:01
layout: post
link: >
  http://www.yushuai.me/2017/10/15/3477.html
published: true
tags:
  - Python
  - python学习
categories:
  - Python
---
<p class="MsoListParagraph" style="margin-left:28px"><span style="font-family:Wingdings">l<span style="font-variant-numeric: normal;font-stretch: normal;font-size: 9px;line-height: normal;font-family: &#39;Times New Roman&#39;">&nbsp; </span></span>A simple dictionary</p><p></p><pre class="brush:python;toolbar:false">alien_0&nbsp;=&nbsp;{&#39;color&#39;:&nbsp;&#39;green&#39;,&#39;point&#39;:&nbsp;5}
print(alien_0[&#39;color&#39;])#使用大括号</pre><p><br/></p><p>The window will show green.</p><p class="MsoListParagraph" style="margin-left:28px"><span style="font-family:Wingdings">l<span style="font-variant-numeric: normal;font-stretch: normal;font-size: 9px;line-height: normal;font-family: &#39;Times New Roman&#39;">&nbsp; </span></span>Using dictionary</p><p class="MsoListParagraph" style="margin-left:56px"><span style="font-family:Wingdings">n<span style="font-variant-numeric: normal;font-stretch: normal;font-size: 9px;line-height: normal;font-family: &#39;Times New Roman&#39;">&nbsp; </span></span>Add key-value pair</p><p>For example,</p><pre class="brush:python;toolbar:false">alien_0&nbsp;=&nbsp;{&#39;color&#39;:&nbsp;&#39;green&#39;,&#39;point&#39;:&nbsp;5}
print(alien_0[&#39;color&#39;])
&nbsp;
alien_0[&#39;x_position&#39;]&nbsp;=&nbsp;0
alien_0[&#39;y_position&#39;]&nbsp;=&nbsp;25
print(alien_0)</pre><p>The window will show</p><pre class="brush:python;toolbar:false">{&#39;color&#39;:&nbsp;&#39;green&#39;,&nbsp;&#39;point&#39;:&nbsp;5,&nbsp;&#39;x_position&#39;:&nbsp;0,&nbsp;&#39;y_position&#39;:&nbsp;25}</pre><ul style="margin-top:0" class=" list-paddingleft-2"><ul style="list-style-type: square;" class=" list-paddingleft-2"><li><p>Modify the key-value pair</p></li></ul></ul><pre class="brush:python;toolbar:false">alien_0[&#39;color&#39;]&nbsp;=&nbsp;&#39;yellow&#39;</pre><ul style="margin-top:0" class=" list-paddingleft-2"><ul style="list-style-type: square;" class=" list-paddingleft-2"><li><p>Delete the key-value pair</p></li></ul></ul><p>Use <strong><em>del</em></strong> is OK.</p><p>For example,</p><pre class="brush:python;toolbar:false">del&nbsp;alien_0[&#39;points&#39;]</pre><p>Dictionary will not include <strong><em>points</em></strong>.</p><ul style="margin-top:0" class=" list-paddingleft-2"><ul style="list-style-type: square;" class=" list-paddingleft-2"><li><p>Dictionary just like struct in C language.</p></li><li><p>The dictionary which consists of many objects:</p></li></ul></ul><p>For example,</p><p></p><pre class="brush:python;toolbar:false">favorite_languages&nbsp;=&nbsp;{
&#39;David&#39;:&nbsp;&#39;python&#39;,
&#39;Jane&#39;&nbsp;:&nbsp;&#39;java&#39;,
&#39;John&#39;&nbsp;:&nbsp;&#39;C&#39;,
&#39;Sarah&#39;&nbsp;:&nbsp;&#39;ruby&#39;,
&#39;Michel&#39;&nbsp;:&nbsp;&#39;swift&#39;&nbsp;
}
&nbsp;
print(&quot;David&#39;s&nbsp;favorite&nbsp;languages&nbsp;is&nbsp;&quot;&nbsp;+&nbsp;
favorite_languages[&#39;David&#39;].title()&nbsp;+&nbsp;&quot;.&quot;)</pre><p><br/></p><p>It will show,</p><pre class="brush:python;toolbar:false">David&#39;s&nbsp;favorite&nbsp;languages&nbsp;is&nbsp;Python.</pre><p><br/></p><p><strong>Remember the format!</strong></p><p class="MsoListParagraph" style="margin-left:28px"><span style="font-family:Wingdings">l<span style="font-variant-numeric: normal;font-stretch: normal;font-size: 9px;line-height: normal;font-family: &#39;Times New Roman&#39;">&nbsp; </span></span>Ergodic dictionary</p><p class="MsoListParagraph" style="margin-left:56px"><span style="font-family:Wingdings">n<span style="font-variant-numeric: normal;font-stretch: normal;font-size: 9px;line-height: normal;font-family: &#39;Times New Roman&#39;">&nbsp; </span></span>Ergodic all key-value pairs</p><p>Method: items(): items()方法用于返回字典dict的(key，value)元组对的列表</p><ul style="margin-top:0" class=" list-paddingleft-2"><ul style="list-style-type: square;" class=" list-paddingleft-2"><li><p>Ergodic all keys</p></li></ul></ul><p>Method: keys():返回字典dict的键列表</p><p>For example,</p><p></p><pre class="brush:python;toolbar:false">for&nbsp;name&nbsp;in&nbsp;favorite_languages.keys():
print(name.title()&nbsp;+&nbsp;&nbsp;&quot;.&quot;)
But&nbsp;if&nbsp;we&nbsp;use
for&nbsp;name&nbsp;in&nbsp;favorite_languages:
print(name.title()&nbsp;+&nbsp;&nbsp;&quot;.&quot;)</pre><p><br/></p><p>They all have same output.</p><p class="MsoListParagraph" style="margin-left:56px"><span style="font-family:Wingdings">n<span style="font-variant-numeric: normal;font-stretch: normal;font-size: 9px;line-height: normal;font-family: &#39;Times New Roman&#39;">&nbsp; </span></span>Ergodic all values</p><p class="MsoListParagraph" style="margin-left:56px"><span style="font-family:Wingdings">n<span style="font-variant-numeric: normal;font-stretch: normal;font-size: 9px;line-height: normal;font-family: &#39;Times New Roman&#39;">&nbsp; </span></span>Method: values():返回字典dict的值列表</p><p>As we all know, the list of <strong><em>value</em></strong> may have same values, then ,how to keep only one value?</p><p>We can use <strong><em>set()</em></strong>. For example,</p><pre class="brush:python;toolbar:false">for&nbsp;language&nbsp;in&nbsp;set(favorite_languages.values()):
print(language.title())</pre><p class="MsoListParagraph" style="margin-left:28px"><span style="font-family:Wingdings">n<span style="font-variant-numeric: normal;font-stretch: normal;font-size: 9px;line-height: normal;font-family: &#39;Times New Roman&#39;">&nbsp; </span></span>Nesting: 将一系列字典存储在列表中，或将列表作为值存储在字典中，这被称为嵌套。</p><p>&nbsp;</p><p><br/></p>