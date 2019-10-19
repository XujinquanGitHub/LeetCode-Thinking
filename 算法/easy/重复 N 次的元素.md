
## 题目地址
 https://leetcode-cn.com/problems/n-repeated-element-in-size-2n-array/ 

## 题目描述
```
在大小为 2N 的数组 A 中有 N+1 个不同的元素，其中有一个元素重复了 N 次。

返回重复了 N 次的那个元素。

 

示例 1：

输入：[1,2,3,3]
输出：3
示例 2：

输入：[2,1,2,5,3,2]
输出：2
示例 3：

输入：[5,1,5,2,5,3,5,4]
输出：5
 

提示：

4 <= A.length <= 10000
0 <= A[i] < 10000
A.length 为偶数

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/n-repeated-element-in-size-2n-array
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。
```

## 思路

>   既然是2N个元素，其中有一个数据重复N次。那么还有N个不是该元素。但数组中有N+1个不同元素，减去重得的1个元素，就是说有N个不同元素，那么就是说除去重复元素剩下的元素不可能重复。只需要定义一个HashSet，然后循环数组向HashSet中添加元素，如果添加失败就表示是重复元素，直接返回重复元素即可。
>
>   程序如下：
>
>   ```java
>class Solution {
>       public int repeatedNTimes(int[] A) {
>           HashSet<Integer> hashSet = new HashSet<>();
>            for (int i = 0; i < A.length; i++) {
>                int num = A[i];
>                if (!hashSet.add(num)) {
>                    return num;
>                }
>            }
>            return -1;
>        }
>    }
>    ```
>    
>    

## 结果

> 执行用时 :1 ms, 在所有 java 提交中击败了97.42%的用户
>
> 内存消耗 :38.6 MB, 在所有 java 提交中击败了95.01%的用户
