## 题目
https://leetcode-cn.com/problems/convert-sorted-list-to-binary-search-tree/

## 思路
- 每次找到中间节点，以中间节点为跟节点，尽最大可能保证左右平衡，然后递归执行左边所有节点为左子节点，递归右边所有节点为右子节点。(需要注意的是，需要及时断中间节点与前一个节点的连接，不然会导致死循环)

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
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode() {}
 *     TreeNode(int val) { this.val = val; }
 *     TreeNode(int val, TreeNode left, TreeNode right) {
 *         this.val = val;
 *         this.left = left;
 *         this.right = right;
 *     }
 * }
 */
class Solution {
    public TreeNode sortedListToBST(ListNode head) {
        if (head == null) return null;
        if (head.next == null) return new TreeNode(head.val);
        int n = 0;
        ListNode temp = head;
        while (temp != null) {
            temp = temp.next;
            n++;
        }
        n = n >> 1;
        temp = head;
        ListNode pre = head;
        for (int i=0;i<n;i++) {
            pre = temp;
            temp = temp.next;
        }
        pre.next = null;
        TreeNode root = new TreeNode(temp.val);
        root.right = sortedListToBST(temp.next);
        root.left = sortedListToBST(head);
        return root;
    }
}
```

## 复杂度
- 时间复杂度：O(n log n)
- 空间复杂度：O(log n) 递归栈
