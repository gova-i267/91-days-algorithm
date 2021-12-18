## 题目：
https://leetcode-cn.com/problems/rotate-list/

## 思路：
1. 先对链表进行求长度 n ，k = k % n，避免多余的移动；
2. last 代表当前链表的最后一个节点，pre 代表 last 的前一个；
3. 每次移动之前都需要满足第二点，移动的时候就把 pre.next = null, pre = last, last.next = head, head = last 及时更新头节点
4. 返回 head 即可！

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
    public ListNode rotateRight(ListNode head, int k) {
        if (head == null || head.next == null) return head;
        ListNode last = head;
        ListNode pre = null;
        int n = 1;
        while (last.next!=null){
                pre = last;
                last = last.next;
                n++;
        }
        n = k % n ;
        for (int i=0;i<n;i++){
            while (last.next!=null){
                pre = last;
                last = last.next;
            }
            pre.next = null;
            last.next = head;
            head = last;
        }

        return head;
    }
}
```

## 复杂度分析
- 时间复杂度 O(n^(k%len)) len为链表长度
- 空间复杂度 O(1)
