---
title: leetcode刷题日记
date: 2022-02-01 09:27:58
tags: 
	- leetcode
categories:
	- 实习
---

不断学习，不断进步

<!-- more -->
# `if` 语句中 `nullptr` 和 `！`区别
```c++
    if (!p)
    # equals;
    if (p == nullptr)
```

# 懒惰标记
```c++
// 记录动作，而不真正的执行。
// bitset的翻转操作
class bitset{
    int flips;
    bitset() {
        flips = false;
    }
    void flip() {
        flips ^= 1;
    }
};
```

# 异或 1 取反
```c++
    x ^= 1;
```

# 前后缀分解 + dp
```c++
    // 一般有三种操作，前、后和其他，都可以分解前后缀。
    // leetcode 6003
```

# 线段树
```c++

```

# 自定义hash函数， 参数必须加const
```c++
auto hash_p = [&](pair<int, int> &p) -> size_t{
    static hash<long long> hash_ll;
    return hash_ll((static_cast<long long>(p.first) << 32) + p.second);
};
```

# 动态规划什么时候