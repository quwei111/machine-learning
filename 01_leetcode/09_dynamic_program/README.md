# 动态规划

- 问题
  - 解决有**重复子问题**的**最优化**问题
  - 通过保存子问题的解，避免重复计算
  - 思路：数学归纳法，base case

- 类型
  - top-down (记忆化dfs)
  - bottom-up (循环)

- 类型
  - 记忆化搜索（DFS + Memoization Search）
  - for循环方式的动态规划，非Memoization Search方式。DP可以在多项式时间复杂度内解决DFS需要指数级别的问题。常见的题目包括找最大最小，找可行性，找总方案数等，一般结果是一个Integer或者Boolean
  - 结合了BFS和动态规划，或者DFS和动态规划

- 常见
  - 背包问题
  - 打劫问题
  - 字符串子序列/编辑距离
  - 股票问题
