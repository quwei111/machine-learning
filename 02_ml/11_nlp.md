# 自然语言处理
包括自然语言理解和自然语言生成

## 文本分类

知识点
- word2vec
  - HS是怎么做的？负采样怎么做的？
  - 负采样：加速了模型计算,保证了模型训练的效果。模型每次只需要更新采样的词的权重，不用更新所有的权重，那样会很慢。中心词其实只跟它周围的词有关系，位置离着很远的词没有关系，也没必要同时训练更新。采样 ，词频越大，被采样的概率就越大。
- fasttext
  - fasttext的架构和word2vec 中的cbow 类似，不同之处在于，fasttext预测的是标签，cbow 预测的是中间词
  - 将整篇文档的词及n-gram向量叠加平均得到文档向量，然后使用文档向量做softmax多分类
- bert

## 实体识别

关系抽取
- spert

事件抽取
- djhee 和 plmee

关系抽取后的结果：保存Neo4j


## 文本摘要 Text summarization
- 分为抽象式摘要（abstractive summarization）和抽取式摘要(extractive summarization)
- 在抽象式摘要中，目标摘要所包含的词或短语会不在原文中，通常需要进行文本重写等操作进行生成；
- 抽取式摘要，通过复制和重组文档中最重要的内容(一般为句子)来形成摘要。那么如何获取并选择文档中重要句子，就是抽取式摘要的关键。传统抽取式摘要方法包括Lead-3和TextRank，传统深度学习方法一般采用LSTM或GRU模型进行重要句子的判断与选择，可以采用预训练语言模型自编码BERT/自回归GPT进行抽取式摘要。

常用指标
- ROUGE
- BLEU


## 关键词提取

key phrase generation
- https://www.zhihu.com/question/21104071

- NPChunker


## Transformers
- 三类模型：bert（自编码）、gpt（自回归）、bart（编码-解码）


## 问答
- 为啥文本不用batch norm要用layer norm
- transformer计算kvq的含义
- 如何‌估计微调一个language model的成本是多少
- quantization的概念，解释一下如何工作的
- 如何克服固定context window的限制，能不能有100K的context window
- tokenizer
  - word level
  - char level
  - subword level: BPE, Bytes BPE, WordPiece, Unigram, SentencePiece,
- query理解
  - NER 品牌、品类等
  - 构建实体库
  - 提升：增强，构造邻居词，共现的实体补充文本


## 参考与继续阅读
- [CS224N](https://web.stanford.edu/class/cs224n/index.html#schedule)
- [information-retrieval-book](https://nlp.stanford.edu/IR-book/information-retrieval-book.html)
- [前处理 Byte Pair Encoder](https://github.com/karpathy/minGPT/blob/master/mingpt/bpe.py)
- [Text clustering with K-means and tf-idf](https://medium.com/@MSalnikov/text-clustering-with-k-means-and-tf-idf-f099bcf95183)
- https://github.com/wangle1218/KBQA-for-Diagnosis
- https://github.com/wangle1218/faq-qa-sys-v2
- [beam search的简单实现（面试版） - lumino的文章 - 知乎](https://zhuanlan.zhihu.com/p/623540053)
