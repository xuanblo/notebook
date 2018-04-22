# MkDocs使用方法

For full documentation visit

- [mkdocs.org](http://mkdocs.org)  
- [MkDocs 中文文档](http://markdown-docs-zh.readthedocs.io/zh_CN/latest/)  
- [Github markdown 中文文档](https://github.com/riku/Markdown-Syntax-CN/blob/master/syntax.md "Title")   
- [cinder](http://sourcefoundry.org/cinder/), 模板,要安装包
- [中文搜索的解决办法windows](https://my.oschina.net/u/3465063/blog/895142)只有这篇可以，加上search.py的修改  
- [中文搜索的解决办法mac](http://beautycss.net/2017/01/23/use-mkdocs-on-mac/)
- [生成pdf和epub](https://github.com/jgrassler/mkdocs-pandoc)  
- [markdown语法](http://equation85.github.io/blog/markdown-examples/ 
- [sublime + markdown 配置插件](http://tinyletter.com/CNFeat/letters/sublime-text-markdown)
- [mkdocs on mac](http://beautycss.net/2017/01/23/use-mkdocs-on-mac/) 
- [markdown-material(https://squidfunk.github.io/mkdocs-material/)

## install
```bash
# 先安装好python3和pip3
pip install mkdocs # 1. 安装MkDocs包
pip install mkdocs-cinder # 2. 安装Cinder主题
mkdocs new Knowledge_of_bioinfoers_with_MkDocs # 3. 新建一个项目
cd Knowledge_of_bioinfoers_with_MkDocs # 4. 进入目录
mkdocs serve -a 0.0.0.0:8000 # 5. 启动服务
scp -r js bioinfo@192.168.31.89:/home/bioinfo/.local/lib/python3.5/site-packages/mkdocs/assets/search/mkdocs # 6. 复制中文搜索js
```

## Commands
在windows上的项目直接复制到linux上启动会有问题，先在linux上创建目录，然后把文件复制过去
* `mkdocs new [dir-name]` - Create a new project.
* `mkdocs serve` - Start the live-reloading docs server.
* `mkdocs build` - Build the documentation site.
* `mkdocs help` - Print this help message.

## mkdocs把md文件转换成html文件,放在临时目录
* windows 加载了视频之后mkdocs用起来非常卡
    原因是C盘被占满了，可以用金山毒霸垃圾清理检测出来，原因可能是打开了多个mkdocs serve会创建新的临时文件
    查看地址：C:\Users\ZHANGXUAN\AppData\Local\Temp\tmp173qgsbl\uploads\twang_lecture\wangting_lecture_vedio
* mac上生成的位置又在哪呢?(思路:看看python tempfile生成文件夹目录在哪) /var/folders/0r/wnxd3fn53t19w_sjc8d9m1500000gn/T
* linux上生成的位置在/tmp目录下

## 终端里输入MKDOCS BUILD，生成文档站点：
`mkdocs build`  
生成完的站点包括完整的css,js,fonts,html等文件/目录。

## 部署文档站点：
`git`

## 解决中文搜索问题
#### Mac
```shell
由于mkdocs生成json文件时将汉字转成了ascii码字符，且mkdocs使用的搜索插件lunr.js本身不支持中文，因此解决中文搜索问题就是要解决这两个问题。

1. 打开FINDER，使用快捷键COMMAND+SHIFT+G，输入以下路径，进入MKDOCS的目录：

/Users/zhangxuan/work/apps/anaconda3/lib/python3.6/site-packages

2. 用代码编辑器打开SEARCH.PY文件，搜索GENERATE_SEARCH_INDEX，修改后的如下：

return json.dumps(page_dicts, sort_keys=True, ensure_ascii=False, indent=4)
添加了ensure_ascii=False,

3. 保存文件，如果权限问题无法保存，就另存到其他目录下，再拷贝覆盖MKDOCS目录下的SEARCH.PY文件；

4. 打开GITHUB站点 HTTPS://GITHUB.COM/CODEPIANO/LUNR.JS 下载或克隆该修改版的LUNR.JS项目到本地；
cd /Users/zhangxuan/work/apps/anaconda3/lib/python3.6/site-packages/mkdocs/assets/search/mkdocs/js
git clone https://github.com/codepiano/lunr.js.git

5. 将下载或克隆到本地的LUNR.JS项目里的LUNR.MIN.JS文件，拷贝覆盖到以下目录里的同名文件：

此目录仍然为mkdocs工具的目录，覆盖官方工具里的同名文件，以后每次生成站点就直接好用了，也可以先备份官方使用的lunr.min.js文件再覆盖它
mv lunr.min.js lunr.min.js.bak
cp lunr.js/lunr.min.js ./

这种方法不得行, 需要把已经弄好的中文搜索比如把/Users/zhangxuan/work/apps/anaconda3/lib/python3.6/site-packages/mkdocs/assets/search/mkdocs/js下的所有文件复制过来

6. 进入文档的目录，使用MKDOCS BUILD重新生成站点；

7. 查看生成好的文档目录下MKDOCS/SEARCH_INDEX.JSON文件，确认里面的中文可以正常显示，非ASCII码字符，说明修改官方文件成功；

8. 将生成好的文档站点上传更新后，清除浏览器缓存，输入中文进行搜索，出来结果即表示成功
```

## Project layout

    mkdocs.yml    # The configuration file.
    docs/
        index.md  # The documentation homepage.
        ...       # Other markdown pages, images and other files.

* bioinformatics: 生物信息学相关的md文档，包括scripts和tools
* img: 存放图片
* scripts: 存放python和perl等脚本
* testing_data: 测试数据
* uploads: 存放一些学习资料和文档

![Screenshot](../../img/mydocpath1.png)

* 整理好了用过的工具, 以后干起来更快更方便, 下面是做过一个事情后整理的文档

![Screenshot](../../img/mydocpath2.png)

* 新增加的页面设置url

![Screenshot](../../img/mydocpath3.png)


## Markdown 语法


#### 分隔线  

---

#### 标题1,2,3...
head1 #  
head2 ##

#### 列表，有序
* Red
* Blue
* Green
- gray

#### 列表，无序
1. abstract
2. introduction
3. result

#### 区块引用
> This is the first level of quoting.
>
> > This is nested blockquote.
>
> Back to the first level.

#### Task Lists
- [x] @mentions, #refs, [links](), **formatting**, and <del>tags</del> supported
- [√] list syntax required (any unordered or ordered list supported)
- [x] this is a complete item
- [ ] this is an incomplete item


#### 缩进
*    This is a list item with two paragraphs.

    This is the second paragraph in the list item. You're
only required to indent the first line. Lorem ipsum dolor
sit amet, consectetuer adipiscing elit.

*   Another item in the same list.

#### 强调
**两个星号**

#### 插入图片

西部世界好烧脑！

![Screenshot](../../img/westernlife.jpg)

*斜体*


#### 代码块

以三个以上 ` （反引号）开始一行, 并在结束位置以相同数目的反引号 ` （反引号）开始一行即可包含一个代码块:

```
Fenced code blocks are like Stardard
Markdown regular code blocks, except that
theye not indented and instead rely on a
start and end fence lines to delimit the code
block.
```

#### 表格

First Header | Second Header | Third Header
------------ | ------------- | ------------
Content Cell | Content Cell  | Content Cell
Content Cell | Content Cell  | Content Cell

&copy;zhangxuan 2017 <zhangxuan@xtbg.ac.cn> 自动创建连接

#### Kindle
* [free ebook](https://ebookfriendly.com/download-free-kindle-books/)
* [Samshwords](https://www.smashwords.com/books/category/1/newest/0/free/any)



#### 参考式的链接
This is [Google][1] reference-style link.

[1]: http://www.google.com/ "Optional Title Here"