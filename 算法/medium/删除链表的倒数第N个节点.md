
## 题目地址
 https://leetcode-cn.com/problems/remove-nth-node-from-end-of-list/submissions/ 

## 题目描述
```
给定一个链表，删除链表的倒数第 n 个节点，并且返回链表的头结点。

示例：

给定一个链表: 1->2->3->4->5, 和 n = 2.

当删除了倒数第二个节点后，链表变为 1->2->3->5.
说明：

给定的 n 保证是有效的。

进阶：

你能尝试使用一趟扫描实现吗？

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/remove-nth-node-from-end-of-list
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。
```

## 思路

>   1、先定义两个变量len 链表长度，deletePreNode要删除节点的上一个节点。
>
>   2、循环链表查看长度是否大于要删除节点的倒数。如果是将deletePreNode向下移一位。
>   
>    ​       第二步可以这么理解，假定：给定一个链表: 1->2->3->4->5, 和 n = 2.
>    
>    ​		第一次循环 Head为1，len 为1 
>    
>    ​		第二次循环 Head为2    len 为 2
>    
>    ​		第三次循环 Head为3    len为 3
>    
>    ​		此时len大于n deletePreNode为1
>    
>    ​		如此循环下去 len的长度和 delePreNode所在位置相差3个元素。
>    
>    循环完成时就找到了要删除节点的上一个节点，只需要移除下一个节点即可。具体程序如下：
>    
>    ```java
>    class Solution {
>        public ListNode removeNthFromEnd(ListNode head, int n) {
>            ListNode dumpHead = new ListNode(0);
>            dumpHead.next = head;
>            int len = 0;
>            ListNode deletePreNode = dumpHead;
>            while (head != null) {
>                len++;
>                if (len > n) {
>                    deletePreNode = deletePreNode.next;
>                }
>                head = head.next;
>            }
>            if (deletePreNode.next != null) {
>                deletePreNode.next = deletePreNode.next.next;
>            }
>            return dumpHead.next;
>        }
>    }
>    ```
>    
>    

## 结果

> 执行用时 :0 ms, 在所有 Java 提交中击败了100.00%的用户
>
> 内存消耗 :34.7 MB, 在所有 Java 提交中击败了87.18%的用户
