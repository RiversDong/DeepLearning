请看下面的图是transformer的整体流程    
wx+b进行不断的线性变换得到的还是针对同一个向量的空间平移或者大小的变化，并不会导致直线变成曲线（线性变换只进行空间的频移或者伸缩），
但是加上激活函数以后就会导致直线的形状发生变化，这样就会很强大的去拟合空间中的任何一种状态    

transformer的编码器是想让客观世界的某些东西能够映射成空间中的一个面，对应客观空间的状态   让客观世界中的东西对应空间上的一个位置   

![image](https://github.com/RiversDong/DeepLearning/assets/45725241/0eed29fb-dca7-4e10-909a-db1f332fefc9)    

transformer中的input embedding有什么特殊的要求吗？    
由于transformer内部有很强的词向量生成能力和很想的反向传播和参数更新能力，因此对于input embedding的类型限制不大，可以是one hot编码的向量也可以是word2vec生成的词向量。 虽然用到的input embedding的类型不会影响到最终transformer的性能，但是却会影响到参数更新的速度，例如用了一个很差劲的编码，参数更新找到最优参数的时候需要的时间就会变长。

