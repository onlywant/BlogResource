---
title: leetcode
date: 2022-03-24 11:01:51
tags: 
    - leetcode
categories:
    - leetcode
---

# leetcode备忘录

## 题：912 排序数组
快速排序、堆排序
```c++
// 快速排序
class Solution {
public:
    vector<int> sortArray(vector<int>& nums) {
        int n = nums.size();
        quickSort(nums, 0, n - 1);
        return nums;
    }
    void quickSort(vector<int>& nums, int l, int r) {
        if (l < r) {
            int j = patition(nums, l, r);
            quickSort(nums, l, j - 1);
            quickSort(nums, j + 1, r);
        }
    }
    int patition(vector<int>& nums, int l, int r) {
        int pivot = l + rand() % (r - l + 1);
        int t = nums[pivot];
        swap(nums[pivot], nums[l]);
        int i = l, j = r;
        while (i < j) {
            while (j > i && nums[j] >= t) j--;
            while (i < j && nums[i] <= t) ++i;
            if (i < j)  swap(nums[i], nums[j]);
        }
        swap(nums[j], nums[l]);
        return j;
    }
};
```

```c++
// 堆排序
class Solution {
public:
    vector<int> sortArray(vector<int>& nums) {
        int n = nums.size();
        for (int i = n / 2; i >= 0; --i) {
            down_adjust(nums, i, n);
        }
        for (int i = n - 1; i >= 0; --i) {
            swap(nums[i], nums[0]);
            n--;
            down_adjust(nums, 0, n);
        }
        for (int i = 0; i < n; ++i) cout << nums[i] << " ";
        return nums;
    }
    void down_adjust(vector<int>& nums, int idx, int len) {
        int fa = idx;
        int child = idx * 2 + 1;
        while (child < len) {
            if (child + 1 < len && nums[child + 1] > nums[child]) {
                child = child + 1;
            }
            if (nums[fa] < nums[child]) {
                swap(nums[fa], nums[child]);
            }
            fa = child;
            child = fa * 2 + 1;
        }
    }
};
```