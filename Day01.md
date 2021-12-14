## 题目：
https://leetcode-cn.com/problems/add-to-array-form-of-integer/

## 思路：
- 数组从后往前与 k 的尾数相加，如果超过 10，则给 k 先 / 10 ，再加1(相当于加 10 )
- 此时需要注意，k 可能还不等于 0 ，需要将 k 组合进数组里
- 最后要反转list集合

```java
class Solution {
    public List<Integer> addToArrayForm(int[] num, int k) {
        int n = num.length;
        List<Integer> list = new ArrayList<>();
        for (int i=n-1;i>=0;i--) {
            int sum = num[i] + k % 10;
            k /= 10;
            k += sum / 10;
            list.add(sum % 10);
        }
        for ( ;k>0;k/=10) {
            list.add(k % 10);
        }
        Collections.reverse(list);
        return list;
    }
}
```

## 复杂度：
- 时间复杂度 O(n)
- 空间复杂度 O(n)
