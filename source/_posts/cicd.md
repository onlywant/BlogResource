---
title: github actions 如何使两个仓库联动
date: 2022-02-09 12:32:11
tags: 
	- github
    - actions 
---

<!-- more -->

# 前期准备：
>  - 源代码仓库、执行仓库
>  - pub_key 和 pri_key
>  - deploy.yml

# key用来做什么？

> 源代码仓库需要向执行仓库推送改变，那么执行仓库识别源代码仓库就需要 ssh-key 公私钥判定。
![source](pri_key.png)
![source](pub_key.png)

# deploy.yml 流程
> 1. 在源代码仓库中监控 push 行为，如果监控到 push，则进行项目编译
> 2. 编译完成后推送到执行仓库。