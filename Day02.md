## 题目：
https://leetcode-cn.com/problems/shortest-distance-to-a-character

## 思路：

- 先利用list集合储存 c 字符出现的位置；
- 再判断 s 字符串中每个字符与所有 c 字符的距离，取最小值

```java
class Solution {
    public int[] shortestToChar(String s, char c) {
        int n = s.length();
        int[] res = new int[n];
        Arrays.fill(res,10001);
        List<Integer> list = new ArrayList<>();
        for (int i=0;i<n;i++) {
            if (s.charAt(i) == c) list.add(i);
        }
        int len = list.size();
        for (int i=0;i<n;i++) {
            for (int j=0;j<len;j++) {
                res[i] = Math.min(res[i], Math.abs(i-list.get(j)));
            }
        }
        return res;
    }
}
```

- 空间复杂度 O(n)
- 时间复杂度 O(n2)
