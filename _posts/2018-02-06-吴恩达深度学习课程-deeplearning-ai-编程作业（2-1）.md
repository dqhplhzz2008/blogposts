---
ID: 3586
post_title: >
  吴恩达深度学习课程
  DeepLearning.ai
  编程作业（2-1）Part.1
post_name: '%e5%90%b4%e6%81%a9%e8%be%be%e6%b7%b1%e5%ba%a6%e5%ad%a6%e4%b9%a0%e8%af%be%e7%a8%8b-deeplearning-ai-%e7%bc%96%e7%a8%8b%e4%bd%9c%e4%b8%9a%ef%bc%882-1%ef%bc%89'
author: 小奥
post_date: 2018-02-06 12:25:34
layout: post
link: >
  http://www.yushuai.me/2018/02/06/3586.html
published: true
tags:
  - Python
  - 人工智能
categories:
  - Deep Learning
---
<p style="margin-top:auto;margin-bottom: auto;text-align:left"><strong><span style="font-size:32px;font-family:宋体">初始化</span></strong></p><p style="margin-top:auto;margin-bottom: auto;text-align:left;text-indent:32px"><span style="font-size:16px;font-family:宋体">欢迎来到“改进深度网络”课程作业的第一周第一部分。</span></p><p style="margin-top:auto;margin-bottom: auto;text-align:left;text-indent:32px"><span style="font-size:16px;font-family:宋体">训练你自己的深度网络需要指定权重的初始值，精心挑选的初始化方法将有助于学习的进度。</span></p><p style="margin-top:auto;margin-bottom: auto;text-align:left;text-indent:32px"><span style="font-size:16px;font-family:宋体">如果你完成了之前的课程，你可以按照我们的指导进行权重初始化，并且现在已经完成了。但是，你如何对一个新的神经网络进行初始化？在本次作业，你会看到不同的初始化会带来不同的结果。</span></p><p style="margin-top:auto;margin-bottom: auto;text-align:left;text-indent:32px"><span style="font-size:16px;font-family:宋体">一个良好的初始化能够：</span></p><p class="MsoListParagraph" style="margin-top:auto;margin-bottom: auto;margin-left:60px;text-align:left"><span style="font-size:16px;font-family:Wingdings">l<span style="font:9px &#39;Times New Roman&#39;">&nbsp; </span></span><span style="font-size:16px;font-family:宋体">加速梯度收敛</span></p><p class="MsoListParagraph" style="margin-top:auto;margin-bottom: auto;margin-left:60px;text-align:left"><span style="font-size:16px;font-family:Wingdings">l<span style="font:9px &#39;Times New Roman&#39;">&nbsp; </span></span><span style="font-size:16px;font-family:宋体">增加梯度下降收敛到较低的训练（和泛化）错误的几率</span></p><p style="margin-top:auto;margin-bottom: auto;text-align:left;text-indent:32px"><span style="font-size:16px;font-family:宋体">为了开始本作业，请运行下面的单元格来加载用来尝试分类的packages和planar dataset。</span></p><p style="margin-top:auto;margin-bottom: auto;text-align:left"><span style="font-size:16px;font-family:宋体"></span></p><pre class="brush:python;toolbar:false">import&nbsp;numpy&nbsp;as&nbsp;np
import&nbsp;matplotlib.pyplot&nbsp;as&nbsp;plt
import&nbsp;sklearn
import&nbsp;sklearn.datasets
from&nbsp;init_utils&nbsp;import&nbsp;sigmoid,relu,compute_loss,forward_propagation
from&nbsp;init_utils&nbsp;import&nbsp;update_parameters,&nbsp;predict,backward_propagation
from&nbsp;init_utils&nbsp;import&nbsp;predict_dec,load_dataset,&nbsp;plot_decision_boundary
%matplotlib&nbsp;inline
#使用%matplotlib命令可以将matplotlib的图表直接嵌入到Notebook之中，
#或者使用指定的界面库显示图表，它有一个参数指定matplotlib图表的显示方式
#inline表示将图表嵌入到Notebook中
plt.rcParams[&#39;figure.figsize&#39;]&nbsp;=&nbsp;(7.0,&nbsp;4.0)&nbsp;#&nbsp;set&nbsp;default&nbsp;size&nbsp;of&nbsp;plots
plt.rcParams[&#39;image.interpolation&#39;]&nbsp;=&nbsp;&#39;nearest&#39;
plt.rcParams[&#39;image.cmap&#39;]&nbsp;=&nbsp;&#39;gray&#39;
#&nbsp;load&nbsp;image&nbsp;dataset:&nbsp;blue/red&nbsp;dots&nbsp;in&nbsp;circles
train_X,&nbsp;train_Y,&nbsp;test_X,&nbsp;test_Y&nbsp;=&nbsp;load_dataset()</pre><p style="margin-top: auto; margin-bottom: auto; text-align: center;"><span style="font-size:16px;font-family:宋体"></span><img src="/wp-content/uploads/image/20180206/1517931363840180.jpg" title="1517931363840180.jpg" alt="1.jpg"/></p><p style="margin-top:auto;margin-bottom: auto;text-align:left"><strong><span style="font-size:16px;font-family:宋体"><br/></span></strong></p><p style="margin-top:auto;margin-bottom: auto;text-align:left"><strong><span style="font-size:16px;font-family:宋体"></span></strong></p><h2>1 – 深度网络模型</h2><p>你将使用三层网络模型（该模型已经提供给你）。这里有三种可以使用的初始化方式：</p><ul class=" list-paddingleft-2"><li><p><em><span style="font-family:等线">Zeros initialization</span></em> -- setting <code><span style="font-size:      16px">initialization = &quot;zeros&quot;</span></code> &nbsp; &nbsp; &nbsp;in the input argument.</p></li><li><p><em><span style="font-family:等线">Random initialization</span></em> -- setting <code><span style="font-size:      16px">initialization = &quot;random&quot;</span></code> &nbsp; &nbsp; &nbsp;in the input argument. This initializes the weights to large random &nbsp; &nbsp; &nbsp;values.</p></li><li><p><em><span style="font-family:等线">He initialization</span></em> -- setting <code><span style="font-size:      16px">initialization = &quot;he&quot;</span></code> in &nbsp; &nbsp; &nbsp;the input argument. This initializes the weights to random values scaled &nbsp; &nbsp; &nbsp;according to a paper by He et al., 2015.</p></li></ul><p><strong><span style="font-family:宋体">Instructions</span></strong>: 请快速阅读下面的代码，并运行它。 在下一部分中，您将实现这个model()调用的三个初始化方法。</p><p style="margin-top:auto;margin-bottom: auto;text-align:left"><span style="font-size:16px;font-family:宋体"></span></p><pre class="brush:python;toolbar:false">def&nbsp;model(X,Y,learning_rate=0.01,num_iterations=15000,
print_cost=True,initialization=&quot;he&quot;):
&nbsp;&nbsp;&nbsp;&nbsp;&quot;&quot;&quot;
&nbsp;&nbsp;&nbsp;&nbsp;Implements&nbsp;a&nbsp;three-layer&nbsp;neural&nbsp;network:
&nbsp;&nbsp;&nbsp;&nbsp;LINEAR-&gt;RELU-&gt;LINEAR-&gt;RELU-&gt;LINEAR-&gt;SIGMOID.

&nbsp;&nbsp;&nbsp;&nbsp;&quot;&quot;&quot;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;grads&nbsp;=&nbsp;{}
&nbsp;&nbsp;&nbsp;&nbsp;costs&nbsp;=&nbsp;[]&nbsp;#&nbsp;to&nbsp;keep&nbsp;track&nbsp;of&nbsp;the&nbsp;loss
&nbsp;&nbsp;&nbsp;&nbsp;m&nbsp;=&nbsp;X.shape[1]&nbsp;#&nbsp;number&nbsp;of&nbsp;examples
&nbsp;&nbsp;&nbsp;&nbsp;layers_dims&nbsp;=&nbsp;[X.shape[0],&nbsp;10,&nbsp;5,&nbsp;1]
&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;#&nbsp;Initialize&nbsp;parameters&nbsp;dictionary.
&nbsp;&nbsp;&nbsp;&nbsp;if&nbsp;initialization&nbsp;==&nbsp;&quot;zeros&quot;:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;parameters&nbsp;=&nbsp;initialize_parameters_zeros(layers_dims)
&nbsp;&nbsp;&nbsp;&nbsp;elif&nbsp;initialization&nbsp;==&nbsp;&quot;random&quot;:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;parameters&nbsp;=&nbsp;initialize_parameters_random(layers_dims)
&nbsp;&nbsp;&nbsp;&nbsp;elif&nbsp;initialization&nbsp;==&nbsp;&quot;he&quot;:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;parameters&nbsp;=&nbsp;initialize_parameters_he(layers_dims)
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;#&nbsp;Loop&nbsp;(gradient&nbsp;descent)
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;for&nbsp;i&nbsp;in&nbsp;range(0,&nbsp;num_iterations):
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;#&nbsp;Forward&nbsp;propagation:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;#LINEAR-&gt;RELU-&gt;LINEAR-&gt;RELU-&gt;LINEAR-&gt;SIGMOID.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;a3,&nbsp;cache&nbsp;=&nbsp;forward_propagation(X,&nbsp;parameters)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;#&nbsp;Loss
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;cost&nbsp;=&nbsp;compute_loss(a3,&nbsp;Y)
&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;#&nbsp;Backward&nbsp;propagation.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;grads&nbsp;=&nbsp;backward_propagation(X,&nbsp;Y,&nbsp;cache)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;#&nbsp;Update&nbsp;parameters.
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;parameters&nbsp;=&nbsp;update_parameters(parameters,&nbsp;grads,&nbsp;learning_rate)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;#&nbsp;Print&nbsp;the&nbsp;loss&nbsp;every&nbsp;1000&nbsp;iterations
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;if&nbsp;print_cost&nbsp;and&nbsp;i&nbsp;%&nbsp;1000&nbsp;==&nbsp;0:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;print(&quot;Cost&nbsp;after&nbsp;iteration&nbsp;{}:&nbsp;{}&quot;.format(i,&nbsp;cost))
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;costs.append(cost)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;#&nbsp;plot&nbsp;the&nbsp;loss
&nbsp;&nbsp;&nbsp;&nbsp;plt.plot(costs)
&nbsp;&nbsp;&nbsp;&nbsp;plt.ylabel(&#39;cost&#39;)
&nbsp;&nbsp;&nbsp;&nbsp;plt.xlabel(&#39;iterations&nbsp;(per&nbsp;hundreds)&#39;)
&nbsp;&nbsp;&nbsp;&nbsp;plt.title(&quot;Learning&nbsp;rate&nbsp;=&quot;&nbsp;+&nbsp;str(learning_rate))
&nbsp;&nbsp;&nbsp;&nbsp;plt.show()
&nbsp;&nbsp;&nbsp;&nbsp;
return&nbsp;parameters</pre><h2>2 – 零初始化</h2><p>两种在深度网络中进行初始化的参数:</p><ul class=" list-paddingleft-2"><li><p>深度网络<span style="font-size:19px;font-family:&#39;STIXMathJax_Main&#39;,serif">(</span><span style="display:inline-block"><em><span style="font-size: 19px; font-family: &quot;STIXMathJax_Main&quot;, serif; clip: rect(3.157em, 1000.91em, 4.185em, -1000em);">W</span></em></span>[<span style="font-size:      13px;font-family:&#39;STIXMathJax_Main&#39;,serif">1]</span>,<span style="display:inline-block"><em><span style="font-size: 19px; font-family: &quot;STIXMathJax_Main&quot;, serif; clip: rect(3.157em, 1000.91em, 4.185em, -1000em);">W</span></em></span>[<span style="font-size:13px;font-family:&#39;STIXMathJax_Main&#39;,serif">2]</span>,<span style="display:inline-block"><em><span style="font-size: 19px; font-family: &quot;STIXMathJax_Main&quot;, serif; clip: rect(3.157em, 1000.91em, 4.185em, -1000em);">W</span></em></span>[<span style="font-size:13px;font-family:&#39;STIXMathJax_Main&#39;,serif">3]</span>,...,<span style="display:inline-block"><em><span style="font-size: 19px; font-family: &quot;STIXMathJax_Main&quot;, serif; clip: rect(3.157em, 1000.91em, 4.185em, -1000em);">W</span></em></span>[<em><span style="font-size:13px;font-family:&#39;STIXMathJax_Main&#39;,serif">L</span></em>−<span style="font-size:13px;font-family:&#39;STIXMathJax_Main&#39;,serif">1]</span>,<span style="display:inline-block"><em><span style="font-size: 19px; font-family: &quot;STIXMathJax_Main&quot;, serif; clip: rect(3.157em, 1000.91em, 4.185em, -1000em);">W</span></em></span>[<em><span style="font-size:13px;font-family:&#39;STIXMathJax_Main&#39;,serif">L</span></em>])(W[1],W[2],W[3],...,W[L<span style="font-family:&#39;微软雅黑&#39;,sans-serif">−</span>1],W[L])</p></li><li><p><span style="font-size:19px">偏差值向量</span><span style="font-size:19px;font-family:&#39;STIXMathJax_Main&#39;,serif">(</span><span style="display:inline-block"><em><span style="font-size: 19px; font-family: &quot;STIXMathJax_Main&quot;, serif; clip: rect(3.127em, 1000.47em, 4.178em, -1000em);">b</span></em></span>[<span style="font-size:13px;font-family:&#39;STIXMathJax_Main&#39;,serif">1]</span>,<span style="display:inline-block"><em><span style="font-size: 19px; font-family: &quot;STIXMathJax_Main&quot;, serif; clip: rect(3.127em, 1000.47em, 4.178em, -1000em);">b</span></em></span>[<span style="font-size:13px;font-family:&#39;STIXMathJax_Main&#39;,serif">2]</span>,<span style="display:inline-block"><em><span style="font-size: 19px; font-family: &quot;STIXMathJax_Main&quot;, serif; clip: rect(3.127em, 1000.47em, 4.178em, -1000em);">b</span></em></span>[<span style="font-size:13px;font-family:&#39;STIXMathJax_Main&#39;,serif">3]</span>,...,<span style="display:inline-block"><em><span style="font-size: 19px; font-family: &quot;STIXMathJax_Main&quot;, serif; clip: rect(3.127em, 1000.47em, 4.178em, -1000em);">b</span></em></span>[<em><span style="font-size:13px;font-family:&#39;STIXMathJax_Main&#39;,serif">L</span></em>−<span style="font-size:13px;font-family:&#39;STIXMathJax_Main&#39;,serif">1]</span>,<span style="display:inline-block"><em><span style="font-size: 19px; font-family: &quot;STIXMathJax_Main&quot;, serif; clip: rect(3.127em, 1000.47em, 4.178em, -1000em);">b</span></em></span>[<em><span style="font-size:13px;font-family:&#39;STIXMathJax_Main&#39;,serif">L</span></em>])(b[1],b[2],b[3],...,b[L<span style="font-family:&#39;微软雅黑&#39;,sans-serif">−</span>1],b[L])</p><p><strong><span style="font-family:宋体">Exercise</span></strong>: Implement the following function to initialize all parameters to zeros. You&#39;ll see later that this does not work well since it fails to &quot;break symmetry&quot;, but lets try it anyway and see what happens. Use np.zeros((..,..)) with the correct shapes.</p><p><br/></p><p><br/></p><p style="margin-top:auto;margin-bottom: auto;text-align:left"><span style="font-size:16px;font-family:宋体">用以下代码来做测试：</span></p><p style="margin-top:auto;margin-bottom: auto;text-align:left"><span style="font-size:16px;font-family:宋体"></span></p><p style="margin-top:auto;margin-bottom: auto;text-align:left"><span style="font-size:16px;font-family:宋体"></span></p></li><li><pre class="brush:python;toolbar:false">#&nbsp;GRADED&nbsp;FUNCTION:&nbsp;initialize_parameters_zeros
def&nbsp;initialize_parameters_zeros(layers_dims):
&nbsp;&nbsp;&nbsp;&nbsp;&quot;&quot;&quot;
&nbsp;&nbsp;&nbsp;&nbsp;Arguments:
&nbsp;&nbsp;&nbsp;&nbsp;layer_dims&nbsp;--&nbsp;python&nbsp;array&nbsp;(list)&nbsp;containing&nbsp;the&nbsp;size&nbsp;of&nbsp;each&nbsp;layer.
&nbsp;&nbsp;&nbsp;&nbsp;Returns:
&nbsp;&nbsp;&nbsp;&nbsp;parameters&nbsp;--&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;python&nbsp;dictionary&nbsp;containing&nbsp;your&nbsp;parameters&nbsp;&quot;W1&quot;,&nbsp;&quot;b1&quot;,&nbsp;...,&nbsp;&quot;WL&quot;,&nbsp;&quot;bL&quot;:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;W1&nbsp;--&nbsp;weight&nbsp;matrix&nbsp;of&nbsp;shape&nbsp;(layers_dims[1],&nbsp;layers_dims[0])
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;b1&nbsp;--&nbsp;bias&nbsp;vector&nbsp;of&nbsp;shape&nbsp;(layers_dims[1],&nbsp;1)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;WL&nbsp;--&nbsp;weight&nbsp;matrix&nbsp;of&nbsp;shape&nbsp;(layers_dims[L],&nbsp;layers_dims[L-1])
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;bL&nbsp;--&nbsp;bias&nbsp;vector&nbsp;of&nbsp;shape&nbsp;(layers_dims[L],&nbsp;1)
&nbsp;&nbsp;&nbsp;&nbsp;&quot;&quot;&quot;
&nbsp;&nbsp;&nbsp;&nbsp;parameters&nbsp;=&nbsp;{}
&nbsp;&nbsp;&nbsp;&nbsp;L&nbsp;=&nbsp;len(layers_dims)#&nbsp;number&nbsp;of&nbsp;layers&nbsp;in&nbsp;the&nbsp;network
&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;for&nbsp;l&nbsp;in&nbsp;range(1,&nbsp;L):
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;###&nbsp;START&nbsp;CODE&nbsp;HERE&nbsp;###&nbsp;(≈&nbsp;2&nbsp;lines&nbsp;of&nbsp;code)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;parameters[&#39;W&#39;&nbsp;+&nbsp;str(l)]&nbsp;=&nbsp;np.zeros((layers_dims[1],&nbsp;layers_dims[0]))&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;if&nbsp;l&nbsp;==&nbsp;1&nbsp;else&nbsp;np.zeros((layers_dims[l],&nbsp;layers_dims[l-1]))
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;parameters[&#39;b&#39;&nbsp;+&nbsp;str(l)]&nbsp;=&nbsp;np.zeros((layers_dims[l],&nbsp;1))
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;###&nbsp;END&nbsp;CODE&nbsp;HERE&nbsp;###
&nbsp;&nbsp;&nbsp;&nbsp;return&nbsp;parameters</pre></li><li><pre class="brush:python;toolbar:false">parameters&nbsp;=&nbsp;model(train_X,&nbsp;train_Y,&nbsp;initialization&nbsp;=&nbsp;&quot;zeros&quot;)
print&nbsp;(&quot;On&nbsp;the&nbsp;train&nbsp;set:&quot;)
predictions_train&nbsp;=&nbsp;predict(train_X,&nbsp;train_Y,&nbsp;parameters)
print&nbsp;(&quot;On&nbsp;the&nbsp;test&nbsp;set:&quot;)
predictions_test&nbsp;=&nbsp;predict(test_X,&nbsp;test_Y,&nbsp;parameters)</pre></li></ul><p style="margin-top:auto;margin-bottom: auto;text-align:left;text-indent:32px"><span style="font-size:16px;font-family:宋体"></span>Cost after iteration 0: 0.6931471805599453<br/>Cost after iteration 1000: 0.6931471805599453<br/>Cost after iteration 2000: 0.6931471805599453<br/>Cost after iteration 3000: 0.6931471805599453<br/>Cost after iteration 4000: 0.6931471805599453<br/>Cost after iteration 5000: 0.6931471805599453<br/>Cost after iteration 6000: 0.6931471805599453<br/>Cost after iteration 7000: 0.6931471805599453<br/>Cost after iteration 8000: 0.6931471805599453<br/>Cost after iteration 9000: 0.6931471805599453<br/>Cost after iteration 10000: 0.6931471805599455<br/>Cost after iteration 11000: 0.6931471805599453<br/>Cost after iteration 12000: 0.6931471805599453<br/>Cost after iteration 13000: 0.6931471805599453<br/>Cost after iteration 14000: 0.6931471805599453<br/></p><p style="text-align:center"><img src="/wp-content/uploads/image/20180206/1517931521181830.jpg" title="1517931521181830.jpg" alt="2.jpg"/></p><p style="margin-top:auto;margin-bottom: auto;text-align:left;text-indent:32px">On the train set:</p><p style="margin-top:auto;margin-bottom: auto;text-align:left;text-indent:32px">Accuracy: 0.5</p><p style="margin-top:auto;margin-bottom: auto;text-align:left;text-indent:32px">On the test set:</p><p style="margin-top:auto;margin-bottom: auto;text-align:left;text-indent:32px">Accuracy: 0.5</p><p style="margin-top:auto;margin-bottom: auto;text-align:left;text-indent:32px"><br/></p><p>可以看出，性能表现非常差，代价函数也没有任何下降，这个算法的表现都不如自己随机猜一个好。这是为什么呢？让我们来看一下预测和决策边界的详细情况：<br/></p><pre class="brush:python;toolbar:false">print&nbsp;(&quot;predictions_train&nbsp;=&nbsp;&quot;&nbsp;+&nbsp;str(predictions_train))
print&nbsp;(&quot;predictions_test&nbsp;=&nbsp;&quot;&nbsp;+&nbsp;str(predictions_test))</pre><p><br/>&nbsp;<br/>该模型预测每个例子均为0。<br/>一般来说，将所有权重初始化为零将导致网络无法破坏对称性。&nbsp;这意味着每一层中的每一个神经元都会学到相同的东西，而且你也可以用n&nbsp;[l]&nbsp;=&nbsp;1n&nbsp;[l]&nbsp;=&nbsp;1来训练一个神经网络，而且网络没有如逻辑回归之类的线性分类器那么强大。<br/><br/></p><p style="margin-top:auto;margin-bottom: auto;text-align:left"><span style="color: #FF0000;"><strong><span style="font-size: 16px; font-family: 宋体;">你需要记住的是：</span></strong></span></p><ul class=" list-paddingleft-2"><li><p><span style="font-size: 16px; font-family: 宋体; color: #FF0000;">为了打破对称，权重W[l]应当被随机初始化。</span></p></li><li><p><span style="font-size: 16px; font-family: 宋体; color: #FF0000;">将b[l]初始化为0是可以的，只要权重矩阵随机初始化就可以打破对称性。</span></p><p><span style="font-size: 16px; font-family: 宋体; color: #FF0000;"></span></p></li></ul><p><br/></p><h2>3 – 随机初始化</h2><p>为了打破对称，现在随机初始化权重矩阵。随机初始化之后，每个神经元可以继续学习其输入的不同功能。 在这个练习中，你会看到如果权重是随机初始化会发生什么情况，但是会看到非常大的值。</p><p><strong><span style="font-family:宋体">Exercise</span></strong>: 执行接下来的函数来用较大的数值进行随机初始化，将偏差值初始化为0。Use <code>np.random.randn(..,..) * 10</code> for weights and <code>np.zeros((.., ..))</code> for biases. We are using a fixed <code>np.random.seed(..)</code> to make sure your &quot;random&quot; weights match ours, so don&#39;t worry if running several times your code gives you always the same initial values for the parameters.</p><p style="margin-top:auto;margin-bottom: auto;text-align:left"><span style="font-size:16px;font-family:宋体"></span></p><pre class="brush:python;toolbar:false">#&nbsp;GRADED&nbsp;FUNCTION:&nbsp;initialize_parameters_random
&nbsp;
def&nbsp;initialize_parameters_random(layers_dims):
&nbsp;&nbsp;&nbsp;&nbsp;&quot;&quot;&quot;
&nbsp;&nbsp;&nbsp;&nbsp;Arguments:
&nbsp;&nbsp;&nbsp;&nbsp;layer_dims&nbsp;--&nbsp;python&nbsp;array&nbsp;(list)&nbsp;containing&nbsp;the&nbsp;size&nbsp;of&nbsp;each&nbsp;layer.
&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;Returns:
&nbsp;&nbsp;&nbsp;&nbsp;parameters--python&nbsp;dictionary&nbsp;containing&nbsp;your&nbsp;parameters&quot;W1&quot;,&quot;b1&quot;,...,&quot;WL&quot;,&quot;bL&quot;:
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;W1&nbsp;--&nbsp;weight&nbsp;matrix&nbsp;of&nbsp;shape&nbsp;(layers_dims[1],&nbsp;layers_dims[0])
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;b1&nbsp;--&nbsp;bias&nbsp;vector&nbsp;of&nbsp;shape&nbsp;(layers_dims[1],&nbsp;1)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;WL&nbsp;--&nbsp;weight&nbsp;matrix&nbsp;of&nbsp;shape&nbsp;(layers_dims[L],&nbsp;layers_dims[L-1])
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;bL&nbsp;--&nbsp;bias&nbsp;vector&nbsp;of&nbsp;shape&nbsp;(layers_dims[L],&nbsp;1)
&nbsp;&nbsp;&nbsp;&nbsp;&quot;&quot;&quot;
&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;np.random.seed(3)&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;#&nbsp;This&nbsp;seed&nbsp;makes&nbsp;sure&nbsp;your&nbsp;&quot;random&quot;&nbsp;numbers&nbsp;will&nbsp;be&nbsp;the&nbsp;as&nbsp;ours
&nbsp;&nbsp;&nbsp;&nbsp;parameters&nbsp;=&nbsp;{}
&nbsp;&nbsp;&nbsp;&nbsp;L&nbsp;=&nbsp;len(layers_dims)&nbsp;#&nbsp;integer&nbsp;representing&nbsp;the&nbsp;number&nbsp;of&nbsp;layers
&nbsp;&nbsp;&nbsp;&nbsp;print(&quot;shuzhi&nbsp;is&nbsp;&quot;&nbsp;+&nbsp;str(L))
&nbsp;&nbsp;&nbsp;&nbsp;for&nbsp;l&nbsp;in&nbsp;range(1,&nbsp;L):#range(1,L)={1,2,3...,L-1}
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;###&nbsp;START&nbsp;CODE&nbsp;HERE&nbsp;###&nbsp;(≈&nbsp;2&nbsp;lines&nbsp;of&nbsp;code)
&nbsp;&nbsp;&nbsp;&nbsp;parameters[&#39;W&#39;+str(l)]=np.random.randn(layers_dims[1],layers_dims[0])*10&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;if&nbsp;l==1&nbsp;else&nbsp;np.random.randn(layers_dims[l],layers_dims[l-1])*10
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;parameters[&#39;b&#39;&nbsp;+&nbsp;str(l)]&nbsp;=&nbsp;np.zeros((layers_dims[l],&nbsp;1))
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;###&nbsp;END&nbsp;CODE&nbsp;HERE&nbsp;###
return&nbsp;parameters</pre><p style="margin-top:auto;margin-bottom: auto;text-align:left;text-indent:32px"><span style="font-size:16px;font-family:宋体"></span><br/></p><p style="margin-top:auto;margin-bottom: auto;text-align:left"><span style="font-size:16px;font-family:宋体">测试代码：</span></p><p style="margin-top:auto;margin-bottom: auto;text-align:left"><span style="font-size:16px;font-family:宋体"></span></p><pre class="brush:python;toolbar:false">parameters=&nbsp;initialize_parameters_random([4,&nbsp;2,&nbsp;1])
print(&quot;W1&nbsp;=&nbsp;&quot;&nbsp;+&nbsp;str(parameters[&quot;W1&quot;]))
print(&quot;b1&nbsp;=&nbsp;&quot;&nbsp;+&nbsp;str(parameters[&quot;b1&quot;]))
print(&quot;W2&nbsp;=&nbsp;&quot;&nbsp;+&nbsp;str(parameters[&quot;W2&quot;]))
print(&quot;b2&nbsp;=&nbsp;&quot;&nbsp;+&nbsp;str(parameters[&quot;b2&quot;]))</pre><p style="margin-top:auto;margin-bottom: auto;text-align:left"><span style="font-size:16px;font-family:宋体"></span><br/></p><p style="margin-top:auto;margin-bottom: auto;text-align:left"><span style="font-size:16px;font-family:宋体">做15000次迭代代码：</span></p><p style="margin-top:auto;margin-bottom: auto;text-align:left"><span style="font-size:16px;font-family:宋体"></span></p><pre class="brush:python;toolbar:false">parameters&nbsp;=&nbsp;model(train_X,&nbsp;train_Y,&nbsp;initialization&nbsp;=&nbsp;&quot;random&quot;)
print&nbsp;(&quot;On&nbsp;the&nbsp;train&nbsp;set:&quot;)
predictions_train&nbsp;=&nbsp;predict(train_X,&nbsp;train_Y,&nbsp;parameters)
print&nbsp;(&quot;On&nbsp;the&nbsp;test&nbsp;set:&quot;)
predictions_test&nbsp;=&nbsp;predict(test_X,&nbsp;test_Y,&nbsp;parameters)</pre><p style="margin-top:auto;margin-bottom: auto;text-align:left"><span style="font-size:16px;font-family:宋体"></span>Cost after iteration 0: inf<br/>Cost after iteration 1000: 0.6237287551108738<br/>Cost after iteration 2000: 0.5981106708339466<br/>Cost after iteration 3000: 0.5638353726276827<br/>Cost after iteration 4000: 0.550152614449184<br/>Cost after iteration 5000: 0.5444235275228304<br/>Cost after iteration 6000: 0.5374184054630083<br/>Cost after iteration 7000: 0.47357131493578297<br/>Cost after iteration 8000: 0.39775634899580387<br/>Cost after iteration 9000: 0.3934632865981078<br/>Cost after iteration 10000: 0.39202525076484457<br/>Cost after iteration 11000: 0.38921493051297673<br/>Cost after iteration 12000: 0.38614221789840486<br/>Cost after iteration 13000: 0.38497849983013926<br/>Cost after iteration 14000: 0.38278397192120406</p><p style="margin-top: auto; margin-bottom: auto; text-align: center;"><img src="/wp-content/uploads/image/20180206/1517931768760767.jpg" title="1517931768760767.jpg" alt="3.jpg"/></p><p style="margin-top: auto; margin-bottom: auto;">On the train set:<br/>Accuracy: 0.83<br/>On the test set:<br/>Accuracy: 0.86</p><p style="margin-top:auto;margin-bottom: auto;text-align:left"><span style="font-size:16px;font-family:宋体">如果您看到“inf”作为迭代0之后的成本，这是因为数值舍入，一个更复杂的实现可以解决这个问题。 但是这不值得为我们的目的而担心。</span></p><p style="margin-top:auto;margin-bottom: auto;text-align:left;text-indent:32px"><span style="font-size:16px;font-family:宋体">无论如何，看起来已经失去了对称性，这样会有更好的结果。相比以前来说，该模型不再输出全0。</span></p><p style="margin-top:auto;margin-bottom: auto;text-align:left"><span style="font-size:16px;font-family:宋体">观察：</span></p><p style="margin-top:auto;margin-bottom: auto;text-align:left"><span style="font-size:16px;font-family:宋体">&nbsp;&nbsp;&nbsp;&nbsp; </span><span style="font-size: 16px;font-family:宋体">代价函数在开始的时候非常高。 这是因为对于大的随机值权重，最后一次激活（sigmoid）输出的结果非常接近于0或1，并且当这个例子错误时，这个例子会导致很高的损失。 事实上，当log（a [3]）= log（0）log</span><span style="font-size:16px;font-family:&#39;Cambria&#39;,serif">⁡</span><span style="font-size:16px;font-family:宋体">（a [3]）=log</span><span style="font-size:16px;font-family:&#39;Cambria&#39;,serif">⁡</span><span style="font-size:16px;font-family:宋体">（0）时，损失趋于无穷大。</span></p><p style="margin-top:auto;margin-bottom: auto;text-align:left"><span style="font-size:16px;font-family:宋体">&nbsp;&nbsp;&nbsp;&nbsp; </span><span style="font-size: 16px;font-family:宋体">初始化不良会导致渐变/爆炸渐变，这也会减慢优化算法的速度。</span></p><p style="margin-top:auto;margin-bottom: auto;text-align:left"><span style="font-size:16px;font-family:宋体">&nbsp;&nbsp;&nbsp;&nbsp; </span><span style="font-size: 16px;font-family:宋体">如果你长时间训练这个网络，你会看到更好的结果，但是用过大的随机数初始化会减慢优化速度。</span></p><p style="margin-top:auto;margin-bottom: auto;text-align:left"><span style="font-size:16px;font-family:宋体;color:blue">总结: </span></p><ul class=" list-paddingleft-2"><li><p><span style="font-size:16px;font-family:宋体">初始化权重矩阵的值非常大的结果并不好。</span></p></li><li><p><span style="font-size:16px;font-family:宋体;color:blue">较小随机值的理想随机表现的更好。</span></p></li></ul><p style="margin-top:auto;margin-bottom: auto;text-align:left;text-indent:32px"><span style="font-size:16px;font-family:宋体;color:blue">但是现在有一个关键问题：这些值多小才是真正的小呢？让我们在下一节来完成这个问题。</span></p><h2>4 – He初始化</h2><p>最后，尝试使用“HE初始化”。If you have heard of &quot;Xavier initialization&quot;, this is similar except Xavier initialization uses a scaling factor for the weights <span style="color:inherit"><span style="display:inline-block"><span style="display:inline-block"><span style="clip:rect(1.237em, 1001.73em, 2.458em, -1000em)"><span style="display:inline-block"><span style="clip:rect(3.157em, 1000.91em, 4.185em, -1000em)">W[l]</span></span> of <code>sqrt(1./layers_dims[l-1])</code> where He initialization would use <code>sqrt(2./layers_dims[l-1])</code>.)</span></span></span></span></p><p><strong><span style="font-family:宋体">Exercise</span></strong>: Implement the following function to initialize your parameters with He initialization.</p><p><strong><span style="font-family:宋体">Hint</span></strong>: This function is similar to the previous <code>initialize_parameters_random(...)</code>. The only difference is that instead of multiplying <code>np.random.randn(..,..)</code> by 10, you will multiply it byof the previous layer, which is what He initialization recommends for layers with a ReLU activation.</p><p style="margin-top:auto;margin-bottom: auto;text-align:left"><span style="font-size:16px;font-family:宋体"></span></p><pre class="brush:python;toolbar:false">#&nbsp;GRADED&nbsp;FUNCTION:&nbsp;initialize_parameters_he
&nbsp;
def&nbsp;initialize_parameters_he(layers_dims):
&nbsp;&nbsp;&nbsp;&nbsp;&quot;&quot;&quot;
&nbsp;&nbsp;&nbsp;&nbsp;Arguments:
&nbsp;&nbsp;&nbsp;&nbsp;layer_dims&nbsp;--&nbsp;python&nbsp;array&nbsp;(list)&nbsp;containing&nbsp;the&nbsp;size&nbsp;of&nbsp;each&nbsp;layer.
&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;Returns:
&nbsp;&nbsp;parameters-
&nbsp;&nbsp;python&nbsp;dictionary&nbsp;containing&nbsp;your&nbsp;parameters&nbsp;&quot;W1&quot;,&quot;b1&quot;,...,&quot;WL&quot;,&quot;bL&quot;:
&nbsp;&nbsp;&nbsp;W1&nbsp;--&nbsp;weight&nbsp;matrix&nbsp;of&nbsp;shape&nbsp;(layers_dims[1],&nbsp;layers_dims[0])
&nbsp;&nbsp;&nbsp;b1&nbsp;--&nbsp;bias&nbsp;vector&nbsp;of&nbsp;shape&nbsp;(layers_dims[1],&nbsp;1)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...
&nbsp;&nbsp;&nbsp;WL&nbsp;--&nbsp;weight&nbsp;matrix&nbsp;of&nbsp;shape&nbsp;(layers_dims[L],&nbsp;layers_dims[L-1])
&nbsp;&nbsp;&nbsp;bL&nbsp;--&nbsp;bias&nbsp;vector&nbsp;of&nbsp;shape&nbsp;(layers_dims[L],&nbsp;1)
&nbsp;&nbsp;&nbsp;&nbsp;&quot;&quot;&quot;
&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;np.random.seed(3)
&nbsp;&nbsp;&nbsp;&nbsp;parameters&nbsp;=&nbsp;{}
&nbsp;&nbsp;&nbsp;&nbsp;L&nbsp;=&nbsp;len(layers_dims)&nbsp;-&nbsp;1&nbsp;#&nbsp;integer&nbsp;representing&nbsp;the&nbsp;number&nbsp;of&nbsp;layers
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
&nbsp;&nbsp;&nbsp;&nbsp;for&nbsp;l&nbsp;in&nbsp;range(1,&nbsp;L&nbsp;+&nbsp;1):
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;###&nbsp;START&nbsp;CODE&nbsp;HERE&nbsp;###&nbsp;(≈&nbsp;2&nbsp;lines&nbsp;of&nbsp;code)
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;parameters[&#39;W&#39;+str(l)]=
&nbsp;&nbsp;&nbsp;&nbsp;np.random.randn(layers_dims[1],layers_dims[0])*np.sqrt(2./layers_dims[0])
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;if&nbsp;l&nbsp;==&nbsp;1&nbsp;else&nbsp;np.random.randn(layers_dims[l],layers_dims[l-1])*
&nbsp;&nbsp;&nbsp;np.sqrt(2./layers_dims[l-1])
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;parameters[&#39;b&#39;&nbsp;+&nbsp;str(l)]&nbsp;=&nbsp;np.zeros((layers_dims[1],&nbsp;1))
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;###&nbsp;END&nbsp;CODE&nbsp;HERE&nbsp;###
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
return&nbsp;parameters</pre><p style="margin-top:auto;margin-bottom: auto;text-align:left;text-indent:32px"><span style="font-size:16px;font-family:宋体"></span><br/></p><p style="margin-top:auto;margin-bottom: auto;text-align:left;text-indent:32px"><span style="font-size:16px;font-family:宋体">测试代码：</span></p><p style="margin-top:auto;margin-bottom: auto;text-align:left"><span style="font-size:16px;font-family:宋体"></span></p><pre class="brush:python;toolbar:false">parameters&nbsp;=&nbsp;initialize_parameters_he([2,&nbsp;4,&nbsp;1])
print(&quot;W1&nbsp;=&nbsp;&quot;&nbsp;+&nbsp;str(parameters[&quot;W1&quot;]))
print(&quot;b1&nbsp;=&nbsp;&quot;&nbsp;+&nbsp;str(parameters[&quot;b1&quot;]))
print(&quot;W2&nbsp;=&nbsp;&quot;&nbsp;+&nbsp;str(parameters[&quot;W2&quot;]))
print(&quot;b2&nbsp;=&nbsp;&quot;&nbsp;+&nbsp;str(parameters[&quot;b2&quot;]))</pre><p style="margin-top:auto;margin-bottom: auto;text-align:left"><span style="font-size:16px;font-family:宋体"></span></p><h2>5 – 结论</h2><p>在相同迭代次数和相同超参数下，其结果如表所示：</p><table><tbody><tr class="firstRow"><td style="border:solid windowtext 1px;padding:0 7px 0 7px" valign="top"><p style="text-align:left"><strong><span style="font-size:16px;font-family:宋体">Model</span></strong> </p></td><td style="border:solid windowtext 1px;border-left:none;padding:0 7px 0 7px" valign="top"><p style="text-align:left"><strong><span style="font-size:16px;font-family:宋体">Train accuracy</span></strong> </p></td><td style="border:solid windowtext 1px;border-left:none;padding:0 7px 0 7px" valign="top"><p style="text-align:left"><strong><span style="font-size:16px;font-family:宋体">Problem/Comment</span></strong> </p></td></tr><tr><td style="border:solid windowtext 1px;border-top:none;padding:0 7px 0 7px" valign="top"><p style="text-align:left"><span style="font-size:16px;font-family:宋体">3-layer NN with zeros initialization </span></p></td><td style="border-top:none;border-left:none;border-bottom:solid windowtext 1px;border-right:solid windowtext 1px;padding:0 7px 0 7px" valign="top"><p style="text-align:left"><span style="font-size:16px;font-family:宋体">50% </span></p></td><td style="border-top:none;border-left:none;border-bottom:solid windowtext 1px;border-right:solid windowtext 1px;padding:0 7px 0 7px" valign="top"><p style="text-align:left"><span style="font-size:16px;font-family:宋体">fails to break symmetry </span></p></td></tr><tr><td style="border:solid windowtext 1px;border-top:none;padding:0 7px 0 7px" valign="top"><p style="text-align:left"><span style="font-size:16px;font-family:宋体">3-layer NN with large random initialization </span></p></td><td style="border-top:none;border-left:none;border-bottom:solid windowtext 1px;border-right:solid windowtext 1px;padding:0 7px 0 7px" valign="top"><p style="text-align:left"><span style="font-size:16px;font-family:宋体">83% </span></p></td><td style="border-top:none;border-left:none;border-bottom:solid windowtext 1px;border-right:solid windowtext 1px;padding:0 7px 0 7px" valign="top"><p style="text-align:left"><span style="font-size:16px;font-family:宋体">too large weights </span></p></td></tr><tr><td style="border:solid windowtext 1px;border-top:none;padding:0 7px 0 7px" valign="top"><p style="text-align:left"><span style="font-size:16px;font-family:宋体">3-layer NN with He initialization </span></p></td><td style="border-top:none;border-left:none;border-bottom:solid windowtext 1px;border-right:solid windowtext 1px;padding:0 7px 0 7px" valign="top"><p style="text-align:left"><span style="font-size:16px;font-family:宋体">99% </span></p></td><td style="border-top:none;border-left:none;border-bottom:solid windowtext 1px;border-right:solid windowtext 1px;padding:0 7px 0 7px" valign="top"><p style="text-align:left"><span style="font-size:16px;font-family:宋体">recommended method</span></p></td></tr></tbody></table><p style="margin-top:auto;margin-bottom: auto;text-align:left">结论：<br/> （1）不同的初始化导致不同的结果<br/> （2）随机初始化用于破坏对称性，并确保不同的隐藏单元可以学习不同的东西<br/> （3）不要初始化太大的值<br/> （4）HE初始化适用于ReLU激活的网络。</p><p style="margin-top: auto; margin-bottom: auto;"><br/></p>