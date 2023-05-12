
# 设计推荐系统
[推荐系统知识](../../02_ml/10_recommendation.md)

## 实例：design ads recommendation system for amazon

### Functional requirement
which part should we focus on
Who is the producer/consumer
Text or image/ video
Ranking / Localization
Permission management

### NonFunctional requirement
- MVP and Non-MVP
- users should have a real time/ near real time / small latency experience Idempotency/ exact-once/ at-least-once/ at-most-once

- reliability: data not get lost/ job not executed in parallel retention policy
- security: store encoded personal data
- consistency: read/ write heavy

召回：对召回系统的要求是，“低延时”与“高精度（precision）


### Capacity planning
- dau
- qps
- peak qps

### Diagram & API
- pagination + sort_key / video start timestamp / offset, page_size
- user context/ client info(ios, network condition) diagram
- list high level diagram first, then each component
- different choices/ tradeoffs and give your recommendation
- MQ or no mq
- cache: consistency/ failure/ cold start
- data model/database: 1 master, 2 replica, primary key, user_id, timestamp, status

1 advertiser create ads
2 ads indexing (inverted index, we can use elastic search)
3 users search for certain keywords
4 recall
5 ranking. 如何减少广告索引的latency，inverted index + db replica + cache

### DataSchema & Scale

### Monitoring & Metrics
注意区分statistical metric和business metric。后者意义更大，但经常无法直接optimize，只能通过ab-testing测试。
- ctr
- impression per second
- candidate count (from recall)
- budget burn rate
- 通用metrics：cpu,qps, latency


## 特定情况
- 地点约束，例如yelp的饭馆推荐
- user network，例如facebook newsfeed推荐
- 音乐、视频的embedding，例如spotify音乐推荐

## 模型
- rule based model
- 转化为classification/regression模型
- matrix factorization
- factorization machine
- wide and deep learning

例如怎么加user and item metadata
retrain plan


## Reference
- [twitter/the-algorithm](https://github.com/twitter/the-algorithm)
- https://github.com/Doragd/Algorithm-Practice-in-Industry
- https://xie.infoq.cn/article/e1db36aecf60b4da29f56eeb4
- https://github.com/wzhe06/SparrowRecSys
- [推荐系统--完整的架构设计和算法(协同过滤、隐语义)](https://zhuanlan.zhihu.com/p/81752025)
- https://www.6aiq.com/article/1553963227373
- https://github.com/jiawei-chen/RecDebiasing
- [Twitter是怎么做推荐的？马斯克开源代码梳理](https://zhuanlan.zhihu.com/p/618667508) 
- [架构设计之广告系统架构解密](https://juejin.cn/post/6988408093587537933)
