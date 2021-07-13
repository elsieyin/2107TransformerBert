

![image-20210630150938954](C:%5CUsers%5C86182%5CAppData%5CRoaming%5CTypora%5Ctypora-user-images%5Cimage-20210630150938954.png)



**输入**  input embedding-- > positional encoding

​		for i in range (6) :
**encoder**  self attention--> layer normalization
​		-- >feed forward-->layer normalization
​		for i in range (6) :
​		
**decoder** self attention--> layer normalization
​		-->encoder-decoder attention-->
​		layer normalization-->feed forward-->layer normalization

输入
x1:[batch_size,1,embedding_dim=512]
x2:[batch_size,1,embedding_dim=512]

维度
[batch_size,sequence_length,embedding_dim]

![image-20210630151213422](C:%5CUsers%5C86182%5CAppData%5CRoaming%5CTypora%5Ctypora-user-images%5Cimage-20210630151213422.png)

![image-20210630151154638](C:%5CUsers%5C86182%5CAppData%5CRoaming%5CTypora%5Ctypora-user-images%5Cimage-20210630151154638.png)

前馈层:包含两层。1、线性结构，2、卷积结构
x:上一层的输出（─般是self-attention的输出)W1、W2、b1、b2都是需要学习的参数

![image-20210630151133460](C:%5CUsers%5C86182%5CAppData%5CRoaming%5CTypora%5Ctypora-user-images%5Cimage-20210630151133460.png)

硬件:8块NVIDIA P100 GPU
优化器:  Adam,β 1 = 0.9,3 2 = 0.98 and _x000F_ = 10 -9 .
学习率:  Irate = d -0.5 ·min(step_num -0.5 ， step_num · warmup_steps -1.5 )
正则化: Dropout、Label Smoothing

English-to-German:  比现有最好模型的bleu高出2个点。
English-to-French:  bleu值达到41.0，比单个模型都要高，并且时间上缩减了1/4