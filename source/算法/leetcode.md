---
title: 力扣刷题小技巧
date: 2022-02-01 09:27:58
top: 2
tags: 
	- 力扣
categories:
	- 思维
---

# 力扣刷题小技巧
不断学习，不断进步。
山外青山楼外楼

## 复杂度->数据规模
|  复杂度   |   规模  |
|  ----    | ----  |
| O(logn)  |  long long内 |
| O(n)  | 10^7 |
| O(nlogn)  | 10^5 ~ 5 * 10^5 |
| O(n^2)  | 1000 ~ 5000 |
| O(n^3)  | 200 ~ 500 |
| O(2^n)  | 20 ~ 24 |
| O(n!)  | 12 |

---

## 懒惰标记
[设计位集](https://leetcode-cn.com/problems/design-bitset/)
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

## String 类
```c++
    ans = ans + 'c';
    ans += 'c';

    // = 表示深拷贝
```

--- 

## 异或 1 取反
```c++
    x ^= 1;
```

--- 

## 前后缀分解 + dp
```c++
    // 一般有三种操作，前、后和其他，都可以分解前后缀。
    // leetcode 6003
```

--- 

## 自定义hash函数， 参数必须加const
```c++
auto hash_p = [&](pair<int, int> &p) -> size_t{
    static hash<long long> hash_ll;
    return hash_ll((static_cast<long long>(p.first) << 32) + p.second);
};
```

--- 

## 写完程序之后样例怎么设置
一定要测数组元素数量的边界：0, 1, 2, 4;

---

## 让一个数的最后一个为1的二进制位变成零
n & (n - 1)

---

## 递归


## 连续
前缀和、双指针（单调）

## 二分
[一定要看这一篇](https://leetcode-cn.com/problems/search-insert-position/solution/te-bie-hao-yong-de-er-fen-cha-fa-fa-mo-ban-python-/)