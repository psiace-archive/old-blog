---
layout: post
title: LeetCode 暑期练习记录
categories: [LeetCode题解]
tags: [数据结构与算法, 题解, LeetCode, 沸点工作室]
excerpt: 一些精简的思路和代码，没有难度的练习
creativecommons: true
comments: true
---

沸点这边要求假期做 LeetCode 的题，然后写一下记录，所以更新几道题的思路和代码。

### Fizz Buzz

链接：https://leetcode-cn.com/problems/fizz-buzz/description/

思路：就按照题意就可以，这道题本来用 C 写过

代码：
```javascript
var fizzBuzz = function(n) {
    var arr = [];
    for(var i=1;i<n+1;i++){
        if(i%15 == 0){
            arr[i-1] = "FizzBuzz"
        }else if(i%5 == 0){
            arr[i-1] = "Buzz"
        }else if(i%3 == 0){
            arr[i-1] = "Fizz"
        }else{
            arr[i-1] = "" + i
        }
    }
    return arr;
};
```

### 删除排序数组中的重复项

链接：https://leetcode-cn.com/problems/remove-duplicates-from-sorted-array/description/

思路：这里用到了双指针技巧，一个指向当前元素，一个用来跳过与当前元素重复的项。

代码：
```java
public int removeDuplicates(int[] nums) {
    if (nums.length == 0) return 0;
    int i = 0;
    for (int j = 1; j < nums.length; j++) {
        if (nums[j] != nums[i]) {
            i++;
            nums[i] = nums[j];
        }
    }
    return i + 1;
}
```


### 验证回文串

链接：https://leetcode-cn.com/problems/valid-palindrome/description/

思路：如果是字母或数字，则判断指向的元素是否相同，不同则不是回文。依次检查。

代码：

```javascript
var isPalindrome = function(s) {
    s = s.toLowerCase();
    var beg = 0;
    var end = s.length - 1;
    
    while(beg < end) {
        if(!s[beg].match(/[a-z0-9]/)) {
            beg++;
        } else if(!s[end].match(/[a-z0-9]/)) {
            end--;
        } else if(s[beg] !== s[end]) {
            return false;
        } else {
            end--;
            beg++;
        }
    }
    
    return true;
};
```

### 移除元素

链接：https://leetcode-cn.com/problems/remove-element/description/

思路：找在不在然后移除，返回长度

代码：

```python
class Solution:
    def removeElement(self, nums, val):
        while val in nums:
            nums.remove(val)
        return(len(nums))
```       

### 翻转字符串里的单词

链接：https://leetcode-cn.com/problems/reverse-words-in-a-string/description/

思路：分割 -> 去空格 -> 翻转 -> 加空格连接

代码：

```python
class Solution:
    def reverseWords(self, s):
        tmp = s.split(' ') 
        while '' in tmp:  
            tmp.remove('')
        tmp.reverse()   
        tmp = ' '.join(tmp) 
        return(tmp)
```

### Nim 游戏

链接：https://leetcode-cn.com/problems/nim-game/description/

思路：当出现 4 的倍数时，你作为先手必输，否则，在作出最优选择情况下你一定可以赢。

代码：
```c++
class Solution {
public:
    bool canWinNim(int n) {
        return n%4 != 0;
    }
};
```

### 位 1 的个数

链接：https://leetcode-cn.com/problems/number-of-1-bits/description/

思路：这个方法模拟了十进制转二进制的过程，每出现 1 时就累加，然后返回总数。

代码：
```c++
class Solution {
public:
    int hammingWeight(uint32_t n) {
        int sum = 0;
        while(n != 0){
            if(n % 2 == 1){
                sum += 1;
            }
            n = n / 2;
        }
        return sum;
    }
};
```

### 大的国家

链接：https://leetcode-cn.com/problems/big-countries/description/

思路：如题所述，需要 `area>3000000` 或 `population>25000000`，把语句写出来就行

代码：

```MySQL
SELECT name, population, area
FROM World
WHERE area > 3000000 OR population > 25000000;
```

### 石子游戏

链接：https://leetcode-cn.com/problems/stone-game/description/

思路：这道题其实重点在最佳发挥上，既然没有平局，那么先选者就会胜出，用推理的方法得出，然后直接返回 `true`。 

代码：

```c++
class Solution {
public:
    bool stoneGame(vector<int>& piles) {
        return true;
    }
};
```



### 数据流中的第 K 大元素

链接： https://leetcode-cn.com/explore/learn/card/introduction-to-data-structure-binary-search-tree/66/conclusion/183/

思路：这个解法用了二叉搜索树，值得注意的是 C 语言没有很好的办法确定传入函数的数组大小（`sizeof` 不可行），所以是要用到 `numsSize` 的。

代码：感谢 [@aiken](https://leetcode-cn.com/aiken)

```c
typedef struct treeNode {
    int val;
    int occasions;
    int cnt;
    struct treeNode *left;
    struct treeNode *right;
 }Tree;
typedef struct {
    int k;
    struct treeNode *head;    
} KthLargest;
 Tree * insertIntoBST(Tree* root, int val) {
    if(NULL==root)
    {
        Tree* res=calloc(1,sizeof(Tree));
        res->val=val;
        res->occasions=1;
        res->cnt=1;
        //res->right=NULL;
        //res->left=NULL;
        return res;
    }
    if (root->val > val)
    {
        root->cnt++;
        root->left=insertIntoBST(root->left,val);
    }    
    else if(root->val == val)
    {
        root->cnt++;
        root->occasions++;
    }
    else
    {
        root->cnt++;
        root->right=insertIntoBST(root->right, val);
    }
    return root;
}
int findkth(Tree* h,int k)
{
    if(NULL==h || k<=0)
        return 0;
    if(k > h->cnt)
        return 0;
    if(h->right)
    {
        Tree* tmp=h->right;
        int t=tmp->cnt + h->occasions;
        if(k <= tmp->cnt)
        {
           return findkth(h->right,k);
        }
        else if(k <= t )
            return h->val;
        else
            return findkth(h->left,k-t);
    }
    else if ( k <= h->occasions)
        return h->val;
    else
        return findkth(h->left,k - h->occasions );
}
KthLargest* kthLargestCreate(int k, int* nums, int numsSize) {
    if(k<=0)
        return NULL;
    KthLargest* kth=calloc(1,sizeof(KthLargest));
    kth->k=k;
    //kth->head=NULL;
    if(NULL==nums )
        return kth;
    struct treeNode * h=NULL;
    for(int i=0;i<numsSize;i++)
    {
        h=insertIntoBST( h, nums[i]);
    }
    kth->head=h;
    return kth;
}
int kthLargestAdd(KthLargest* obj, int val) {
    if(NULL==obj)
        return 0;
    int res=0;
    obj->head=insertIntoBST( obj->head,val);
    res=findkth(obj->head,obj->k);
    return res;
}
void freetree(Tree* root)
{
    if(NULL==root) 
        return ;
    if(root->left)
        freetree(root->left);
    if(root->right)
        freetree(root->right);
    free(root);
    return ;
}
void kthLargestFree(KthLargest* obj) {
    //free tree;
    freetree(obj->head);
    free(obj);
}
```