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


## 方法->问题的映射
### 数学
### 双指针
### 前缀和
### 哈希表
### 有限队列
### 栈
1. 树与双向链表：[二叉搜索树与双向链表](https://leetcode-cn.com/problems/er-cha-sou-suo-shu-yu-shuang-xiang-lian-biao-lcof/)
2. 单调栈应用：[二叉搜索树的后序遍历序列](https://leetcode-cn.com/problems/er-cha-sou-suo-shu-de-hou-xu-bian-li-xu-lie-lcof/)
### 队列
### 单调栈
### 单调队列
### 二分法
### 树状数组
### 递归
只需要明白一个函数的作用并相信它能完成这个任务。
### BFS
**解决**：
1. 树的遍历问题： [从上到下打印二叉树](https://leetcode-cn.com/problems/cong-shang-dao-xia-da-yin-er-cha-shu-iii-lcof/)
2. 二叉树的序列化：[序列化二叉树](https://leetcode-cn.com/problems/xu-lie-hua-er-cha-shu-lcof/)
    

### DFS
**解决**：
1. 树与双向链表：[二叉搜索树与双向链表](https://leetcode-cn.com/problems/er-cha-sou-suo-shu-yu-shuang-xiang-lian-biao-lcof/)
2. 树的子结构：[树的子结构](https://leetcode-cn.com/problems/shu-de-zi-jie-gou-lcof/)


## 知识点总结

### `if` 语句中 `nullptr` 和 `！`区别
```c++
    if (!p)
    ## equals;
    if (p == nullptr)
```

--- 
### 懒惰标记
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

--- 
### 异或 1 取反
```c++
    x ^= 1;
```

--- 
### 前后缀分解 + dp
```c++
    // 一般有三种操作，前、后和其他，都可以分解前后缀。
    // leetcode 6003
```

--- 

### 自定义hash函数， 参数必须加const
```c++
auto hash_p = [&](pair<int, int> &p) -> size_t{
    static hash<long long> hash_ll;
    return hash_ll((static_cast<long long>(p.first) << 32) + p.second);
};
```

--- 
### 写完程序之后样例怎么设置
一定要测数组元素数量的边界：0, 1, 2, 4;

---

### 让一个数的最后一个为1的二进制位变成零
n & (n - 1)

---

### 递归


### 连续
前缀和、双指针（单调）