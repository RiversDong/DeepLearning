#### transformer的编码器
编码器在干嘛：他是将词转化为词向量，总而言之编码器是让计算机能够更加合理的认识人类世界客观存在的一些东西      

#### transformer解码器   
解码器会接收遍编码器生成的词向量，然后然后通过这个词向量去生成翻译的结果。通过下面的图可以看出decoder可以分成三个子层self-attention、encoder-decoder attention以及feed forward
![image](https://github.com/RiversDong/DeepLearning/assets/45725241/d92b3148-d410-40e2-bef7-bcaa2731cb11)     

解码器的attention在编码已经生成的词，什么意思呢？    
假如目标词“我是一个学生”----》masked self attention    
训练阶段：目标此是已知的，然后self-attention是对我是一个学生做编码，如果不做masked，每次训练阶段，都会获得所有的信息    

测试阶段：1.目标词未知，假设目标词是“我是一个老师”，self-attention第一词对我做计算   
2. 第二次对我是做计算     
3. 。。。。     
而测试阶段，每生成一点获得一点

attention是通过查询变量Q找出V里面比较重要的东西，在transformrt中查询变量是encoder（Q）、而V是来自于解码器的self-attention



#### 生成词    
下面来看看具体是怎么生成词的，见下面的图。编码器的输出会传递给decoder，每一个decoder都会进行encoder-decoder计算。除了接收encoder传来的输入，decoder本身也会有两外的两个输入（下面的图片右边部分的最下面）
，分别是目标词（利用了已经生成的词，这个已经生成的词经过了self-attention） 最后经过linear层的转换成词向量的维度
softmax得到最大词的概率

![image](https://github.com/RiversDong/DeepLearning/assets/45725241/10d792bb-ead6-463c-b354-69d59f0c6fe9)








