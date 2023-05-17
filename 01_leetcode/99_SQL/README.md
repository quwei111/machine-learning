# SQL

对product和metrics的业务了解能够帮助我们更好的准备SQL面试，所有的SQL面试都是围绕着**与business相关的metrics**而展开。

建议自己下载一个My SQL装到电脑上，模拟真实SQL环境来学习。

## 知识点
- row number
- explode
- Windows function
- frame clause
- self-join
- case when
- aggregate function
- WITH common_table_expression

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



## Reference
- SQL ZOO 
- w3schools.com/sql
- udemy: SQL - MySQL for Data Analytics and Business Intelligence 和The Ultimate MySQL Bootcamp
- sqlbolt.com
- mode.com/sql-tutorial
- Hackerrank
- sqlteaching.com
- selectstarsql.com
- https://github.com/oleg-agapov/data-engineering-book/blob/master/book/2-beginner-path/2-2-sql-for-beginners/sql-1.md
- 18 best sql online learning resources

window function, 
rank
