## 题目
https://leetcode-cn.com/problems/intersection-of-two-linked-lists/

## 思路
- 先用一个 list 集合把 A 链表保存起来
- 然后遍历 B 链表的时候同时判断 B 中的节点是否存在list集合中，如果存在直接返回该节点
- 最后 没有交点 返回 null

## java 代码
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public ListNode getIntersectionNode(ListNode headA, ListNode headB) {
        List<ListNode> list = new ArrayList<>();
        while (headA != null) {
            list.add(headA);
            headA = headA.next;
        }
        while (headB != null) {
            if (list.contains(headB)) {
                return headB;
            }
            headB = headB.next;
        }

        return null;
    }
}
```

## 复杂度
- 空间复杂度：O(len(A)) A 链表长度
- 时间复杂度：O(len(A)*len(B)) 
