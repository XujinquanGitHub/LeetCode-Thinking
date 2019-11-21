
## 题目地址
 https://leetcode-cn.com/problems/excel-sheet-column-number/ 

## 题目描述
```
给定一个Excel表格中的列名称，返回其相应的列序号。

例如，

    A -> 1
    B -> 2
    C -> 3
    ...
    Z -> 26
    AA -> 27
    AB -> 28 
    ...
示例 1:

输入: "A"
输出: 1
示例 2:

输入: "AB"
输出: 28
示例 3:

输入: "ZY"
输出: 701

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/excel-sheet-column-number
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。
```

## 思路

>   此题类似数字中的进制，不过数字大多是十进制，而本题是26进制。所以结果可以转制成公式
>
>   result=s1*26^(L-1) + s2 * 26^(L-2)+....+sn。
>   
>    其中s1、s2 代表s中的各个字符，L代表长度。关于每个字符所代表的数，我最开始打算用HashMap存储，不过参考leetcode中评论区发现更巧妙的办法， 因为字符在转换成int型时按顺序加一，所以可以转制成如下公式：  s.charAt(i) - 'A' + 1; 最终程序如下：
>    
>    ```java
>    class Solution {
>        public int titleToNumber(String s) {
>            int result = 0;
>            int pow = 0;
>            for (int i = s.length() - 1; i > -1; i--) {
>                int num = s.charAt(i) - 'A' + 1;
>                result += num * Math.pow(26, pow);
>                pow++;
>            }
>            return result;
>        }
>    }
>    ```
>   

## 结果

> 执行用时 :2 ms, 在所有 java 提交中击败了74.85%的用户
>
> 内存消耗 :36.1 MB, 在所有 java 提交中击败了36.96%的用户
