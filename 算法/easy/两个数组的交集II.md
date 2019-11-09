
## 题目地址
 https://leetcode-cn.com/problems/intersection-of-two-arrays-ii/ 

## 题目描述
```
给定两个数组，编写一个函数来计算它们的交集。

示例 1:

输入: nums1 = [1,2,2,1], nums2 = [2,2]
输出: [2,2]
示例 2:

输入: nums1 = [4,9,5], nums2 = [9,4,9,8,4]
输出: [4,9]
说明：

输出结果中每个元素出现的次数，应与元素在两个数组中出现的次数一致。
我们可以不考虑输出结果的顺序。
进阶:

如果给定的数组已经排好序呢？你将如何优化你的算法？
如果 nums1 的大小比 nums2 小很多，哪种方法更优？
如果 nums2 的元素存储在磁盘上，磁盘内存是有限的，并且你不能一次加载所有的元素到内存中，你该怎么办？

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/intersection-of-two-arrays-ii
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。
```

## 思路

>   定义一个HashMap用来记录nums1中每个数出现的次数，循环num2查询HashMap中是否存在，如果存在把次数减一并且加到结果集中，如果不存在继续循环。程序如下：
>
>   ```java
>   class Solution {
>       public int[] intersect(int[] nums1, int[] nums2) {
>           List<Integer> arrayList = new ArrayList<>(nums1.length);
>           HashMap<Integer, Integer> map = new HashMap<>(nums1.length);
>           for (int i = 0; i < nums1.length; i++) {
>               int num = nums1[i];
>               Integer count = map.get(num);
>               if (count == null) {
>                   map.put(num, 1);
>               } else {
>                   count++;
>                   map.put(num, count);
>               }
>           }
>           int index = 0;
>           for (int i = 0; i < nums2.length; i++) {
>               int num = nums2[i];
>               Integer count = map.get(num);
>               if (count != null && count > 0) {
>                   arrayList.add(num);
>                   index++;
>                   count--;
>                   map.put(num, count);
>               }
>           }
>           int[] result = new int[arrayList.size()];
>           for (int i = 0; i < arrayList.size(); i++) {
>               result[i] = arrayList.get(i);
>           }
>           return result;
>       }
>   }
>   ```
>
>   

## 结果

> 执行用时 :6 ms, 在所有 java 提交中击败了62.05%的用户
>
> 内存消耗 :36.3 MB, 在所有 java 提交中击败了68.25%的用户
