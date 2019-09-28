
## 题目地址
https://leetcode-cn.com/problems/nth-highest-salary/

## 题目描述
```
编写一个 SQL 查询，获取 Employee 表中第 n 高的薪水（Salary）。

+----+--------+
| Id | Salary |
+----+--------+
| 1  | 100    |
| 2  | 200    |
| 3  | 300    |
+----+--------+
例如上述 Employee 表，n = 2 时，应返回第二高的薪水 200。如果不存在第 n 高的薪水，那么查询应返回 null。

+------------------------+
| getNthHighestSalary(2) |
+------------------------+
| 200                    |
+------------------------+

来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/nth-highest-salary
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。
```

## 模板

> ```sql
> CREATE FUNCTION getNthHighestSalary(N INT) RETURNS INT
> BEGIN
>   RETURN (
>       # Write your MySQL query statement below.
>       
>   );
> END
> ```

## 思路

> 本题要求传入N ，就取出排名为N的薪水，所以可知需要对薪水去重之后排序，取得排名第N的薪水。所以可以先针对薪水分组然后倒序，SQL如下：
>
> ```sql
> SELECT Salary FROM Employee GROUP BY Salary  ORDER BY Salary DESC
> ```
>
> 如此之后再针对结果集做排序并且记录名次，SQL如下：
>
> ```sql
> SELECT ss.Salary, @rowno:=@rowno+1 AS Rank FROM  
> (SELECT Salary FROM Employee GROUP BY Salary  ORDER BY Salary DESC) AS ss,
> (SELECT (@rowno :=0) ) AS b
> ```
>
> 如此之后可以得到两列，薪水和薪水排名，接下来只需要将参数N和排序对比即可。最终SQL如下：
>
> ```sql
> CREATE FUNCTION getNthHighestSalary(N INT) RETURNS INT
> BEGIN
> RETURN (
>     SELECT  Salary FROM (SELECT ss.Salary, @rowno:=@rowno+1 AS Rank FROM  
>     (SELECT Salary FROM Employee GROUP BY Salary  ORDER BY Salary DESC) AS ss,
>     (SELECT (@rowno :=0) ) AS b) AS ts WHERE Rank=N
> );
> END
> ```
>
> 

## 结果

> 执行用时 :147 ms, 在所有 MySQL 提交中击败了94.28%的用户