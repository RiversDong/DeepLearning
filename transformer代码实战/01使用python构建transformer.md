# 通过python构建一个transformer框架
# huggingface
# transformer

'''
transformer分为编码器和解码器，编码器主要包含6个编码器，所以先构建小的编码器，然后叠加六次就变成了transformer大的编码器    
Step1： 构建一个小的编码器，进行叠加变成transformer的编码器单元    
Step2： 构建一个小的解码器，对小的解码器进行叠加形成transformer的解码器单元     

一个一个小的东西构建小类，然后通过一个总的类将其整合起来    
'''

import copy 
import marth 
import torch 
import numpy as np 

