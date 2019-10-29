## 题目地址
 https://leetcode-cn.com/problems/contains-duplicate-ii/ 
 
## 题目描述
```
给定一个整数数组和一个整数 k，判断数组中是否存在两个不同的索引 i 和 j，使得 nums [i] = nums [j]，
并且 i 和 j 的差的绝对值最大为 k。
 
示例 1:
 
输入: nums = [1,2,3,1], k = 3
输出: true
示例 2:
 
输入: nums = [1,0,1,1], k = 1
输出: true
示例 3:
 
输入: nums = [1,2,3,1,2,3], k = 2
输出: false
 
来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/contains-duplicate-ii
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。
```
 
## 思路
 
>   1、定义一个HashMap变量用来记录元素和元素的下标。
>
>   2、循环数组查找HashMap中是否出现过该元素并且元素下标下于k，如果找到返回true 。
>
>   程序如下：
>
>   ```java
>   class Solution {
>        public boolean containsNearbyDuplicate(int[] nums, int k) {
>            HashMap<Integer, Integer> hashMap = new HashMap<>(nums.length);
>            for (int i = 0; i < nums.length; i++) {
>                int num = nums[i];
>                Integer index = hashMap.get(num);
>                if (index != null &&(i - index) <= k) {
>                    return true;
>                }
>                hashMap.put(num, i);
>            }
>            return false;
>        }
>    }
>    ```
>   
>   
 
## 结果
 
> 执行用时 :13 ms, 在所有 java 提交中击败了91.09%的用户
>
> 内存消耗 :42.7 MB, 在所有 java 提交中击败了85.18%的用户
