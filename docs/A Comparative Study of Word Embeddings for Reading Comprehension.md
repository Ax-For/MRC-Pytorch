# A Comparative Study of Word Embeddings for Reading Comprehension

## 摘要

本文探讨两个问题：

- the use of pre-trained word embeddings
- the representation of outof-vocabulary tokens at test time,

这两大因素所带来的影响要比模型结构选择要大。

## Introduction

当前模型分为三步：

1.  Tokens in the document and question are represented using word vectors obtained from a lookup table
2. A sequence model such as LSTM augmented with an attention mechanism，updates these vectors to produce contextual representations.
3. An output layer uses these contextual representations to locate the answer in the document.

当前许多研究都专注于2和3，本文专注于第一步。the use of pretrained word embeddings and the handling of out-of-vocabulary tokens at test time, can lead to substantial differences in the final performance of the reader. 



## 3. Experiments and Result

### 1. Comparison of Word Embeddings

- The first observation is that using embeddings trained on the right corpora can improve anywhere from 3-6% over random initialization.
- Also note that in every single case, GloVe embeddings outperform word2vec embeddings trained on the same corpora
-  if used out-of-the-box, GloVe seems to be the preferred method for pre-training.
- hence corpora with a high percentage of stopwords may not produce high-quality vectors.
- There is also evidence that **stopword** removal can be beneficial when training word vectors, however this needs further verification on other downstream tasks.

### 2. Handling OOV tokens

- 最开始 OOV 词包括所有不在 pre-trained word embdding 词表中的词，然而这忽略了那部分不在 word embdding 词表但是再训练语料中出现多次的词。

