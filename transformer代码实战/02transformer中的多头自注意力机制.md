#### 什么是多头自注意力
就是Q*K*V相乘（QKV同源来源于一个X），QK相乘得到相似度A，AV相乘得到注意力Z，所以代码里面第一步是实现一个自注意力机制     多头自注意力是为了获取子空间的关系   
![image](https://github.com/RiversDong/DeepLearning/assets/45725241/f1653bb1-1538-48a5-8d96-02795bf519e8)    

例如下面的图是将X分为8头，Z1.....Z8，这些Z通过线性变换得到新的Z    
![image](https://github.com/RiversDong/DeepLearning/assets/45725241/93a2c942-455a-47ce-b54b-fdfc887802aa)     

代码里面实现一个注意力机制，然后在其它的著代码部分引用这个自注意力机制实现多头自注意力机制就可以    ，输入QKV 输出得到Z    
```python
class MultiHeadAttention(nn.Module):

    def __init__(self, head, d_model, dropout=0.1):
        super(MultiHeadAttention, self).__init__()
        assert (d_model % head == 0)
        self.d_k = d_model // head
        self.head = head
        self.d_model = d_model
        self.linear_query = nn.Linear(d_model, d_model)
        self.linear_key = nn.Linear(d_model, d_model)
        self.linear_value = nn.Linear(d_model, d_model)
        self.linear_out = nn.Linear(d_model, d_model)
        self.dropout = nn.Dropout(p=dropout)
        self.attn = None

    def forward(self, query, key, value, mask=None):
        if mask is not None:
            # 多头注意力机制的线性变换层是4维，是把query[batch, frame_num, d_model]变成[batch, -1, head, d_k]
            # 再1，2维交换变成[batch, head, -1, d_k], 所以mask要在第一维添加一维，与后面的self attention计算维度一样
            mask = mask.unsqueeze(1)
        n_batch = query.size(0)
        # if self.head == 1:
        #     x, self.attn = self_attention(query, key, value, dropout=self.dropout, mask=mask)
        # else:
        #     query = self.linear_query(query).view(n_batch, -1, self.head, self.d_k).transpose(1, 2)  # [b, 8, 32, 64]
        #     key = self.linear_key(key).view(n_batch, -1, self.head, self.d_k).transpose(1, 2)  # [b, 8, 28, 64]
        #     value = self.linear_value(value).view(n_batch, -1, self.head, self.d_k).transpose(1, 2)  # [b, 8, 28, 64]
        #
        #     x, self.attn = self_attention(query, key, value, dropout=self.dropout, mask=mask)
        #     # 变为三维， 或者说是concat head
        #     x = x.transpose(1, 2).contiguous().view(n_batch, -1, self.head * self.d_k)

        query = self.linear_query(query).view(n_batch, -1, self.head, self.d_k).transpose(1, 2)  # [b, 8, 32, 64]
        key = self.linear_key(key).view(n_batch, -1, self.head, self.d_k).transpose(1, 2)  # [b, 8, 28, 64]
        value = self.linear_value(value).view(n_batch, -1, self.head, self.d_k).transpose(1, 2)  # [b, 8, 28, 64]

        x, self.attn = self_attention(query, key, value, dropout=self.dropout, mask=mask)
        # 变为三维， 或者说是concat head
        x = x.transpose(1, 2).contiguous().view(n_batch, -1, self.head * self.d_k)

        return self.linear_out(x)
```




