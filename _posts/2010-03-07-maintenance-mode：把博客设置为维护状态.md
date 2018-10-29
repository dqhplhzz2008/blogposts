---
ID: 679
post_title: >
  Maintenance
  Mode：把博客设置为维护状态
post_name: 'maintenance-mode%ef%bc%9a%e6%8a%8a%e5%8d%9a%e5%ae%a2%e8%ae%be%e7%bd%ae%e4%b8%ba%e7%bb%b4%e6%8a%a4%e7%8a%b6%e6%80%81'
author: 小奥
post_date: 2010-03-07 22:44:14
layout: post
link: >
  http://www.yushuai.me/2010/03/07/679.html
published: true
tags: [ ]
categories:
  - Wordpress
---
<a href="http://sw-guide.de/wordpress/plugins/maintenance-mode/" target="_blank">Maintenance Mode</a> 是一个 WordPress 插件，它的功能非常简单，能把你的 WordPress 博客设置为维护状态，这个功能特别有用，特别是你对博客测试建设期间不想公开的时候，或者进行一些改动还不想让用户看到的时候，这个是把博客设置为维护状态，当功能更新好，内容填充完再开放给用户使用。
<!--more-->

Maintenance Mode 这个插件我在给客户使用 WordPress 开发网站的时候，经常使用到，在建设期间，由于客户不想让人看到站点，但是又需要自己能够预览到站点功能的添加和更新，这个站点刚好符合需求，普通用户则看到维护状态，登录的用户则可以看到网站。

Maintenance Mode 使用非常简单，安装之后，在 WordPress 后台 &gt; 设置（Setting） &gt; Maintenance Mode 就可以进行设置了。

Maintenance Mode 插件第一个设置是让你是否把这个插件设置为 Activated 状态，个人觉得这个基本没有用，既然开启了这个插件自然是让他工作，如果把它设置为 Deactivated 状态还不如直接停止插件。

设置维护状态页面的信息：可以设置标题和页面内容，并且提供了 [blogurl], [blogtitle] 和 [backtime] 三个变量使用。另外这个插件还可以提供一个选项，让你使用当前主题下的 <code>503.php</code> 文件来显示维护状态页面的信息，这样你就可以自定义维护状态页面信息的样式，更加灵活。

Maintenance Mode 还可以让你设置显示多长时间网站会恢复，以及在网页的 HTTP header 中添加 '503 Service Unavailable' 和 'Retry-After ' 信息。

如果你想让用户在维护状态下还能访问一些页面，这个插件也提供了这种可能，你只需要把你让用户访问的页面输入 Paths to be still accessable 的输入框中即可。

最后 Maintenance Mode 还可以让你设置只有博客管理员才能访问 WordPress 后台。