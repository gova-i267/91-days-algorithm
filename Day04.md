## 题目：
https://leetcode-cn.com/problems/decode-string/

## 思路：
> 注意，方括号有可能会嵌套，需要借助栈或者递归完成
- 字符有四种情况
1. 数字：则存起来(存在多位数情况)
2. 左方括号：递归执行，并得到与之对应的右方括号的位置，并更新 index 位置
3. 右方括号：返回当前的 str 字符串与当前右方括号的位置
4. 字符：拼接到当前 str 的后面

## Java 代码
```java
class Solution {
    public String decodeString(String s) {
        return dfs(s, 0)[0];
    }
    public String[] dfs(String s, int index) {
        StringBuilder str = new StringBuilder();
        if (index >= s.length()) {
            return new String[0];
        }
        int num = 0;
        while(index < s.length()) {
            if (s.charAt(index) >= '0' && s.charAt(index) <= '9') {
                num = num * 10 + (int)(s.charAt(index) - '0');
            }
            else if (s.charAt(index) == '[') {
                String[] temp = dfs(s, index+1);
                index = Integer.valueOf(temp[1]);
                while(num > 0) {
                    str.append(temp[0]);
                    num--;
                }
            }
            else if (s.charAt(index) == ']') {
                return new String[]{str.toString(), String.valueOf(index)};
            }
            else {
                str.append(String.valueOf(s.charAt(index)));
            }
            index++;
        }
        return new String[]{str.toString(), ""};
    }
}
```

## 复杂度分析：
时间复杂度：O(n) 一次遍历
空间复杂度：O(n) 递归栈
