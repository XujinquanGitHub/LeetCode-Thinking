
## 题目地址
https://leetcode-cn.com/problems/sqrtx/

## 题目描述
```
实现 int sqrt(int x) 函数。

计算并返回 x 的平方根，其中 x 是非负整数。

由于返回类型是整数，结果只保留整数的部分，小数部分将被舍去。

示例 1:

输入: 4
输出: 2
示例 2:

输入: 8
输出: 2
说明: 8 的平方根是 2.82842..., 
     由于返回类型是整数，小数部分将被舍去。

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/sqrtx
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。
```

## 思路

>   此题可采用二分法查找对应的平方根。初始程序如下：
>
>   ```java
>   class Solution {
>       public int mySqrt(int x) {
>           if (x <= 0) {
>               return 0;
>           }
>           if (x < 4) {
>               return 1;
>           }
>           int left = 0;
>           int right = x;
>           while (true) {
>               int middle = (left + right) / 2;
>               if (middle * middle == x) {
>                   return middle;
>               } else if (middle * middle < x) {
>                   if ((middle + 1) * (middle + 1) > x) {
>                       return middle;
>                   } else {
>                       left = middle;
>                   }
>               } else {
>                   if ((middle - 1) * (middle - 1) < x) {
>                       return middle - 1;
>                   } else {
>                       right = middle;
>                   }
>               }
>           }
>       }
>   }
>   ```
>
>   发现上面程序在x **2147395599** 在product 超出 int 范围的值，改有 除法比较。最终程序如下：
>
>   ```java
>   class Solution {
>       public int mySqrt(int x) {
>          if (x <= 0) {
>               return 0;
>           }
>           if (x < 4) {
>               return 1;
>           }
>           int left = 0;
>           int right = x;
>           while (true) {
>               int middle = (left + right) / 2;
>               if (middle == x / middle) {
>                   return middle;
>               } else if (middle < x / middle) {
>                   if ((middle + 1) > x / (middle + 1)) {
>                       return middle;
>                   } else {
>                       left = middle;
>                   }
>               } else {
>                   if ((middle - 1) < x / (middle - 1)) {
>                       return middle - 1;
>                   } else {
>                       right = middle;
>                   }
>               }
>           }
>   
>       }
>   }
>   ```
>
>   

## 结果

> 执行用时 :2 ms, 在所有 Java 提交中击败了94.71%的用户
>
> 内存消耗 :33.3 MB, 在所有 Java 提交中击败了79.12%的用户
