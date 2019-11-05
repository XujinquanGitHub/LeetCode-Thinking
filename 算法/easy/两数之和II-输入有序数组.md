## 题目地址
 https://leetcode-cn.com/problems/two-sum-ii-input-array-is-sorted/ 
 
## 题目描述
```
给定一个已按照升序排列 的有序数组，找到两个数使得它们相加之和等于目标数。
 
函数应该返回这两个下标值 index1 和 index2，其中 index1 必须小于 index2。
 
说明:
 
返回的下标值（index1 和 index2）不是从零开始的。
你可以假设每个输入只对应唯一的答案，而且你不可以重复使用相同的元素。
示例:
 
输入: numbers = [2, 7, 11, 15], target = 9
输出: [1,2]
解释: 2 与 7 之和等于目标数 9 。因此 index1 = 1, index2 = 2 。
 
来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/two-sum-ii-input-array-is-sorted
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。
```
 
## 暴力法
 
>   直接采用双重循环相加对比目标值是否相等，如果相等直接返回。程序如下：
>
>   ```java
>   class Solution {
>        public int[] twoSum(int[] numbers, int target) {
>            for (int i = 0; i < numbers.length; i++) {
>                for (int j = i + 1; j < numbers.length; j++) {
>                    if (numbers[i] + numbers[j] == target) {
>                        return new int[]{i + 1, j + 1};
>                    }
>                }
>            }
>            return null;
>        }
>    }
>    ```
>    
>    
 
## 结果
 
> 时间复杂度为 O(n^2)  空间复杂度为 O(1)
>
> 执行用时 :111 ms, 在所有 java 提交中击败了11.06%的用户
>
> 内存消耗 :36.2 MB, 在所有 java 提交中击败了95.69%的用户
 
## 二分搜索
 
>   循环数组，用目标值送去当前元素值，然后用二分法在元素中查找剩下数字，找到之后对比下标，如果是不同的下标直接返回。程序如下：
>
>   ```java
>   class Solution {
>       public int[] twoSum(int[] numbers, int target) {
>           for (int i = 0; i < numbers.length; i++) {
>               int findTarget = target - numbers[i];
>               int targetIndex = bSearch(numbers, findTarget);
>               if (targetIndex != i && targetIndex != -1) {
>                  if (i < targetIndex) {
>                       return new int[]{i + 1, targetIndex + 1};
>                   } else {
>                       return new int[]{targetIndex + 1, i + 1};
>                   }
>               }
>           }
>           return null;
>       }
>       int bSearch(int a[], int key) {
>           int low = 0;
>           int high = a.length - 1;
>           while (low <= high) {
>               int mid = low + (high - low) / 2;
>               if (a[mid] > key) high = mid - 1;
>               else if (a[mid] < key) low = mid + 1;
>               else return mid;
>           }
>           return -1;
>       }
>   }
>   ```
>
>   
 
## 结果
 
> 时间复杂度为 O(n * log n)    空间复杂度为 O(1)
>
> 执行用时 :3 ms, 在所有 java 提交中击败了33.51%的用户
>
> 内存消耗 :37.3 MB, 在所有 java 提交中击败了90.38%的用户
