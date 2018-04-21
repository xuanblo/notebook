# python3

## 教程
* [python3 cookbook](http://python3-cookbook.readthedocs.io/zh_CN/latest/index.html) | [本地下载](../../uploads/books/《Python+Cookbook》第三版中文v2.0.0.pdf)
* [runoob菜鸟](http://www.runoob.com/python3/python3-tutorial.html)

## 读取文件
```python
f = open("read.txt", "r") # 文本模式

f = open("read.txt", "r", encoding = "utf-8") # 读文件的时候注意编码方式,
#python默认是unicode编码，但是读取的文件如有一些中文空格、横杠、希腊字母的
#时候会报错。在web开发中统一使用utf-8编码方式最好，因为绝大多数浏览器默认都是utf-8编码

f = open("read.txt", "rb") # 二进制模式

whole_file = f.read() # 读取整个文件

first_line = f.readline() # 读取一行

lines = f.readlines() # 读取文件到一个列表

f.close() # 关闭文件
```

## 写文件
```python
f = open("write", "w") # 文本模式
f = open("write", "wb") # 二进制模式
```

## 去掉字符串前后的空白字符
```python
tmp_str = ' a b '
str = str.strip() # 读取文件的时候进行此操作，好处太多了, 比如中文的特殊字符在linux或者后续处理名字不匹配
```

## 判断字符串的起始和结尾
```python
str.startswith('+-') # 起始
str.endswith('+-') # 结尾
# 如果你想检查多种匹配可能，只需要将所有的匹配项放入到一个元组中去， 然后传给 startswith() 或者 endswith() 方法：
for i in cancer_related_lncRNA_df.index:
    for hallmark in cancer_hallmarks:
        cell_val = cancer_related_lncRNA_df[hallmark][i]
        cell_val.strip()
        if cell_val.startswith(('+', '-')):
            print(cell_val, "yes")
        break
```

## 分割字符串, 和连接字符串
```python
# 分割
tmp_str = 'a b c d'

strlist = str.split(' ')

# 连接
tmp_list = ['a', '1', 'b']

tmp_str = ' '.join(tmp_list) # 字符串是一个对象，这里比较想对对象进行操作
```

## 对文件地址的操作os.path
```python
import os

current_path = os.getcwd()

base_path = os.path.dirname(current_path)

lncrna_glist_filename = "fish.txt"

file_path = os.path.join(base_path, "Tempresult", lncrna_glist_filename)
```

## 与os.path配合新建文件夹
```python
# path = 文件路径

os.path.exists(path) # 判断文件是否存在

os.path.join('/home', 'zhangxuan', 'Project', 'readme.txt') # 文件路径连接

os.makedirs('文件夹名', exist_ok = True) # 新建文件夹，如果已经存在exist_ok = True不会报错
```

## 格式化字符串
```python
# 对字符串的使用，主要不要使用关键字，比如str是python3中的一个函数
tmp_str = "这是第一个参数param1 = {}; 这是第二个参数param2 = {}".format(param1, param2)

# 保留有效字符如何操作？等后续碰到之后添加
# put code here
```

## 字典（哈希）的使用
```python
# 一维字典
fasta_sequence = dict() # 定义

fasta_sequence['gene1'] = 'ATGC'

fasta_sequence['gene2'] = 'ATGC'

# result: {'gene1': 'ATGC', 'gene2': 'ATGC'}

# 二维字典
fasta_sequence['gene1']['gene2'] = 'ATGC' # 二维字典不能直接赋值

# 上面的代码会出现这种错误：TypeError: 'str' object does not support item assignment

# 应该这样创建python二维哈希（字典）
fasta_sequence = dict()

fasta_sequence.setdefault('gene1', {})

fasta_sequence['gene1']['gene2'] = 'ATGC'

result: {'gene1': {'gene2': 'a'}}
```

## lambda函数的使用
```python
gene_list = [' gene1', 'gene2 ']

map_object = map(lambda x:x.strip(), gene_list) # 这里返回的是一个map对象， 要转变成list才好用

gene_new_list = list(map_object)

# 这里有个例子：把列表所有的元素变成字符串类型

tmp_list = ['str1', 123]

tmp_str_list = list(map(str, tmp_list))

```

## 各种类型转换
```python
num = '123'

tmp_str = str(num) # 数值类型换字符串类型

tmp_chr = 'abc'

tmp_upper_chr = tmp_chr.upper() # 字符串大写转换成小写

tmp_upper_chr = tmp_upper_chr.lower() # 字符串小写转换成大写

num = list(range(97,123))

alphabet = list(map(chr,num)) # chr函数把数值转换成字符

lower_str = "".join(alphabet)

upper_str = lower_str.upper()

upper_str = upper_str + "0123456789"
```

## try catch
```

```

## json
```python
import json

data = {
	'name': 'zhangxuan',
	'height': '162',
	'age': '28'
}

json_str = json.dumps(data) # Python数据结构转换成JSON

data1 = json.loads(json_str) # JSON编码的字符串转换成Python数据结构

# 如果处理的是文件
# Writing JSON data
with open('data.json', 'w') as f:
    json.dump(data, f)

# Reading data back
with open('data.json', 'r') as f:
    data = json.load(f)
```

## 排序
```python
# 列表排序
b = ['b', 'a']
b.sort()
b -> ['a', 'b']

# 字典输出排序
```

## logging包
```python
# ----------------------------------
import logging

log = logging.getLogger(__name__)

log.critical('Host %s unknown', hostname)
log.error("Couldn't find %r", item)
log.warning('Feature is deprecated')
log.info('Opening file %r, mode=%r', filename, mode)
log.debug('Got here')
# ----------------------------------

```
see [more](http://python3-cookbook.readthedocs.io/zh_CN/latest/c13/p11_add_logging_to_simple_scripts.html)

## 虚拟环境，env
`virtualenv` 是一个创建隔绝的Python环境的工具。

通过pip3安装virtualenv(我想要python3的环境)：
`pip install virtualenv`

测试你的安装
`virtualenv --version`

要开始使用虚拟环境，其需要被激活：
`source my_project/bin/activate`

如果你在虚拟环境中暂时完成了工作，则可以停用它：
`deactivate`

## random

* 使用python random模块的choice方法随机选择某个元素
```python
from random import choice
foo = ['a', 'b', 'c', 'd', 'e']
choice(foo)
```

* 使用python random模块的sample函数从列表中随机选择一组元素
```python
import random
list = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
slice = random.sample(list, 5)  #从list中随机获取5个元素，作为一个片断返回
slice
list #原有序列并没有改变。
```

## pickle
```python
import pprint, pickle

pkl_file = open('data.pkl', 'rb')

data1 = pickle.load(pkl_file)
pprint.pprint(data1)
```

## 查看当前使用的python的包安装目录
```python
import sys
sys.path
```

## 查看使用tempfile包, 创建的临时文件在电脑上的位置
```python
import tempfile
with tempfile.mkdirtempdir() as fp:
    fp.name()
```

## spyder

删除所有变量: `reset` + y, 删除单个变量用右键  
打开多个spyder: `spyder --new-instance` Run a new instance of Spyder, even if the instance mode has been turned on (default)


## 集合set
A B 交集 `A & B`  
A B 并集 `A | B`  
A B 差集 `A - B`  


## 匹配
```python
import re

```

## glob