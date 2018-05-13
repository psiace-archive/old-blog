---
layout: post
title: LeetCode 7. Reverse Integer
categories: [LeetCode题解]
tags: [数据结构与算法, 题解, LeetCode简单题]
creativecommons: true
comments: true
---

**原题链接：https://leetcode-cn.com/problems/reverse-integer/description/**

给定一个 32 位有符号整数，将整数中的数字进行反转。

### 示例1：

```
输入: 123
输出: 321
```

### 示例2：

```
输入: -123
输出: -321
```

### 示例3：

```
输入: 120
输出: 21
```

### 注意:

假设我们的环境只能存储 32 位有符号整数，其数值范围是 [−2<sup>31</sup>,  2<sup>31</sup> − 1]。根据这个假设，如果反转后的整数溢出，则返回 0。

### 分析：

本题分类为`数学`

重点即为关于是否溢出的判断，加减法查看标志位，乘除法逆运算和原来的数字是否相同


### 题解：

```cpp
class Solution {
public:
    int reverse(int x) {
        int ans = 0;
        while (x) {
             int temp = ans * 10 + x % 10;
             if (temp / 10 != ans)  //如果不等的话说明temp已经溢出了
                 return 0;
        ans = temp;
        x /= 10;
        }
        return ans;
    }
};
```

