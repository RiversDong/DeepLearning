* 计算文件的列数
  ```
  awk -F'\t' '{print NF; exit}' ./data/TCGA/correlation_matrix_tcga.tsv
  ```
  -F 指定文件列的分隔符    
  ./data/TCGA/correlation_matrix_tcga.tsv 所要计算的文件

* 显示文件的大小
  ```
  ls -l --block-size=GB correlation_matrix_tcga.tsv
  ```
  --block-size=GB 以GB显示文件的大小    
  --block-size=KB 以KB显示文件的大小

* python 数据国内pip安装很慢     
```
pip install scipy -i https://pypi.tuna.tsinghua.edu.cn/simple     
-i 用来指定源，这个代码中指定了国内的源
```

* dataframe相关命令
 
data如果是一个dataframe，则
data.columns.values 得到这个数据框的列标题
data.iloc[0] 取出dataframe中的第0行
data[1:] 取出从第一行到最后一行的数据
data.columns = new_header 重新给data新的列标题
np.where(columns==j) 从columns数组中找出其中值和j的值相当的元素的索引

* loc和iloc的区别
loc 和 iloc 是 Pandas 中用于选择 DataFrame 数据的两种不同方法。
loc：根据标签选择数据。
loc 使用行和列的标签来选择数据。这意味着您可以使用行和列的具体名称来访问数据。
语法：df.loc[row_label, column_label]
```
df.loc['行标签', '列标签']
df.loc['行标签1':'行标签2', '列标签1':'列标签2']
df.loc['行标签', :]
df.loc[:, '列标签']
```

iloc：根据位置选择数据。   
iloc 使用整数位置来选择数据。这意味着您可以使用行和列的整数位置（从0开始）来访问数据。
语法：df.iloc[row_position, column_position]
```
Copy code
df.iloc[0, 0]
df.iloc[0:2, 1:3]
df.iloc[0, :]
df.iloc[:, 2]
```

loc 使用标签，而 iloc 使用整数位置。
当您知道要选择的行和列的具体标签时，使用 loc 更方便。
当您需要根据位置进行选择或使用切片时，使用 iloc 更合适。
loc 包括末尾位置，而 iloc 不包括末尾位置。例如，df.loc[0:2] 会包括第0、第1和第2行，而 df.iloc[0:2] 只会包括第0和第1行。
总之，选择使用 loc 还是 iloc 取决于您的需求，您可以根据情况选择合适的方法来访问 DataFrame 数据。



