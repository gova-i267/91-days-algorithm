## 题目
https://leetcode-cn.com/problems/linked-list-cycle-ii/

## 思路
- 用 set 保存每个节点，当有重复时就是交点了

## Java 代码
```java
/**
 * Definition for singly-linked list.
 * class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) {
 *         val = x;
 *         next = null;
 *     }
 * }
 */
public class Solution {
    public ListNode detectCycle(ListNode head) {
        
        ListNode fast = head, low = head;
        if (head == null) {
            return null;
        }
        if (head.next != null && head.next.next == head) {
            return head;
        }
        while (low != null && fast.next != null) {
            fast = fast.next.next;
            low = low.next;
            if (fast == low) {
                return fast.next;
            }
        }
        return null;
    }
}
```

## 复杂度分析
- 时间复杂度 O(n)
- 空间复杂度 O(n)

## 进阶
- 快慢指针
