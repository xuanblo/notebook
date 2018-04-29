# pandas使用

## 读取常见的文件格式如：excel, csv, txt(table)
```
import pandas as pd

# read data to import
file_name = "cancer_related_lncRNA 6-28.xlsx"

current_path = os.getcwd()

base_path = os.path.dirname(current_path)

file_path = os.path.join(base_path, "Rawdata", "lncrna_info_table_finnal", file_name)

# read excel
df = pd.read_excel(file_path, header = 0, sep = "\t")

df = df.fillna("") # 对空的数据补齐

# read_csv 
# 这里有个坑，注意文件不路径不能有空、中文、非asic字符

df = pd.read_csv(file_path, header = 0, sep = "\t")

# read_table, 跟read_csv有啥差别？目前还不知道

```

## pandas写入文件
```
# read file to dataframe

df = pd.read_excel(file_path, header = 0, sep = "\t", encoding = 'utf-8')

df.to_excel('写入的文件名')

df.to_csv('写入的文件名')

```

## dataframe 的切割使用
```
df.columns # 表格的header头，可作为列表使用

df.index # 表格的index列，可最为列表使用

df.loc['行名', '列名'] # 取特定的位点

df.loc['行名', :] # 取一行

df.'gene' # 去基因这一列

df.iloc[[1:2], [3:4]] # 通过坐标选子集, 这里[]中的列表可以用header的列表, 比如['gene1', 'gene2']这样取了两列
```

## merge 通过键拼接列
[Merge, join, and concatenate](https://pandas.pydata.org/pandas-docs/stable/merging.html)

* merge
```
df1=DataFrame({'key':['a','b','b'],'data1':range(3)})
df2=DataFrame({'key':['a','b','c'],'data2':range(3)})
pd.merge(df1,df2)   #没有指定连接键，默认用重叠列名，没有指定连接方式
```

## pandas缺失值
缺失值默认是nan，float类型，如果你想判断这个值的话不可能，最好的方式就是：
```python
protein_df = pd.read_csv("Census_allFri_Feb_24_085913_2017.tsv", header = 0, index_col = None, sep = '\t')

# 填充缺失值
protein_df = protein_df.fillna('')
```