## 题目：
https://leetcode-cn.com/problems/max-chunks-to-make-sorted-ii/

## 思路：
- 前提：
1. clone 是 arr 已经排好序的数组
2. arr 是原始数组
- 做法：
1. 利用 count 记录当前的数字平衡
2. 把 arr 中的数字往 map 中加，并且 count++;
3. 把 clone 中的数字往 map 中取，并且 count--;
4. 当 count == 0 时，代表平衡，可以构成排序块；


## Java 代码
```java
class Solution {
    public int maxChunksToSorted(int[] arr) {
        int n = arr.length;
        int[] clone = arr.clone();
        Arrays.sort(clone);
        Map<Integer,Integer> map = new HashMap<>();
        int count = 0, sum = 0;
        for (int i=0;i<n;i++) 
        {
            int ar = arr[i], cl = clone[i];
            map.put(ar, map.getOrDefault(ar,0)+1);
            if (map.get(ar) == 0) count--;
            if (map.get(ar) == 1) count++;

            map.put(cl, map.getOrDefault(cl,0)-1);
            if (map.get(cl) == -1) count++;
            if (map.get(cl) == 0) count--;

            if (count == 0) sum++;
        }
        
        return sum;
    }
}
```

## 复杂度分析：
- 时间复杂度：O(n*log(n)) 排序
- 空间复杂度：O(n) 数组+map
