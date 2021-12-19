## 题目
https://leetcode-cn.com/problems/swap-nodes-in-pairs/submissions/

## 思路
- 找到需要交换的两个节点，pre 代表该两个节点的前节点(head 节点需要构造一个前节点)
- 交换两个节点，并更新两两节点和前节点
- 如果后面没有两两节点则结束

## Java 代码
```java
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode() {}
 *     ListNode(int val) { this.val = val; }
 *     ListNode(int val, ListNode next) { this.val = val; this.next = next; }
 * }
 */
class Solution {
    public ListNode swapPairs(ListNode head) {
        if (head == null || head.next == null) return head;
        ListNode res = new ListNode(0, head);
        ListNode frist = head, second = head.next, pre = res;
        while (frist != null && second != null) {
            pre.next = second;
            frist.next = second.next;
            second.next = frist;
            
            pre = frist;
            frist = pre.next;
            if (frist == null) break;
            second = frist.next;
        }
        return res.next;
    }
}
```

## 复杂度
- 时间复杂度：O(n)
- 空间复杂度：O(1)
