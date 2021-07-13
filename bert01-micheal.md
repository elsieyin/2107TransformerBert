![image-20210711120746886](bert01-micheal.assets/image-20210711120746886.png)

![image-20210711114330195](C:%5CUsers%5C86182%5CAppData%5CRoaming%5CTypora%5Ctypora-user-images%5Cimage-20210711114330195.png)

后BERT时代的所有榜单都是BERT或其变体占据![image-20210711114400436](bert01-micheal.assets/image-20210711114400436.png)

![image-20210711114407888](bert01-micheal.assets/image-20210711114407888.png)

post BERT era![image-20210711114413934](bert01-micheal.assets/image-20210711114413934.png)

BERT网络结构:
·多层叫做transformer的网络叠加

<img src="bert01-micheal.assets/image-20210711114432044.png" alt="image-20210711114432044" style="zoom:67%;" />![image-20210711114507625](bert01-micheal.assets/image-20210711114507625.png)

Transformer层的网络核心要素:
. Multi-head attention(多头注意力)
.FFN(全连接层)
. LayerNorm(层归一化)
·残差连接

### Attention
在深度学习领域的发展历程

![image-20210711114529083](bert01-micheal.assets/image-20210711114529083.png)

NMT model w/o attention
Seq2Seq   <img src="bert01-micheal.assets/image-20210711114552026.png" alt="image-20210711114303813" style="zoom:33%;" />

![image-20210711114544385](bert01-micheal.assets/image-20210711114544385.png)

![image-20210711114652905](bert01-micheal.assets/image-20210711114652905.png)

![image-20210711114657330](bert01-micheal.assets/image-20210711114657330.png)

![image-20210711114703256](bert01-micheal.assets/image-20210711114703256.png)

![image-20210711114709544](bert01-micheal.assets/image-20210711114709544.png)

![image-20210711114713689](bert01-micheal.assets/image-20210711114713689.png)

![image-20210711114717882](bert01-micheal.assets/image-20210711114717882.png)

用注意力分布计算输入句子的加权平均表征at:
![image-20210711114722080](bert01-micheal.assets/image-20210711114722080.png)

![image-20210711114738001](bert01-micheal.assets/image-20210711114738001.png)

注意力输出与s,拼接帮助解码: ![image-20210711114758073](bert01-micheal.assets/image-20210711114758073.png)

![image-20210711114807898](bert01-micheal.assets/image-20210711114807898.png)

#### Attention

注意力的一般定义:
·给定一组向量(key, value)
键值对，以及一个向量query,注意力机制就是一种根据query与keys来计算values的加权平均的模块。

![image-20210711120208612](bert01-micheal.assets/image-20210711120208612.png)

注意力的多种写法：

点积注意力(dot-product attention) :
![image-20210711120236907](bert01-micheal.assets/image-20210711120236907.png)

乘法注意力(multiplicative attention): ![image-20210711120344667](bert01-micheal.assets/image-20210711120344667.png)

加法注意力(additive attention):  ![image-20210711120356818](bert01-micheal.assets/image-20210711120356818.png)

Attention建模句子表征
·从单个字角度:e.g.,“it_”的向量表征
与句子中的所有词之间计算注意力，由此更新其向量表征:

<img src="bert01-micheal.assets/image-20210711120501259.png" alt="image-20210711120501259" style="zoom: 67%;" />

attention操作完全并行的使句子中词语两两间有了交互;

<img src="bert01-micheal.assets/image-20210711120545482.png" alt="image-20210711120545482" style="zoom:67%;" />

Attention建模句子表征
。整个句子的一次self-attention :句子的现有的表征记为H =[h1, ... , hT], 则:

<img src="bert01-micheal.assets/image-20210711120619002.png" alt="image-20210711120619002" style="zoom:67%;" />

<img src="bert01-micheal.assets/image-20210711120654426.png" alt="image-20210711120654426" style="zoom:67%;" />

![image-20210711120737115](bert01-micheal.assets/image-20210711120737115.png)