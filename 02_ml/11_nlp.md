# 自然语言处理
包括自然语言理解和自然语言生成。

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


## 问答
- 为啥文本不用batch norm要用layer norm
- transformer计算kvq的含义


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