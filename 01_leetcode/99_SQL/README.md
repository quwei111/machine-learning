

## 常见问题
- What is the difference between union and union all? where and having?
     2). Table【in_app_purchase】:
                      uid: unique user id.
                      timestamp: specific timestamp detailed to seconds.
                      purchase amount: the amount of a one-time purchase.
           This is a table containing in-app purchase data. A certain user could have multiple purchases on the same day
           Question 1: List out the top 3 names of the users who have the most purchase amount on '2018-01-01'
           Question 2: Sort the table by timestamp for each user. Create a new column named "cum amount" which calculates the cumulative amount of a certain user of purchase on the same day.
           Question 3: For each day, calculate the growth rate of purchase amount compared to the previous day. if no result for a previous day, show 'Null'.
           Question 4: For each day, calculate a 30day rolling average purchase amount.
     3). Table【Friending】
                     time = timestamp of the action
                     date = human-readable timestamp, i.e, 20108-01-01
                     action = {'send', 'accept'}
                     actor_id = uid of the person pressing the button to take the action
                     target_id = uid of another person who is involved in the action
           Question: what was the friend request acceptance rate for requests sent out on 2018-01-01?
           ...
           因为时间关系我没有再陈列更多，但最典型的题目我已经写出来了。
           题目二涵盖了简单的aggregate问题，cumulative问题，rolling window问题等等。搞定这些，其他的都只是一些简单变形。
           题目三涵盖了self-join，并且有一些tricky的大于等于号的应用，有兴趣可以在地里查一下Facebook面经的解答。
           其他的题目无非是多了一些table，join麻烦一些或者加了一些case when，难度都不会有太大的变化。做好几个经典题，然后自己整理好就可以以不变应万变了。
  2. 相关资料准备
      1). 扫盲网站：SQL ZOO 和 W3schools，非常实用，适合翻阅。
      2). 两个Udemy的SQL课，我女朋友用的，一周时间几乎0基础跟下来，进步非常快：SQL - MySQL for Data Analytics and Business Intelligence 和The Ultimate MySQL Bootcamp
      3). 刷题的话，Leetcode上有一些题，可以做一下。还有好心人直接做了个整理，在这里：summary of sql in leetcode。
      4). Hackerrank上的题自然是要全刷光的，因为难度非常简单，快的话一两天也许就做完了。
      5). 更多的网站在这里， 链接甩给你们自行取用：18 best sql online learning resources
      6). 建议自己下载一个My SQL装到电脑上，模拟真实的SQL环境来学习。
      7). Mysql 里关于Windows function和frame clause的教程：Windows function ，Frame Clause。这个非常重要，windows function可以说是SQL面试里的大杀器，非常节省时间而且思路清晰。
8). 建议也学会用WITH common_table_expression。可以让你的SQL看起来非常整洁和容易理解。
      9). 最最重要的来了。
           如果你觉得刷完题或者学完以上的内容就万事大吉了，那还真的不是。我一开始也有这样的误区。实际上刷完Hackerank也并不能帮你很快的做出我给的例题。
           而其实，对于metrics或者product的了解能够帮助你很好的准备SQL面试，因为所有的SQL面试都是围绕着**与business相关的metrics**而展开的。
           举例而言，游戏公司一定会考DAU(daily active user）或者purchase rate, Facebook就会是friend request 相关的，以此类推。所以熟悉你申请公司的业务再针对性准备SQL，一定会事半功倍。


## Reference
- sqlbolt.com
- mode.com/sql-tutorial
- sqlteaching.com
- w3schools.com/sql
- selectstarsql.com
- https://github.com/oleg-agapov/data-engineering-book/blob/master/book/2-beginner-path/2-2-sql-for-beginners/sql-1.md


window function, self-join, case when, aggregate function
rank
