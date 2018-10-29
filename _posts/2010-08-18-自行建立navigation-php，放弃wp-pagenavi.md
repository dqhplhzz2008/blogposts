---
ID: 1309
post_title: >
  自行建立Navigation.php，放弃WP-Pagenavi
post_name: '%e8%87%aa%e8%a1%8c%e5%bb%ba%e7%ab%8bnavigation-php%ef%bc%8c%e6%94%be%e5%bc%83wp-pagenavi'
author: 小奥
post_date: 2010-08-18 14:25:12
layout: post
link: >
  http://www.yushuai.me/2010/08/18/1309.html
published: true
tags: [ ]
categories:
  - Wordpress
---
在使用WordPress的初期，不知道大家有没有曾为没有分页功能而烦恼呢。对于这个很普遍的基本功能WordPress竟然没有，这着实让我愕然了一会。

<!--more-->这样子，不单对用户做成不好的体验，简单来说就是对用户不友善。更会影响蜘蛛搜索你网站的幅盖率，因你页面中并不是完全直接显示网站内所有的页面，而是分成了数页分别输出。这样如果使用「上一页」和「下一页」的表示方式，便会造成了首页缺乏对所有分页的直接连结，从而影响了搜寻结果。
要解决这个问题，很简单，使用WordPress总类繁多的外置分页插件，如：WP-Pagenavi，PageBar等等。
不过这却造成了另一个问题——加重了对服务器CPU的负担，现在很多的虚拟主机都会对用户的CPU使用率有所限制，详情不在此细说。人在屋檐下，所以我们要尽量解决CPU使用量问题，自行使用代码，直接编辑主题，而舍弃插件的使用。
这是的行动可以实现的原因，其实是因为官方提供了paginate_links()函数，使得我们能够直接取得分页页数。
现在我来说一说自行在主题建立分页的过程，首先是在自己的主题建立一个navigation.php，并里面输入以下代码：

<code lang=”language”>
<!--p global $wp_rewrite; $paginate_base = get_pagenum_link(1); if (strpos($paginate_base, '?') || ! $wp_rewrit-->using_permalinks()) {
$paginate_format = '';
$paginate_base = add_query_arg('paged', '%#%');
} else {
$paginate_format = (substr($paginate_base, -1 ,1) == '/' ? '' : '/') .
user_trailingslashit('page/%#%/', 'paged');;
$paginate_base .= '%_%';
}
echo ' </code>
其中的換成你需要的分頁數目
<code lang=”language”>'mid_size' => 10,code>
另外添加以下代码：
<code lang=”language”>echo '<div>'. "\n";
...
echo "\n</div>\n";
 </code>
可以換成你需要的代碼，並加上class。同樣道理，當然你也可以按照規律加上適用的代碼。
<code lang=”language”>
echo '<div class="navi">'. "\n";
...
echo "\n</div>\n";
</code>
navigation.php建立成功後，可以在index.php中找到
<code lang=”language”><div class="navigation">
...
</div>
</code>
預設的WordPress分頁應該是長這樣
<code lang=”language”><div class="alignleft">
<?php next_posts_link('&laquo; Older Entries') ?>
</div>
<div class="alignright">
<?php previous_posts_link('Newer Entries &raquo;') ?>
</div>
</code>
我們以這段判斷代碼替換以上的代碼，來確認用戶是否有使用page-navi插件，如沒有則使用navigation.php。
<code lang=”language”>
<?php if (function_exists('wp_pagenavi')) { wp_pagenavi(); } else { include('navigation.php'); } ?>
</code>
最後加上在style.css加上樣式表，來設定你分頁的樣式就好了。
<code lang=”language”>
.navigation {
	display: block;
	padding:30px 20px 20px 20px;
	clear:both;
	width:100%;
}
.navigation a {
	color:#777;
}
.navigation ul {
	list-style:none;
}
.navigation ul li {
	float:left;
	margin: 0 3px 0 3px;
}
.navigation ul li a {
	background: #fff url(images/pagenavi_btn.gif) no-repeat 0 0;
	width:27px;
	height:22px;
	color: #777;
	padding:5px 0 0 0;
	text-align:center;
	display:block;
}
.navigation ul li a:hover {
	background: #fff url(images/pagenavi_btn.gif) no-repeat 0 100%;
}
.navigation ul li span.current {
	background: #777 url(images/pagenavi_btn_current.gif) no-repeat;
	width:27px;
	height:22px;
	color: #fff;
	padding:5px 0 0 0;
	text-align:center;
	display:block;
}
</code>

转载自：http://wsqsite.com/blog/page-navigation-plugin/