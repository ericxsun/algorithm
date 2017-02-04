keywords
--------

先去 stopwords

- TF-IDF

  很强的 Baseline. 词 $i$ 在文档 $j$ 中的 TF-IDF 权值为：

  $$
  TF-IDF_{i,j} = \frac{n_{i,j}}{\sum_{k \in K}{n_{k,j}}} \times \log{\frac{\vert D \vert + 1}{\vert {\{j: t_i \in d_j\}} \vert + 1}}
  $$

  其中, $n_{i,j}$ 为词 $t_i$ 在 文档 $d_j$ 中的词频, $K$ 为句子的所有不重复词。

  $IDF$ 的简单结构并不能使提取的关键词，十分有效地反映单词的重要程度和特征词的分布情况，使其无法很好地完成对权值调整的功能。尤其是在同类语料库中，这一方法有很大弊端，往往一些同类文本的关键词被掩盖。例如：语料库 $D$ 中教育类文章偏多，而文本 $j$ 是一篇属于教育类的文章，那么教育类相关的词语的 $IDF$ 值将会偏小，使提取文本关键词的召回率更低。

- TF-IWF

  $$
  TF-IWF_{i,j} = \frac{n_{i,j}}{\sum_{k \in K}{n_{k,j}}} \times \log{ \frac{\sum_{l \in L} nt_l}{ nt_i} }
  $$

  其中，$nt_i$ 表示 $t_i$ 在语料库中出现的总频数, $K$ 为句子的所有不重复词, $L$为语料库中出现的不重复词。

  $IWF$ 部分的含义是对语料库词语总数与待查文本中该词出现在语料库中的次数比求对数。这种加权方法降低了语料库中同类型文本对词语权重的影响，更加精确地表达了这个词语在待查文档中的重要程度。

  @see Improved TF-IDF Keyword Extraction Algorithm

- TextRank

    实际应用效果并不比 $TF-IDF$ 有明显优势，而且由于涉及网络构建和随机游走的迭代算法，效率极低。

- 迭代

  一个term单独出现的频次越高，而且和其他term搭配出现的机会越少，这个term表达意图的能力越强，越重要。

  $$
  W(i, t+1) = \frac{1}{N} \sum_{d: i \in d, d \in D} \frac{W(i, t)}{\sum_{j: j \in d} W(j, t)}
  $$

  其中，$W(i,t)$ 表示第 $t$ 轮词 $i$ 的重要程度，$N$ 为含有词 $i$ 的文档数。初始时，$W(i, 0) = \frac{1}{m}$， 其中 $m$ 为词数。

- 考虑词语所在位置信息

  标题、段首、段中、段尾

- CRF

  features

  | No. | Feature | Explanations | Normalization |
  |
