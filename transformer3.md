Encoder：将文字转换成向量的表示形式。eg.进来的时候是一段文字，我们希望把这些文字都先做一个embedding，变成vector呢，但变成vector我们还不满意，因为这个vector我们认为它仅仅是表示了当前单词的信息，你还希望把这些单词能够再进一步的encode一下，变成一些**contexualized word vectors**。contexualized word vectors就是既包含当前单词的信息，也包含周围单词的信息啊，一个非常有名的模型叫做Elmo，他就是这个领域比较早期有名的工作。最有名的contexualized word vectors大部分都是基于RNN, LSTM这样的模型，但是这些模型的重大缺点是没法好好并行，他们总是基于**Autoregressive**的特征，就是这个模型，它的下一步的hidden state总是基于上一步hidden state的输出，所以它总是有一定的这个先后关系。

为了能够去掉这一种对于上一个hidden state的依赖呢，人们就做了很多的尝试，其实(ConvSeek2Seek?)是其中的一个尝试，它的encoder是不完全依赖于之前所有的hidden states，我只依赖于当前附近的那些hidden states，等于是这样的一些设计。至于transformer呢，应该说是一个比ConvSeek2Seek更加直接的一个探索，他就是说完全不需要任何的recurrentNets，我连convNet也不需要，我只需要attention就可以了，这样就可以更加方便地完成，我们这种contexualized word vectors的任务。

Seek2Seek模型的encoder是不需要考虑先后顺序的，他的encoder并不在乎对当前单词的encode必须基于上一个单词。

RNN(l study at Julyedu.) --> RNN(I)->h1,RNN(study, h1)->h2,RNN(at, h2)->h3.
Encoder.我可以同时观看全局信息。

