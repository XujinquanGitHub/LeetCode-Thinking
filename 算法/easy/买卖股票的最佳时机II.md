## 题目地址
 https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock-ii/ 
 
## 题目描述
```
给定一个数组，它的第 i 个元素是一支给定股票第 i 天的价格。
 
设计一个算法来计算你所能获取的最大利润。你可以尽可能地完成更多的交易（多次买卖一支股票）。
 
注意：你不能同时参与多笔交易（你必须在再次购买前出售掉之前的股票）。
 
示例 1:
 
输入: [7,1,5,3,6,4]
输出: 7
解释: 在第 2 天（股票价格 = 1）的时候买入，在第 3 天（股票价格 = 5）的时候卖出, 这笔交易所能获得
利润 = 5-1 = 4 。
     随后，在第 4 天（股票价格 = 3）的时候买入，在第 5 天（股票价格 = 6）的时候卖出, 这笔交易所能获得
     利润 = 6-3 = 3 。
示例 2:
 
输入: [1,2,3,4,5]
输出: 4
解释: 在第 1 天（股票价格 = 1）的时候买入，在第 5 天 （股票价格 = 5）的时候卖出, 这笔交易所能获得
利润 = 5-1 = 4 。
     注意你不能在第 1 天和第 2 天接连购买股票，之后再将它们卖出。
     因为这样属于同时参与了多笔交易，你必须在再次购买前出售掉之前的股票。
示例 3:
 
输入: [7,6,4,3,1]
输出: 0
解释: 在这种情况下, 没有交易完成, 所以最大利润为 0。
 
来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock-ii
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。
```
 
## 思路
 
>   既然是利益最大化还可以连续多次操作，那就先拿一组数据看看怎么利益最大化以[7,1,5,3,6,4] 为利先选择一个低点买入，假设这个低点是第一个数7，循环到第二个发现是1，比上一个低点更低，替换到低点的值。循环到下一个，发现是5，比上一个低点低有利可图，不过不要急着卖出，还要看看明天的点是不是更高。如果更高就先不卖继续寻找下一个更高点。如果明天比今天低则卖出获利。在明天再买入。
>
>   具体程序如下：
>
>   ```java
>   class Solution {
>       public int maxProfit(int[] prices) {
>           int result = 0;
>           int length = prices.length;
>           if (length == 0) {
>               return result;
>           }
>           int startValue = prices[0];
>           for (int i = 1; i < length - 1; i++) {
>               int currentPrice = prices[i];
>               startValue = Math.min(startValue, currentPrice);
>               if (currentPrice > startValue && currentPrice > prices[i + 1]) {
>                   result += currentPrice - startValue;
>                   startValue = currentPrice;
>               }
>           }
>           if (prices[length - 1] > startValue) {
>               result += prices[length - 1] - startValue;
>           }
>           return result; 
>       }
>   }
>   ```
>
 
## 结果
 
> 执行用时 :1 ms, 在所有 java 提交中击败了99.99%的用户
>
> 内存消耗 :37.3 MB, 在所有 java 提交中击败了69.57%的用户
