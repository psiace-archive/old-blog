---
layout: post
title: LeetCode 1. Two Sum
categories: [LeetCode题解]
tags: [数据结构与算法, 题解, LeetCode简单题]
creativecommons: true
comments: true
---

**原题链接：https://leetcode-cn.com/problems/two-sum/description/**

给定一个整数数组和一个目标值，找出数组中和为目标值的两个数。
你可以假设每个输入只对应一种答案，且同样的元素不能被重复利用。

### 示例：

```
给定 nums = [2, 7, 11, 15], target = 9

因为 nums[0] + nums[1] = 2 + 7 = 9
所以返回 [0, 1]
```

### 分析：

本题分类为`数组`和`哈希表`

`vector`中元素使用连续的存储位置，这意味着可以使用到其元素的常规指针上的偏移量来访问它们的元素，并且与数组中的效率一样高。但是与数组不同的是，它们的大小可以动态改变，它们的存储由容器自动处理。（可以片面把它理解为一个动态数组）

`散列表`（Hash table，也叫哈希表），是根据关键码值(Key value)而直接进行访问的数据结构。给定表M，存在函数f(key)，对任意给定的关键字值key，代入函数后若能得到包含该关键字的记录在表中的地址，则称表M为哈希(Hash）表，函数f(key)为哈希(Hash) 函数。

`Map`是一个关联容器，它提供一对一（其中第一个可以称为关键字，每个关键字只能在map中出现一次，第二个可以称为该关键字的值）的数据处理能力，内部建有红黑树（非一种严格意义上的平衡二叉树），具有对数据自动排序的功能，所以在其内部所有的数据都是有序的。

循环遍历，下标为i，在hash_table中查找data[i]，如果没有则插入hash_table中；如果有，则记录该位置i。再在hash_table中查找target-data[i]，如果有没有则丢弃i，开始下一个循环（即++i）；如果有，则记该位置为n。最终i，n都找到时，进行输出（返回值），算法结束。

### 题解：

```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        map<int, int> hash_table;
        vector<int> index;
        for(int i = 0; i < nums.size(); ++i){
            if (!hash_table.count(nums.at(i))){
                hash_table.insert(make_pair(nums.at(i), i));
            }
            if (hash_table.count(target - nums.at(i))){
                int n = hash_table.at(target - nums.at(i));
                if (n != i){
                    index.push_back(n);
                    index.push_back(i);
                    break;
                }
            }
        }
    return index;        
    }
};
```

**注** 不需要对i和n进行排序，这是由于遍历从起始位置开始，第一次找到对应值时，必然满足i比n小。
