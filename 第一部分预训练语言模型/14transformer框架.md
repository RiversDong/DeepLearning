#### 来看看我们是怎么一步一步到transformer的
预训练--》NNLM-->word2vec--》ELMO--》attention--》self-attention--》位置编码--》transformer     
预训练的目的就是为了生成词向量

#### transformer整体框架
transformer其实就是attention的一个堆叠，从一个宏观的角度来看transformer到底在干什么，然后在细分，再总结transformer到底在什么？    



请看下面的图片总体而是是seq2seq模型，即序列到系列的模型（编码器到解码器）。那序列是什么呢？比一句话，一句话就是一个序列，一个视频也是一个序列。所以我们可以把transformer分成两部分：编码器和解码器。下面的图中左边是一个整体，右边是一个整体。
![image](https://github.com/RiversDong/DeepLearning/assets/45725241/b0d464df-7624-469d-b3df-9eec6c48cc9b)

下面是一个缩略图，通过机器翻译来做解释：给一个输入，输出是输入的翻译的结果。中间是经过了transformer，因此这个是可以完成翻译任务的    
![image](https://github.com/RiversDong/DeepLearning/assets/45725241/ba77e22a-6d75-4b3b-852e-e117de3c7a8d)     

下面也是一张缩略图，有两部分一个编码器一个解码器，下面来看看transformer的编码器和解码器做了一些什么事情    
编码器：把一个输入变成一个词向量（self-attention）    
解码器：获取编码器输出的词向量， 生成翻译的结果
![image](https://github.com/RiversDong/DeepLearning/assets/45725241/795f31fe-e88e-4389-877b-ad8046dd96f8)


图中的Nx是编码器，编码器里面又有N个小的编码器（默认是6）       
通过6个编码器对于词向量一步一步的强化（增强），一个encode其实可以看做一个self-attention，说了这么多。了解transformer就是了解其中的小的编码器（encoder）和小的编码器（decoder）

![image](https://github.com/RiversDong/DeepLearning/assets/45725241/dc3dd817-79ca-412f-804e-bd1577fe4b16)

来看下图我们来了解小的编码器和解码器，下一节就来讲讲小的编码器中的encoder是什么
![image](https://github.com/RiversDong/DeepLearning/assets/45725241/cf16a795-e1f4-49b8-a950-8cf9a2cde959)








