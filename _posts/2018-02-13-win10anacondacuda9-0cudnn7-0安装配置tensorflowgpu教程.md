---
ID: 3632
post_title: >
  WIN10+anaconda+CUDA9.0+CUDNN7.0安装配置Tensorflow(GPU)教程
post_name: 'win10anacondacuda9-0cudnn7-0%e5%ae%89%e8%a3%85%e9%85%8d%e7%bd%aetensorflowgpu%e6%95%99%e7%a8%8b'
author: 小奥
post_date: 2018-02-13 16:14:53
layout: post
link: >
  http://www.yushuai.me/2018/02/13/3632.html
published: true
tags:
  - Tensorflow
categories:
  - Deep Learning
---
<p>1.首先可以安装VS也可以不安装VS。VS可以安装2013/2015/2017版本。</p><p>2.然后下载CUDA9.0版本。目前最新版本是CUDA9.1版，但是貌似Tensorflow目前还不支持CUDA9.1版。</p><p>下载地址为：<a href="https://developer.nvidia.com/cuda-downloads">https://developer.nvidia.com/cuda-downloads</a></p><p>点击legacy release，然后选择相应的版本和操作系统。</p><p style="text-align: center;"><img src="/wp-content/uploads/image/20180213/1518509480116234.png" title="1518509480116234.png" alt="1518509480116234.png" width="657" height="490"/></p><p>如图所示。一般情况下选择exe[local]版本，然后选择下载base installer。下载之后，然后进行安装。具体不再叙述。</p><p>3.然后下载CUDNN7.0。下载地址为：<a href="https://developer.nvidia.com/cudnn">https://developer.nvidia.com/cudnn</a></p><p>该地址需要注册，然后点击同意就可以选择相应版本。</p><p>我这里安装的CUDA9.0因此选择的<strong>cuDNN v7.0.5 Library for Windows 10</strong>。</p><p style="text-align: center;"><img src="/wp-content/uploads/image/20180213/1518509503109698.png" title="1518509503109698.png" alt="1518509503109698.png" width="657" height="590"/></p><p>然后下载即可。下载完成后，解压，然后将里面的文件复制到CUDA9.0的安装目录。一般情况下，安装目录为：C:\Program Files\NVIDIA GPU Computing Toolkit\CUDA\v9.0</p><p>4.由于直接运行了安装程序，所以环境配置系统已经自动配置好了。在此就不提配置环境变量了。</p><p>5.接下来安装Anaconda。在官网下载以后，直接安装即可。安装的时候记得选择Just Me，<strong><span style="color:red">下一步后的两个选项全部选择</span></strong>。</p><p>6. 安装好之后在Anaconda程序列表中打开Anaconda Prompt</p><p>如图所示。</p><p style="text-align: center;"><img src="/wp-content/uploads/image/20180213/1518509581111247.png" title="1518509581111247.png" alt="1518509581111247.png" width="657" height="343"/></p><p>然后输入以下代码后敲回车：</p><pre class="brush:python;toolbar:false">conda&nbsp;config&nbsp;--add&nbsp;channels&nbsp;https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/&nbsp;
conda&nbsp;config&nbsp;--set&nbsp;show_channel_urls&nbsp;yes</pre><p>7.然后在Anaconda Prompt中利用Anaconda创建一个python3.5的环境，环境名称为tensorflow ，输入命令：</p><pre class="brush:python;toolbar:false">conda&nbsp;create&nbsp;-n&nbsp;tensorflow&nbsp;python=3.6</pre><p><strong>注意：很多教程里面python=后面为3.5，但是目前我用的是python3.6，所以改为了3.6。</strong></p><p>在Anaconda Prompt中启动tensorflow环境：</p><pre class="brush:python;toolbar:false">activate&nbsp;tensorflow</pre><p>另外，关闭环境为</p><pre class="brush:python;toolbar:false">deactivate</pre><p>8.最后关键的一步就是安装Tensorflow。在Anaconda Prompt中输入：</p><pre class="brush:python;toolbar:false">pip&nbsp;install&nbsp;--ignore-installed&nbsp;--upgrade&nbsp;tensorflow-gpu</pre><p>当然，如果你安装的是CPU版本，在里面输入：</p><pre class="brush:python;toolbar:false">pip&nbsp;install&nbsp;--ignore-installed&nbsp;--upgrade&nbsp;tensorflow</pre><p>&nbsp;</p><p>到此，安装过程已经结束。接下来，到Anaconda Navigator中，点击Environments，可以看到我们建立的tensorflow环境。点击一下，如图所示：</p><p style="text-align: center;"><img src="/wp-content/uploads/image/20180213/1518509600132636.png" title="1518509600132636.png" alt="1518509600132636.png" width="657" height="359"/></p><p><br/></p><p>然后返回Home。如图所示：</p><p style="text-align: center;"><img src="/wp-content/uploads/image/20180213/1518509638135138.png" title="1518509638135138.png" alt="1518509638135138.png" width="657" height="281"/></p><p>一般情况下，notebook还有spyder可能并没有安装，那么直接点击Install安装即可。</p><p>最后，点击两者中的一个，打开以后，做一下测试：</p><pre class="brush:python;toolbar:false">import&nbsp;tensorflow&nbsp;as&nbsp;tf
hello&nbsp;=&nbsp;tf.constant(&quot;Hello!TensorFlow&quot;)
sess&nbsp;=&nbsp;tf.Session()
print(sess.run(hello))</pre><p>如果出现如图所示的结果，则证明安装成功</p><p style="text-align:center"><img src="/wp-content/uploads/image/20180213/1518509666308676.png" title="1518509666308676.png" alt="1518509666308676.png" width="475" height="138"/></p><p>-完-</p>