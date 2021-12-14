## 题目：
https://leetcode-cn.com/problems/design-a-stack-with-increment-operation/

## 思路：用数组实现
- nowIndex 代表当前元素的位置，-1 为栈空
- maxSize 为栈最大，nowIndex == maxSize - 1 时，栈满
- 每 push 一次，nowIndex 往后移动一位
- 每 pop 一次，nowIndex 往前移动一位
- increment 时，遍历 i 从 0 开始，需要满足 i < k && i <= nowIndex

## java
```java
class CustomStack {
    int maxSize = 0;
    int nowIndex = -1;
    int[] arr;
    public CustomStack(int maxSize) {
        this.maxSize = maxSize;
        arr = new int[maxSize];
    }
    
    public void push(int x) {
        if (nowIndex == maxSize-1) {
            return;
        }
        arr[++nowIndex] = x;
    }
    
    public int pop() {
        if (nowIndex == -1) {
            return -1;
        }
    }
    
    public void increment(int k, int val) {
        for (int i=0;i<k && i<=nowIndex;i++) {
            arr[i] += val;
        }
    }
}

/**
 * Your CustomStack object will be instantiated and called as such:
 * CustomStack obj = new CustomStack(maxSize);
 * obj.push(x);
 * int param_2 = obj.pop();
 * obj.increment(k,val);
 */
```

## 复杂度分析
1. 时间复杂度 
- push O(1)
- pop O(1)
-  increment:O(k)最大O(n)
2. 空间复杂度
- O(maxSize)
