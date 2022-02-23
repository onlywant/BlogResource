---
title: 树状数组
date: 2022-02-20 09:33:33
tags:
    - 树状数组
categories:
    - 算法
---

# 树状数组

## 神奇的区间前缀和数据结构
求解单点修改的前缀和

![树状数组](https://cdn.jsdelivr.net/gh/onlywant/blog_img/img/binary-indexed-tree/20220223093713.png)

![](https://cdn.jsdelivr.net/gh/onlywant/blog_img/img/binary-indexed-tree/20220223093805.png)

```c++
template<typename T>
class BinaryIndexedTree{
public:
    explicit BinaryIndexedTree(int len) : size(len+1){
        data = vector<T>(size);
    }
    void add(int x, int delta){
        while(x<size){
            data[x] += delta;
            x += lowbit(x);
        }
    }
    T query(int x){
        T ans = 0;
        while(x>0){
            ans += data[x];
            x -= lowbit(x);
        }
        return ans;
    }
private:
    int lowbit(int x){return x&(-x);}
private:
    int size{0};
    vector<T> data;
};

作者：Archer Wang
链接：https://leetcode-cn.com/circle/article/F8YCEM/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
```