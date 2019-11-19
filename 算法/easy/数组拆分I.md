
## 题目地址
 https://leetcode-cn.com/problems/array-partition-i/ 

## 题目描述
```
给定长度为 2n 的数组, 你的任务是将这些数分成 n 对, 例如 (a1, b1), (a2, b2), ..., (an, bn) ，
使得从1 到 n 的 min(ai, bi) 总和最大。

示例 1:

输入: [1,4,3,2]

输出: 4
解释: n 等于 2, 最大总和为 4 = min(1, 2) + min(3, 4).
提示:

n 是正整数,范围在 [1, 10000].
数组中的元素范围在 [-10000, 10000].

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/array-partition-i
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。
```

## 思路

>   这题要求就是让元素两两组队然后保留较小的，可以直接排序然后取奇数位相加即可。
>
>   程序如下：
>   
>    ```java
>    class Solution {
>        public int arrayPairSum(int[] nums) {
>            Arrays.sort(nums);
>            int sum = 0;
>            for (int i = 0; i < nums.length; i += 2) {
>                sum += nums[i];
>            }
>            return sum;
>        }
>    }
>    ```
>    

## 结果

> 执行用时 :18 ms, 在所有 java 提交中击败了93.24%的用户
>
> 内存消耗 :40.4 MB, 在所有 java 提交中击败了95.79%的用户
