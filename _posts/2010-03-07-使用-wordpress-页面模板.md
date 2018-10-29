---
ID: 675
post_title: 使用 WordPress 页面模板
post_name: '%e4%bd%bf%e7%94%a8-wordpress-%e9%a1%b5%e9%9d%a2%e6%a8%a1%e6%9d%bf'
author: 小奥
post_date: 2010-03-07 22:36:39
layout: post
link: >
  http://www.yushuai.me/2010/03/07/675.html
published: true
tags: [ ]
categories:
  - Wordpress
---
如果你定制或者设计过 WordPress 主题，那么你可能遇到过这样的问题：

<strong>如何让每个 WordPress 页面有不同的风格或者样式吗？<!--more--></strong>

如果使用 <a href="http://codex.wordpress.org/Pages" target="_blank">page.php</a> 来处理所有页面的外观的话，答案肯定是不行的，但是如果使用不同的 <strong>WordPress 页面模板</strong>，就可以自定义每个页面的外观了。

比如你博客的所有的页面除了“关于”这个页面之外都有侧边栏，在“关于”页面，你想内容的宽度能够扩展到这个页面的宽度。下面就是详细的实现步骤：
<ul>
	<li>在当前使用的主题文件夹中创建一个新模板，将它命名为 about.php。</li>
	<li>然后把 page.php 模板中的内容拷贝到 about.php 文件中。</li>
	<li>接着，找到模板文件中调用 sidebar 的地方，去掉或者注释掉它。</li>
	<li>可能需要找到 content div 标签，并手动给它增加一个 width 样式来扩展宽度以便能够占满整个 container div 标签。</li>
</ul>
完成之后，到 about.php 的最上面插入以下代码：
<pre>&lt;?php
/*
Template Name: 关于
*/
?&gt;</pre>
做好上面修改之后，保存，并上传到服务器上的当前主题文件夹下。

现在是到 WordPress 后台让“关于”页面使用“关于”页面模板：

创建新页面，或者编辑 about 页面（如果已经创建了），在右边，点击<strong>页面模板</strong>的下拉菜单，在下拉列表中找到“关于”，选择它并点击保存。

现在你的“关于”页面和你其他的页面使用不同的布局了。

使用 WordPress 页面模板技巧是非常常用的技巧，特别是那些把 WordPress 当作 CMS 的用户。使用你的想像力，你可以用它创建出一些非常有创意性的东东。