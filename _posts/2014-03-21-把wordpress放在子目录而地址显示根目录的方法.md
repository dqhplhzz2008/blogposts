---
ID: 2431
post_title: >
  把WordPress放在子目录而地址显示根目录的方法
post_name: '%e6%8a%8awordpress%e6%94%be%e5%9c%a8%e5%ad%90%e7%9b%ae%e5%bd%95%e8%80%8c%e5%9c%b0%e5%9d%80%e6%98%be%e7%a4%ba%e6%a0%b9%e7%9b%ae%e5%bd%95%e7%9a%84%e6%96%b9%e6%b3%95'
author: 小奥
post_date: 2014-03-21 16:20:06
layout: post
link: >
  http://www.yushuai.me/2014/03/21/2431.html
published: true
tags: [ ]
categories:
  - Wordpress
  - 编程语言
---
以WordPress放在在子目录博客显示在根目录开题。要实现如下所示的效果，空间需支持 rewrite–这是前提。如果不支持的话神都救不了你，哈哈。如果我们要在根目录安装WordPress，根目录就会被WordPress的文件弄得很 乱，如果再添加了自己的一些目 录就更加难以维护了。不过还好，WordPress允许将Blog主页不同于 WordPress 的安装目录的Web地址，这样我们就可以把WordPress放在子目录中，只需要简单的设置便可以让链接形式仍以根目录显示。这篇文章翻译自 WordPress官方文档，水平有限，见谅！下面是译文：<!--more-->

把WordPress放在在单独目录中而让你的博客显示在根目录

很多人想让WordPress来驱动他们站点的根目录（例如：http://example.com），但是他们不想让所有的的 WordPress文件把他们的根目录弄乱。WordPress允许你把WordPress文件放在一个子目录，同时让你的博客显示在站点的根目录中。

把WordPress放到单独它单独目录下的程序如下：

1、新建一个用来存放WordPress核心文件的新文件夹（本例以/wordpress示范）。

2、进入选项（options）面板。

3、找到WordPress address (URL)（中文用户请查找”WordPress 地址（URL）“）这个选项：把后面的地址改成你存放WordPress文件的文件夹地址。比如：http://example.com/wordpress

4、找到Blog address (URL)（中文用户请查找”Blog 地址（URL）“）这个选项：把此地址改为你网站的根目录的URL。例如：http://example.com

5、点击Update Options（中文用户为“更新设置”）。

6、把WordPress的核心文件转移到你新建的文件夹中，也就是WordPress address (URL)这个目录。还不明白？在明确一点：/wordpress目录。

7、把index.php和.htaccess文件从WordPress目录转移到根目录（即Blog address）中。

8、用文本编辑器打开并编辑根目录下”index.php”这个文件。

9、找到如下代码，修改并保存：找到：

require('./wp-blog-header.php');

把地址改为你WordPress目录下的文件：

require('./wordpress/wp-blog-header.php');

10、登陆控制面板，新的控制面板地址为http://example.com/wordpress/wp-admin/

11、如果你设置了结构化链接地址（Permalinks），打开永久链接选 项面板更新Permalinks结构。如果.htaccess有正确的权限设置的话WordPress会自动更新你的.htaccess文件。如果 WordPress不能写入你的.htaccess文件，就会显示新的rewrite规则，因此你就需要手动把rewrite规则复制到. htaccess文件中（和index.php同目录）。

原文地址：http://codex.wordpress.org/Giving_WordPress_Its_Own_Directory