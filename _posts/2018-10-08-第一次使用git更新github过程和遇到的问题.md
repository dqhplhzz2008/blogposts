---
ID: 3986
post_title: >
  第一次使用git更新github过程和遇到的问题
post_name: '%e7%ac%ac%e4%b8%80%e6%ac%a1%e4%bd%bf%e7%94%a8git%e6%9b%b4%e6%96%b0github%e8%bf%87%e7%a8%8b%e5%92%8c%e9%81%87%e5%88%b0%e7%9a%84%e9%97%ae%e9%a2%98'
author: 小奥
post_date: 2018-10-08 15:40:46
layout: post
link: >
  http://www.yushuai.me/2018/10/08/3986.html
published: true
tags:
  - Git
  - GitHub
categories:
  - 其它内容
---
不知道大家有没有发现我的个人学习笔记目录发生了变化，实际上这个变化来源于我在更新我的github的repository的方式由利用Github Desktop修改为了利用Git更新。虽然说前者更简洁也更傻瓜式，但是为了今后着想，我还是决定要学习使用Git来进行更新。

其实利用Git更新用两种方式，一是利用https方式，另一种是利用ssh加密传输的方式。我选择的是利用ssh加密传输的方式，这样的好处是传输更加安全，也不需要在第一次的时候输入github的账号密码就可以了。
<h2>利用Git第一次进行GitHub更新的步骤</h2>
1.安装Git for Windows，在GitHub上新建一个repository，具体步骤就不说了。

2.打开Git Bash，输入：

<code class="ruby"><span class="variable">$ </span>git config --global user.name <span class="string">"Your Name"</span>
</code>

<code class="ruby"><span class="variable">$ </span>git config --global user.email <span class="string">"email@example.com"</span></code>

这个命令是填充自己的名字和邮箱，作为自己的一个标识。

3.若本地没有生成ssh的密钥，则需要利用命令进行生成，命令如下：

ssh-keygen -t rsa -C "your_email@youremail.com"

4.完成以后，进入GitHub中，点击Settings，选择SSH and GPG keys,点击NEW SSH key，然后名称随便写（最好作为一个标记），然后将生成的ssh密钥复制进下面的文本框后，点击Add SSH Key即可。（生成的密钥文件在<strong>C:\Users\yourusername\.ssh</strong>目录中的id_rsa.pub）

5.进行更新。更新有以下两种情况：

（1）全新上传

①利用cd命令将git bash中当前目录设置为我们需要上传的目录。

②执行git init。会在该目录中生成一个.git的文件夹。

③执行git add .

④执行git commit -m "first commit"

⑤执行git remote add origin git@github.com:******.git（在github该目录下会获取到）

⑥执行git push -u origin master，开始上传，等待上传完成即完成。

（2）后续更新文件

①直接执行git remote add origin git@github.com:******.git

②执行git push -u origin master
<h2>在首次更新的时候遇到的问题</h2>
在首次更新的时候遇到下面的问题：

<img class="aligncenter size-large wp-image-3987" src="https://dqhplhzz2008-1251830035.cos.ap-guangzhou.myqcloud.com/wp-content/uploads/2018/10/1.png" alt="" width="450" height="87" />
<p style="text-align: center;">图1 错误信息</p>
    所需要做的事情就是在<strong>C:\Users\yourusername\.ssh</strong>目录中新建一个config文件，然后填入以下信息：

Host github.com
User <span style="font-family: 'arial black', sans-serif;"><strong>你的邮箱账号@xxx.com</strong></span>
Hostname ssh.github.com
PreferredAuthentications publickey
IdentityFile ~/.ssh/id_rsa
Port 443

&nbsp;

然后在git bash中执行：

ssh -T git@github.com

会提示有问题，然后让你确认是否继续，输入yes。然后最后会出现successfully的提示即可继续进行接下来的操作。如下图所示。

<img class="aligncenter size-large wp-image-3988" src="https://dqhplhzz2008-1251830035.cos.ap-guangzhou.myqcloud.com/wp-content/uploads/2018/10/2.png" alt="" width="450" height="142" />
<p style="text-align: center;">图2 提示成功界面</p>