---
ID: 2417
post_title: wordpress免插件判断移动设备
post_name: 'wordpress%e5%85%8d%e6%8f%92%e4%bb%b6%e5%88%a4%e6%96%ad%e7%a7%bb%e5%8a%a8%e8%ae%be%e5%a4%87'
author: 小奥
post_date: 2014-03-16 21:24:07
layout: post
link: >
  http://www.yushuai.me/2014/03/16/2417.html
published: true
tags: [ ]
categories:
  - Wordpress
---
这是一段php通用的判断移动浏览器的函数,原理比较简单,就是判断浏览器返回的user_agent,条件包括手机系统,品牌和窗口大小.
以wordpress为例,在主题的function.php内加上如下代码,我找了一些常见移动浏览器的useragent,其中有很多国内流行的手机浏览器,基本上可以涵盖可能会用手机上网的用户群了..<!--more-->
<pre>function is_mobile() {
	$user_agent = $_SERVER['HTTP_USER_AGENT'];
	$mobile_browser = Array(
		"mqqbrowser", //手机QQ浏览器
		"opera mobi", //手机opera
		"juc","iuc",//uc浏览器
		"fennec","ios","applewebKit/420","applewebkit/525","applewebkit/532","ipad","iphone","ipaq","ipod",
		"iemobile", "windows ce",//windows phone
		"240x320","480x640","acer","android","anywhereyougo.com","asus","audio","blackberry","blazer","coolpad" ,"dopod", "etouch", "hitachi","htc","huawei", "jbrowser", "lenovo","lg","lg-","lge-","lge", "mobi","moto","nokia","phone","samsung","sony","symbian","tablet","tianyu","wap","xda","xde","zte"
	);
	$is_mobile = false;
	foreach ($mobile_browser as $device) {
		if (stristr($user_agent, $device)) {
			$is_mobile = true;
			break;
		}
	}
	return $is_mobile;
}</pre>
然后在主题任意模板如顶部加上如下判断:
<pre><?php if (is_mobile() ): ?>
	//怎样怎样..(这里可以添加一个mobile.css,如<link rel="stylesheet" type="text/css" media="all" href="<?php echo get_template_directory_uri(); ?>/mobile.css" />)
<?php endif ;?></pre>
还需要注意的一点：不管是单独的WordPress主题还是自适应主题，都需要在头部&lt;head&gt;将添加下面meta，否者可能导致手机显示字体过小等问题。
<pre>
<meta name="viewport" content="width=device-width"/></pre>