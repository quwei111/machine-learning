# 207 Course Schedule
[]()

There are a total of numCourses courses you have to take, labeled from 0 to numCourses-1.

Some courses may have prerequisites, for example to take course 0 you have to first take course 1, which is expressed as a pair: [0,1]

Given the total number of courses and a list of prerequisite pairs, is it possible for you to finish all courses?

## solution
- 建图，判断图是否有环
- 建立队列存储不需要先行课程的课程，从队列中取出元素，找到依赖该元素的后续课程。如果后续课程不再依赖其他课程，则加入队列


```python

```
时间复杂度：

## Follow-up
- [210. Course Schedule II](./210.%20Course%20Schedule%20II.md)
