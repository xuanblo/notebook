# 机器学习machine learning分类
lncRNA分类: 促癌基因onco gene, 抑癌基因; tumor suppress基因; background基因

## 用了哪些feature?
## H3K4Me1是怎么和增强子相关的?
## H3K4Me3为什么会在启动子那里富集?
## ucsc 上的组蛋白甲基化值为什么是小数
## 哪些feature重要?为什么有些feature不重要?
## 甲基化的差异你是怎么衡量的？如何量化

### UCSC_repeat
LTR是啥? Long transcript regulation


### 组蛋白的甲基化
bysefa 测序深度要高，
组合测甲基化方法，两部分：1随机打断，抗体富集甲基化的片段，2甲基化敏感的内切酶切割
报告的一部分讲根据他们的方法做的实验，另一部分是转座子
Chemical modifications (e.g., methylation and acetylation) to the histone proteins present in chromatin influence gene expression by changing how accessible the chromatin is to transcription. A specific modification of a specific histone protein is called a histone mark. This track shows the levels of enrichment of the H3K4Me1 histone mark across the genome as determined by a ChIP-seq assay. The H3K4me1 histone mark is the mono-methylation of lysine 4 of the H3 histone protein, and it is associated with enhancers and with DNA regions downstream of transcription starts. Additional histone marks and other chromatin associated ChIP-seq data is available at the Broad Histone page.

染色质中存在的组蛋白的化学修饰（例如甲基化和乙酰化）通过改变染色质对转录的可及性来影响基因表达。 特定组蛋白的特异性修饰称为组蛋白标记。 该曲线显示了通过ChIP-seq测定确定的跨基因组的H3K4Me1组蛋白标记的富集水平。 H3K4me1组蛋白标记是H3组蛋白蛋白的赖氨酸4的单甲基化，它与增强子相关，并与转录起始下游的DNA区相关。 其他组蛋白标记和其他染色质相关的ChIP-seq数据可在Broad Histone页面获得。

H3·H4 的乙酰化可打开一个开放的染色质结构，增加基因的表达。组蛋白H3K4的甲基化主要聚集在活跃转录的启动子区域

ucsc上下载的组蛋白数据，使用bigWigTwobed程序转成bed文件，用bedtools得到指定范围的数值

TSS5k_H3k4me3.avg 七个细胞系的平均值

cancer相关的tss1k H3K4me1甲基化高，背景基因甲基化低
onco 和 ts 应该没有很大差异TSS1k_H3k4me1

背景基因是怎么选的呢？上下多少k都没有gwas相关的snp
H3K4me3
在表观遗传研究中，H3K4me3是作为一个组蛋白密码，或者组蛋白标识来识别基因启动子。

### DNA的甲基化CPG岛
我在项目中直接用这个：ange(0-1000, 1k), 这个范围类cpgNum
但是ucsc还有这个：Ratio of observed(cpgNum) to expected(numC*numG/length) CpG in island
Obs/Exp CpG = Number of CpG * N / (Number of C * Number of G)

### lncrna的作用可能是它是否转录

### 保守性
平均值

### 突变
突变的个数




