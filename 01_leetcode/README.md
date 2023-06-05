# Leetcode

## 刷题策略
时间有限的前提下，精刷大于泛刷

- 1、初步掌握考察的常见数据结构和算法，尤其是常见类型的模版
- 2、拿到问题，首先从解决问题角度入手，然后从模板中提供线索。模版的基础上，不断强化练习。按tag刷题
- 3、真正融会贯通，结合问题交流、复杂度分析、头脑测试，刷题量达到满意要求
- 4、面试前，针对面试公司的tag或面经进行重点练习


## 面试解题过程

机器学习方向主要使用python，因此以python为刷题语言

- 明确自己理解问题，甚至有时候面试官故意遗漏内容，所以不明白的地方一定问清楚。通过写test case，确保理解问题并涵盖所有情况。确认输入输出的类型和边界
- 开始想解题思路，尤其是人会如何做这个任务的。没有思路时，想想更简单、数量更少时如何处理
- 转化为代码，用什么数据结构，什么算法。讲思路的时候，一定说清楚为什么选择这个数据结构，结合有代表性的test case讲
- 写完代码后，进行test的过程
- 最后给出复杂度分析

### 给出问题后第一步确认的参考list

- input/output type
- input size 以及edge cases of null or empty
- input element 有无重复
- input element的范围
  - 数字： 全是正数或者全是负数 或者返回必须正数或负数
  - string：是不是都是English letters (A-Z)，有没有特殊符号，有的话，会有哪些会出现
- 能不能改input (1D/2D array比较常见）
- 时间空间复杂度要求
  - 需不需要in place
- 特殊情况的处理， 找没找到的时候返回什么
- 注意区分subarrays和subsequence

## 和算法强相关的技术

- rate limiter
- 不同的cache机制
- geo data (quad tree)
- 文本搜索提示 (trie)

## leetcode刷题列表参考
- [LeetCode 101：和你一起你轻松刷题](https://github.com/changgyhub/leetcode_101/)
- [Leetcode面试高频题分类刷题总结](https://zhuanlan.zhihu.com/p/349940945)
- [代码随想录](https://programmercarl.com/)
- [blind75]
- [Neetcode300]


## 学习资料

基础
- [Introduction to Computer Science - Harvard CS50x](https://cs50.harvard.edu/x/)
- [Structure and Interpretation of Computer Programs - UC Berkeley CS 61A](https://cs61a.org/)
- [How to Design Programs](https://book.douban.com/subject/30175977/)
- [深入理解计算机系统 - CSAPP](https://book.douban.com/subject/5333562/)
- [The Art of Computer Programming - TAOCP](https://www-cs-faculty.stanford.edu/~knuth/taocp.html)
- [代码大全](https://book.douban.com/subject/1477390/)
- [UNIX 编程艺术](https://book.douban.com/subject/11609943/)
- [重构：改善既有代码的设计](https://book.douban.com/subject/4262627/)

数据结构和算法
- [数据结构- 学堂在线 - 邓俊辉](https://next.xuetangx.com/course/THU08091000384/)
- [算法 - Stanford](https://www.coursera.org/specializations/algorithms)
- [Algorithms](https://book.douban.com/subject/1996256/)
- [算法导论 - CLRS](https://book.douban.com/subject/20432061/)

操作系统
- [Operating Systems and System Programming - UC Berkeley CS 162](https://github.com/Berkeley-CS162)
- [Operating System Engineering - MIT 6.828](https://pdos.csail.mit.edu/6.828/)
- [编码：隐匿在计算机软硬件背后的语言](https://book.douban.com/subject/4822685/)
- [计算机系统要素](https://book.douban.com/subject/1998341/)
- [计算机组成与设计](https://book.douban.com/subject/26604008/)
- [Operating Systems: Principles and Practice](https://book.douban.com/subject/25984145/)
- [Operating Systems: Three Easy Pieces](https://book.douban.com/subject/19973015/)
- [Operating System Concepts](https://book.douban.com/subject/10076960/)

Web开发与系统设计
- [Introduction to Computer Networking - Stanford](https://lagunita.stanford.edu/courses/Engineering/Networking-SP/SelfPaced/about)

分布式
- [Distributed Systems - MIT 6.824](https://pdos.csail.mit.edu/6.824/schedule.html)
- [Talent Plan | PingCAP University](https://university.pingcap.com/talent-plan/)
- [数据密集型应用系统设计](https://book.douban.com/subject/30329536/)
