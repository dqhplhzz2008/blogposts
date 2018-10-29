---
ID: 2234
post_title: >
  WordPress将文章同步到新浪微博的几种方法（三种）
post_name: 'wordpress%e5%b0%86%e6%96%87%e7%ab%a0%e5%90%8c%e6%ad%a5%e5%88%b0%e6%96%b0%e6%b5%aa%e5%be%ae%e5%8d%9a%e7%9a%84%e5%87%a0%e7%a7%8d%e6%96%b9%e6%b3%95%ef%bc%88%e4%b8%89%e7%a7%8d%ef%bc%89'
author: 小奥
post_date: 2013-10-13 20:10:32
layout: post
link: >
  http://www.yushuai.me/2013/10/13/2234.html
published: true
tags: [ ]
categories:
  - Wordpress
---
第一种方法：WordPress连接微博——最为强大的同步插件

插件下载地址：http://wordpress.org/extend/plugins/wp-connect/

支持同步Wordpress日志“可选”的标题、摘要、内容、首张图片、链接和短地址等同步到微博；

支持微博账户登录Worppress评论系统并同步评论。

这样基本上将Wordpress和微博完全联系起来，所以插件名也由原来的“wordpress微博同步”升级为“WordPress连接微博”。

另一个不同于WP-Follow5的是”WordPress连接微博“可以设定自己的API KEY。这样同步成功后，微博的“From”可以显示自己的“来自……”。使用自己的API也更大程度上避免了API被封的风险。<!--more-->

第二种方法：关联博客

使用新浪微博的关联博客功能

使用方法：点击新浪微博右上角的"工具"菜单，再在点击"关联博客"，填上你的博客链接即可！这样，你的博客每次有文章更新，就会有同时发一条以下格式的微博到新浪微博：文章标题 + 文章URL

第三种方法：微博开放平台接口

新浪微博的开放平台接口，可以大大提高自由度，不过需要编写一些代码，其实很简单，复制粘贴代码就可以了。用文本编辑器打开你当前使用的主题目录下的functions.php，将以下代码复制到第一个 &lt;?php 下面：
<div>
<div><code>function</code> <code>post_to_sina_weibo($post_ID) {</code></div>
<div><code>    </code><code>if</code><code>( wp_is_post_revision($post_ID) ) </code><code>return</code><code>;</code></div>
<div><code>     </code></div>
<div><code>    </code><code>// 将 abc 替换成你的新浪微博登陆名</code></div>
<div><code>    </code><code>$username = </code><code>"abc"</code><code>;</code></div>
<div><code>    </code><code>// 将 123 替换成你的新浪微博密码</code></div>
<div><code>    </code><code>$password = </code><code>"123"</code><code>;</code></div>
<div><code>     </code></div>
<div><code>    </code><code>$get_post_info = get_post($post_ID);</code></div>
<div><code>     </code></div>
<div><code>    </code><code>if</code> <code>( $get_post_info-&gt;post_status == </code><code>'publish'</code> <code>&amp;&amp; $_POST[</code><code>'original_post_status'</code><code>] != </code><code>'publish'</code> <code>) {</code></div>
<div><code>        </code><code>$request = </code><code>new</code> <code>WP_Http;</code></div>
<div><code>        </code><code>$status = strip_tags( $_POST[</code><code>'post_title'</code><code>] ) . </code><code>' '</code> <code>. urlencode( get_permalink($post_ID) );</code></div>
<div><code>        </code><code>$api_url = </code><code>'<a href="http://api.t.sina.com.cn/statuses/update.json">http://api.t.sina.com.cn/statuses/update.json</a>'</code><code>;</code></div>
<div><code>        </code><code>$body = array( </code><code>'status'</code> <code>=&gt; $status, </code><code>'source'</code><code>=&gt;</code><code>'1134914270'</code><code>);</code></div>
<div><code>        </code><code>$headers = array( </code><code>'Authorization'</code> <code>=&gt; </code><code>'Basic '</code> <code>. base64_encode(</code><code>"$username:$password"</code><code>) );</code></div>
<div><code>        </code><code>$result = $request-&gt;post( $api_url , array( </code><code>'body'</code> <code>=&gt; $body, </code><code>'headers'</code> <code>=&gt; $headers ) );</code></div>
<div><code>    </code><code>}</code></div>
<div><code>}</code></div>
<div><code> </code></div>
<div><code>add_action(</code><code>'publish_post'</code><code>, </code><code>'post_to_sina_weibo'</code><code>, </code><code>0</code><code>);</code></div>
</div>
以上代码15行的1134914270是新浪开放平台的appkey，如果你有appkey的话可以改成你的自己的(以上appkey已经过期，无法使用)。好了，以后每当你的WordPress博客有文章更新，就会有同时发一条以下格式的微博到新浪微博：文章标题 + 文章URL。可能你不喜欢文章标题 + 文章URL这种形式，现在我教你怎么自定义发布到新浪微博的格式。以下介绍几种常见的微博格式：

文章摘要 + 文章URL

WordPress文章编辑页都有个"摘要"输入框，这里可以输入你的文章摘要。如果你想以文章摘要 + 文章URL的形式发布到新浪微博，可以将以上代码中13行改成：
<div><code>$status = strip_tags( $_POST[</code><code>'excerpt'</code><code>] ) . </code><code>' '</code> <code>. urlencode( get_permalink($post_ID) );</code></div>
这样就相当于直接在你WordPress博客上发布新浪微博了！

只输出文章URL

如果你只想发布一条文章链接到新浪微博，那就将以上代码13行改成：
<div><code>$status = urlencode( get_permalink($post_ID) );</code></div>