---
ID: 3448
post_title: 'Deep Learning in Neural Networks: An Overview（自己翻译版）'
post_name: 'deep-learning-in-neural-networks-an-overview%ef%bc%88%e8%87%aa%e5%b7%b1%e7%bf%bb%e8%af%91%e7%89%88%ef%bc%89'
author: 小奥
post_date: 2017-08-19 14:43:51
layout: post
link: >
  http://www.yushuai.me/2017/08/19/3448.html
published: true
tags:
  - Deep Learning
  - 人工智能
  - 深度学习
  - 神经网络
categories:
  - Deep Learning
---
<h1 style="font-size: 32px; font-weight: bold; border-bottom-color: rgb(204, 204, 204); border-bottom-width: 2px; border-bottom-style: solid; padding: 0px 4px 0px 0px; text-align: left; margin: 0px 0px 10px;"><span style="font-family:宋体">一、对于神经网络中深度学习的介绍<br/></span></h1><p style="text-indent:28px"><span style="font-family:宋体">在学习系统中哪些可修改元素应该对其成功或者失败负责？是什么改变了它们来提高了表现？这一切被称为</span><span style="font-family:&#39;Times New Roman&#39;,serif">“</span><span style="font-family:宋体">基本信用分配问题</span><span style="font-family:&#39;Times New Roman&#39;,serif">”</span><span style="font-family:宋体">。通用问题解决者有一般的信用分配方法，这些方法在各种理论意义上是时间最优的。然而，当前的调查主要关注人工神经网络中较窄，但是在商业上非常重要的深度学习的子领域上。我们对神经网络中通过可能的许多计算计算阶段的精确信用分配感兴趣。</span></p><p style="text-indent:28px"><span style="font-family:宋体">浅层学习模型已经存在了大约几十年。具有几个连续非线性神经元层的模型可以追溯到至少</span><span style="font-family:&#39;Times New Roman&#39;,serif">20</span><span style="font-family:宋体">世纪</span><span style="font-family:&#39;Times New Roman&#39;,serif">60</span><span style="font-family:宋体">年代、</span><span style="font-family:&#39;Times New Roman&#39;,serif">70</span><span style="font-family:宋体">年代。在此时，有人提出了一种在离散、可微分的任意深度网络（称为</span><span style="font-family:&#39;Times New Roman&#39;,serif">“</span><span style="font-family:宋体">反向传播</span><span style="font-family:&#39;Times New Roman&#39;,serif">”</span><span style="font-family:宋体">）中基于教学的监督学习的有效梯度下降算法，并且这一方法在</span><span style="font-family:&#39;Times New Roman&#39;,serif">1981</span><span style="font-family:宋体">年被应用到了神经网络。</span></p><p style="text-indent:28px"><span style="font-family:宋体">无论是前馈神经网络（</span><span style="font-family:&#39;Times New Roman&#39;,serif">FNNs</span><span style="font-family:宋体">，非循环）还是递归神经网络（</span><span style="font-family:&#39;Times New Roman&#39;,serif">RNNs</span><span style="font-family:宋体">，循环）都广受欢迎。在某种程度上来说，</span><span style="font-family:&#39;Times New Roman&#39;,serif">RNNs</span><span style="font-family:宋体">是所有神经网络中深度最深的</span><span style="font-family:&#39;Times New Roman&#39;,serif">——</span><span style="font-family:宋体">他们是通用计算机但却比</span><span style="font-family:&#39;Times New Roman&#39;,serif">FNNs</span><span style="font-family:宋体">更为强大，并且它可以原则上创建和处理输入模型的任意序列的记忆。不像传统自动顺序程序综合方法，</span><span style="font-family:&#39;Times New Roman&#39;,serif">RNNs</span><span style="font-family:宋体">可以以一种自然而有效的方式学习混合顺序和并行信息处理的程序，利用大量的并行性被认为是在维持过去</span><span style="font-family:&#39;Times New Roman&#39;,serif">75</span><span style="font-family:宋体">年来观察到的计算成本快速下降的关键。</span></p><p><br/></p>