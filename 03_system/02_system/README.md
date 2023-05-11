# 系统设计

## Template
- Functional requirement
- NonFunctional requirement
- Capacity planning
- Diagram + API
- DataSchema + Scale
- Monitoring/Metrics


## 常见面试问题
- Design a URL shortener (e.g. Bitly)- 
- Design a video watching website (e.g. YouTube)
- Design a chatting service (e.g. Telegram, Slack, Discord)
- Design a file sharing service (e.g. Google Drive, Dropbox)
- Design a ride sharing service (e.g. Uber, Lyft)
- Design a photo sharing service (e.g. Flickr, Pinterest)
- Design an e-commerce website (e.g. Amazon, eBay)
- Design a jobs portal (e.g. LinkedIn, Indeed)
- Design a web crawler (e.g. Google)
- Design AI自动写作系统设计
- Design Auction system
- Design search autocomplete system
- Design large scale rate limiter
- Design Netflix
- Design Amazon inventory system
- Design Venmo 
- Design large scale notification platform
- Design AirBNB platform 
- Design Ticket master
- Design high velocity bank account platform
- Design top10 scorersina large scale mobilegame
- Design large scale real time chat platform 
- Design electric bike rental platform
- Design grocery store order processing system
- Design website building platform
- Design giftcard system
- Design large scale devices location tracker

瓶颈，scale, tradeoff

## 问题
- How to do large scale batch processing
- How to do model serving readiness
- How to do model rollout
- 两个service要互相发消息，怎么解决

## 基础

push and pull

consistent hashing

event sourcing

paxos and raft

cache

redis

数据库规范化(Normalization)
- Normalisation Form(NF)，其中包括第一范式、第二范式、第三范式、第四范式以及第五范式(1NF、2NF、3NF、4NF、5NF)


### SQL and NoSQL

需要支持transaction和join的，需要用SQL
需要high TPS和灵活schema的，用NoSQL

SQL(ACID)
- consistency
- structured data (fixed schema)
- transactions
- joins

NOSQL
- high performance
- unstructured data (flexible schema)
- availability
- easy scalability



## Reference
- Web Application and Software Architecture 101
- Groking the system interview
- DDIA
- CMU 15721: advance database
- MIT 6.824
- Tech blog: uber/ pinterests
- https://www.techinterviewhandbook.org/system-design/
- https://github.com/madd86/awesome-system-design
- https://github.com/binhnguyennus/awesome-scalability
- https://github.com/codersguild/System-Design
- https://github.com/soulmachine/system-design
- http://icyfenix.cn/
- https://github.com/InterviewReady/system-design-resources
- https://rajat19.github.io/system-design/pages/guide.html
- https://time.geekbang.org/column/article/6458
- https://blog.bytebytego.com/?sort=top
- https://soulmachine.gitbooks.io/system-design/content/cn/
- [System Design Introduction For Interview.](https://www.youtube.com/watch?v=UzLMhqg3_Wc)