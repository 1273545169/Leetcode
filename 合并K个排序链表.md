### 题目描述

[23、合并K个排序链表](https://leetcode-cn.com/problems/merge-k-sorted-lists/)

### 思路解析

归并排序

```python

class Solution:
    def mergeKLists(self, lists):
        if not lists:
            return 

        if len(lists) == 1:
            # 注意返回的是链表节点，不能返回lists
            return lists[0]

        mid = len(lists) // 2
        left = self.mergeKLists(lists[:mid])
        right = self.mergeKLists(lists[mid:])
        return self.mergeTwoLists(left, right)

    def mergeTwoLists(self, l1, l2):
        if not l1 or not l2:
            return l1 or l2

        if l1.val < l2.val:
            l1.next = self.mergeTwoLists(l1.next, l2)
            return l1
        else:
            l2.next = self.mergeTwoLists(l1, l2.next)
            return l2


```
