word / sentence / doc similarity
----------------------------

计算词之间、句之间、篇章间的相似性

- word similarity
    + word2vec

- sentence similarity
    + sentence2vec
    + query2vec
    + word2vec
        * 叠加词向量

            确实有效，但只对15个字以内的短句子比较有效，这种方案常用在搜索时做query比对。如果简单向量相加，丢掉了很多词与词相关意思,也对句子与句子的模式、结构等照成负面影响，无法更精细的表达句子与句子之间的关系。

        * DM/DBOW
        * extension: bag of words

            通过语料训练 word2vec，构建词库 (N)，对每个句子，构造 N 维向量，每一维的值为这一维的词与句子中的词的相似度的最大值
    + weighted jaccard
        句子 $A$ 和 $B$
        $$
        A = \{w_{i_k} | i \in [1,n], i_k in [1, i_K]\}
        $$

        $$
        B = \{w_{j_t} | j \in [1,m], j_t \in [1, j_T]\}
        $$

        其中 $w_{i_k}$ 表示词 $w_i$ 重复了 $i_k$ 次

        $$
        Sim(A, B) = \frac{\sum_{w_{i_k} \in A \ \ and \ \  w_{j_t} \in B \ \ and \ \ w_{i_k}=w_{j_t}}\min(i_k, j_t)}{\sum_{({w_{i_k} \in A \ \ or \ \  w_{j_t} \in B) \ \ and \ \ w_{i_k}=w_{j_t}}} \min(i_k, j_t) + \sum_{w_{i_k} \in A \ \ and \ \ w_{i_k} \not \in B}i_k + \sum_{w_{j_t} \in B \ \ and \ \ w_{j_t} \not \in A}j_t}
        $$
