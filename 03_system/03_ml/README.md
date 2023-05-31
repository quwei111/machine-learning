# 机器学习系统设计

## 场景
- Youtube recommendation/doordash search box/auto suggestion
- design youtube violent content detection system
- design a monitoring system to realtime measure ML models, including features, score distribution, qps 

可能聚焦的方向
- improve engagement on a feed
- improve customer churn
- return items from search engine query

## follow up
- solution
- how to scale
  - Scaling general SW system (distributed servers, load balancer, sharding, replication, caching, etc)
  - Train data / KB partitioning
  - Distributed ML
  - Data parallelism (for training)
  - Model parallelism (for training, inference)
  - Asynchronous SGD
  - Synchronous SGD
  - Distributed training
  - Data parallel DT, RPC based DT
  - Scaling data collection
  - MT for 1000 languages
    - NLLB
- Monitoring, failure tolerance, updating (below)
- Auto ML (soft: HP tuning, hard: arch search (NAS))
- 线上线下不一致
  - [推荐系统有哪些坑？](https://www.zhihu.com/question/28247353/answer/2126590086)

## 参考
- https://github.com/khangich/machine-learning-interview
- Machine Learning Engineering by Andriy Burkov
- https://github.com/shibuiwilliam/ml-system-in-actions
- https://github.com/mercari/ml-system-design-pattern
- https://github.com/chiphuyen/machine-learning-systems-design
- https://github.com/ibragim-bad/machine-learning-design-primer
- https://www.1point3acres.com/bbs/thread-901192-1-1.html
- Grokking the Machine Learning Interview
- https://about.instagram.com/blog/engineering/designing-a-constrained-exploration-system

- https://www.youtube.com/c/BitTiger
- [ML system 入坑指南 - Fazzie的文章 - 知乎](https://zhuanlan.zhihu.com/p/608318764)
- [模型生产环境中的反馈与数据回流 - 想飞的石头的文章 - 知乎](https://zhuanlan.zhihu.com/p/493080131)


## design doc
- [https://github.com/eugeneyan/ml-design-docs](https://github.com/eugeneyan/ml-design-docs)
