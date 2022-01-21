---
title: leetcode
date: 2021-02-02 09:27:58
tags: 
	- leetcode
---

Leetcode题目。

<!-- more -->

## 70  [爬楼梯](https://leetcode-cn.com/problems/climbing-stairs/)

1. 第一版：使用深度优先搜索，超时

   ```go
   var res int
   func climbStairs(n int) int {
       res = 0
       backTrack(0, n)
       return res
   }
   func backTrack(cur int, n int){
       if cur == n {
           res++
       }else if cur > n{
           return
       }else{
           backTrack(cur+1, n)
           backTrack(cur+2, n)
       }
   }
   ```

3. 第二版：使用动态规划，$ f(x+2) = f(x)+ f(x+1) $ 

## 121 [买卖股票的最佳时机](https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock/)

1. 动态规划。

   求数组中两个数的差值最大。令 $f(i)$ 表示以第 $i$ 天的价格卖出获得的最大利润，即 $f(i)=max(p[i]-(p[i-1]-f[i-1]),0)$ 。