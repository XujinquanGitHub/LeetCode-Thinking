
## 题目地址
 https://leetcode-cn.com/problems/contains-duplicate-iii/ 

## 题目描述
```
给定一个整数数组，判断数组中是否有两个不同的索引 i 和 j，使得 nums [i] 和 nums [j] 的差的绝对值最大为
t，并且 i 和 j 之间的差的绝对值最大为 ķ。

示例 1:

输入: nums = [1,2,3,1], k = 3, t = 0
输出: true
示例 2:

输入: nums = [1,0,1,1], k = 1, t = 2
输出: true
示例 3:

输入: nums = [1,5,9,1,5,9], k = 2, t = 3
输出: false

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/contains-duplicate-iii
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。
```

## 思路

>   此题可以采用双重循环，第一重循环数组，第二重可以在下标相差k的数据。在两重循环中如果找到相差小于t的数据，则返回true。
>
>   程序如下：
>
>   ```java
>   class Solution {
>       public boolean containsNearbyAlmostDuplicate(int[] nums, int k, int t) {
>           for (int i = 0; i < nums.length; i++) {
>               int num = nums[i];
>               for (int j = i + 1; (j <= i + k) && j < nums.length; j++) {
>                   if (num > nums[j]) {
>                       if (num - nums[j] <= t) {
>                           return true;
>                       }
>                   } else {
>                       if (nums[j] - num <= t) {
>                           return true;
>                       }
>                   }
>               }
>           }
>           return false;
>       }
>   }
>   ```
>
>   上述程序存在一个问题，测试用例如下:
>
>   ```java
>   new int[]{-1, 2147483647}, 1, 2147483647
>   ```
>
>   int 类型溢出，所以需要转换为long 类型。最终程序如下：
>
>   ```java
>   class Solution {
>       public boolean containsNearbyAlmostDuplicate(int[] nums, int k, int t) {
>           for (int i = 0; i < nums.length; i++) {
>               long num = nums[i];
>               for (int j = i + 1; (j <= i + k) && j < nums.length; j++) {
>                   if (num > nums[j]) {
>                       long value = num - (long)nums[j];
>                       if (num - nums[j] <= t) {
>                           return true;
>                       }
>                   } else {
>                       long value = (long) nums[j] - num;
>                       if (value <= t) {
>                           return true;
>                       }
>                   }
>               }
>           }
>           return false;
>       }
>   }
>   ```
>
>   

## 结果

> 执行用时 :507 ms, 在所有 java 提交中击败了5.10%的用户
>
> 内存消耗 :37.5 MB, 在所有 java 提交中击败了78.93%的用户
