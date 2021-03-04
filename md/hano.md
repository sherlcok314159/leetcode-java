*题目链接*
 
 https://leetcode-cn.com/problems/hanota-lcci/

*题目介绍*
********************************
面试题 08.06. 汉诺塔问题

在经典汉诺塔问题中，有 3 根柱子及 N 个不同大小的穿孔圆盘，盘子可以滑入任意一根柱子。一开始，所有盘子自上而下按升序依次套在第一根柱子上(即每一个盘子只能放在更大的盘子上面)。移动圆盘时受到以下限制:
 
(1) 每次只能移动一个盘子;
 
(2) 盘子只能从柱子顶端滑出移到下一根柱子;

(3) 盘子只能叠在比它大的盘子上。

请编写程序，用栈将所有盘子从第一根柱子移到最后一根柱子。

你需要原地修改栈。

示例1:

 输入：A = [2, 1, 0], B = [], C = []
 
 输出：C = [2, 1, 0]

********************************
**解题思路**

其实汉诺塔问题，就是一个递归问题。

递归的思想很重要，假如把这个问题**分解**成一个很**小的问题**，我该怎么做。那么，如果小问题能解决，那么这个问题在哪个地方进行了**复杂化**

因为无论是大问题还是小问题，它们往往**共享**着同一个**本质内核**，而那往往也是解决问题的关键。

A：1个。你会如何做？直接拿过去，很简单！

A：2个。复杂点了，刚刚我们已经解决了一个了，那我们能不能把这个问题转换为1个呢？把A的一个拿到B上，那么问题就迎刃而解了。

A：3个。更复杂了，那我们能不能也像之前一样，把A变成1个呢？把A上面2个拿到B上，那么A不就剩下1个了。再把B上的两个拿过去不就结束了。（可以**类比**一下A：2个的情况，只是变成了B到C，A是过渡的柱子）

![](https://github.com/sherlcok314159/leetcode-java/blob/main/Images/hano_init.png)

![](https://github.com/sherlcok314159/leetcode-java/blob/main/Images/hano_2.png)

![](https://github.com/sherlcok314159/leetcode-java/blob/main/Images/hano_3.png)

![](https://github.com/sherlcok314159/leetcode-java/blob/main/Images/hano_4.png)

```java
class Solution {
    public void hano(int n,List<Integer> A, List<Integer> B, List<Integer> C) {
        // 基例 A上只有一个
        if (n == 1) {
            C.add(A.remove(A.size() - 1)); // A别忘了清空
            return; //不返回值，但是会中断下面进程
        } else {
            hano(n-1,A,C,B);
            hano(1,A,B,C);
            hano(n-1,B,A,C);
        }
    }
    public void hanota(List<Integer> A, List<Integer> B, List<Integer> C) {
        hano(A.size(),A,B,C);
    }
}

***

*最优解*