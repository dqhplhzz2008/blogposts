---
ID: 677
post_title: WP 嘀：嘀咕的 WordPress 插件
post_name: 'wp-%e5%98%80%ef%bc%9a%e5%98%80%e5%92%95%e7%9a%84-wordpress-%e6%8f%92%e4%bb%b6'
author: 小奥
post_date: 2010-03-07 22:38:20
layout: post
link: >
  http://www.yushuai.me/2010/03/07/677.html
published: true
tags: [ ]
categories:
  - Wordpress
---
WP 嘀有三大功能：
<ol>
	<li><!--more-->能够让你在 WordPress 后台查看所有嘀咕，还能分类查看直接的嘀咕，含有链接的嘀咕等等。</li>
	<li>能抓取你自己嘀咕和别人对你的回复嘀咕，以及你回复朋友的源嘀咕，以层式结果显示出来。</li>
	<li>能够让你直接在 WordPress 后台更新嘀咕，以及回复和转嘀。</li>
	<li>同步 WordPress 博客日志到嘀咕。</li>
</ol>
安装非常简单，上传激活之后，到 WordPress 后台 =&gt; 设置（Setting）=&gt; WP 嘀，然后输入你的嘀咕账号和密码之后，WordPress 后台就会多出一个 WP 嘀的根菜单，你就在这里使用 WP 嘀咕各个功能：
<ul>
	<li><strong>WP 嘀</strong>：显示你的嘀咕，别人回复你的嘀咕，以及你回复朋友的源嘀咕。</li>
	<li><strong>所有的嘀咕</strong>：显示你跟踪的所有朋友嘀咕。</li>
	<li><strong>@对我的回应</strong>：别人回复你的嘀咕</li>
	<li><strong>直接嘀咕</strong>：你跟踪的所有朋友的直接嘀咕，即该条嘀咕不是回复。</li>
	<li><strong>链接嘀咕</strong>：你跟踪的所有朋友的所有含有链接的嘀咕。</li>
	<li><strong>设置</strong>：和前面的设置一样。</li>
</ul>
如果你想在博客页面显示你的嘀咕信息，可以通过以下步骤实现：

1. 创建 WordPress 页面模板，在该模板中加入下面函数：
<pre>&lt;?php thread_digu(); ?&gt;</pre>
如何创建页面模板，请参考：使用 <a href="http://fairyfish.net/2007/07/06/using-wordpress-page-templates/">WordPress 页面模板</a>。

2. 新建一个页面，使用刚才的页面模板。

3. 自定义 CSS，样式化该页面的输出，这里是一个推荐是用的 CSS，你可以根据自己的主题适当修改下：
<pre>/* thread digu START */
.digu ul {
    margin:0 12px 0 10px !important;
    margin:0 10px;
}
.digu ul li {
    background:#FCFCFC;
    padding:0;
    float:left;
    list-style:none;
    list-style-position:outside;
    border:solid #CCC;
    border-width:1px !important;
    border-width:1px 0;
    width:100%;
    padding-top:10px;
    margin-bottom:10px;
}
.digu img {
    float:left;
    padding:0 10px 0 0;
    margin:0 0 10px 10px;
}
.digu_source {
    color:#999;
    font-family:georgia;
    font-style:italic;
}
.digu_source a {
    color:#999;
}
.digu_text {
    margin-bottom:5px;
    display:block;
    padding-left:70px;
    padding-right:10px;
}
.digu_reply {
    padding-left:22px;
    padding-right:10px;
    height:16px;
    line-height:16px;
    display:block;
    font-size:11px;
    float:right;
}
/* thread digu END */</pre>
下载：<a href="http://wpcn.googlecode.com/files/thread-digu-1.1.zip" target="_blank">WP 嘀</a>。