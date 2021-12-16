## 题目：
https://leetcode-cn.com/problems/implement-queue-using-stacks/

## 思路：
- 前提：
1. in 栈只存push的数据
2. out 是 peek 和 pop 的栈
- 做法：
1. push 时，直接存 in 栈
2. pop 和 peek 时需要判断 out 栈是否为空，如果为空，则把 in 栈的数据 pop 后再 push 进 out 栈中(栈是后进先出，经过两次压栈后就变成了先进先出)，在 out 栈中 peek 和 pop
3. isEmpty 需要同时判断 in 和 out 栈是否为空

## Java 代码
```java
class MyQueue {
    Stack<Integer> in;
    Stack<Integer> out;
    public MyQueue() {
        in = new Stack<>();
        out = new Stack<>();
    }
    
    public void push(int x) {
        in.push(x);
    }
    
    public int pop() {
        if (out.isEmpty()) {
            int n = in.size();
            for (int i=0;i<n;i++) {
                out.push(in.pop());
            }
        }
        return out.pop();
    }
    
    public int peek() {
        if (out.isEmpty()) {
            int n = in.size();
            for (int i=0;i<n;i++) {
                out.push(in.pop());
            }
        }
        return out.peek();
    }
    
    public boolean empty() {
        return in.isEmpty() && out.isEmpty();
    }
}

/**
 * Your MyQueue object will be instantiated and called as such:
 * MyQueue obj = new MyQueue();
 * obj.push(x);
 * int param_2 = obj.pop();
 * int param_3 = obj.peek();
 * boolean param_4 = obj.empty();
 */
```

## 复杂度分析：
- 时间复杂度：O(n) 一次遍历
- 空间复杂度：O(n) 两个栈辅助存储
