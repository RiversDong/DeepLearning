# 通过python构建一个transformer框架        

transformer分为编码器和解码器，编码器主要包含6个编码器，所以先构建小的编码器，然后叠加六次就变成了transformer大的编码器    
Step1： 构建一个小的编码器，进行叠加变成transformer的编码器单元    
Step2： 构建一个小的解码器，对小的解码器进行叠加形成transformer的解码器单元     

一个一个小的东西构建小类，然后通过一个总的类将其整合起来        

```python
import copy 
import marth 
import torch 
import numpy as np
```

下面面的图是transformer的框架图，其中的add 和 norm出现很多次，即残差和标准化，因此这部分需要代码实现，add 和 norm不但出现在了
编码器中也出现在了解码器中    

![image](https://github.com/RiversDong/DeepLearning/assets/45725241/e34c50fc-0652-48ce-8d44-268e5edc1fde)     


这个图是一个小的编码器的框架，看下面的图Add 和 normalize：首先是Z会丢进去（自注意力值）和原始的X，接着Z和X进行叠加计算，叠加的结果传递给了layernorm
![image](https://github.com/RiversDong/DeepLearning/assets/45725241/48cc1fa9-481e-4dec-8af7-f81ed4b858f8)

