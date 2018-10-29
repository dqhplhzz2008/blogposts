---
ID: 4031
post_title: >
  C++ Primer
  Plus（第五版）Chapter5编程题整理
post_name: 'c-primer-plus%ef%bc%88%e7%ac%ac%e4%ba%94%e7%89%88%ef%bc%89chapter5%e7%bc%96%e7%a8%8b%e9%a2%98%e6%95%b4%e7%90%86'
author: 小奥
post_date: 2018-10-18 16:00:48
layout: post
link: >
  http://www.yushuai.me/2018/10/18/4031.html
published: true
tags: [ ]
categories:
  - C/C++
---
第五章编程题因为时间原因我就只做了前两个题，从第6章开始全部都做。

5.1输入2个整数，输出这2个之间（包括这两个）所有整数和

代码如下：
<pre class="lang:c++ decode:true ">#include&lt;iostream&gt;

#include&lt;cstring&gt;

using namespace std;

int main() {

       int a, b;

       int sum = 0;

       cout &lt;&lt; "Enter two number:" &lt;&lt; endl;

       cin &gt;&gt; a &gt;&gt; b;

       if (a &lt; b)

       {

              for (int i = a; i &lt;= b; i++)

                     sum += i;

       }

       else if (a &gt; b)

       {

              for (int i = b; i &lt;= a; i++)

                     sum += i;

       }

       cout &lt;&lt; sum &lt;&lt; endl;

       system("pause");

       return 0;

}</pre>
&nbsp;

5.2 编写一个整数输入程序，每输入一个数，显示累计和，输入0停止
<pre class="lang:c++ decode:true ">#include&lt;iostream&gt;

#include&lt;cstring&gt;

using namespace std;

int main() {

       int i;

       int count=0;

       cout &lt;&lt; "Enter number:" &lt;&lt; endl;

       cin &gt;&gt; i;

       while (i != 0)

       {

              count += i;

              cout &lt;&lt;"到目前的和为" &lt;&lt; count &lt;&lt; endl;

              cin &gt;&gt; i;

       }

       system("pause");

       return 0;

}</pre>
&nbsp;