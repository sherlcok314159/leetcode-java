*题目链接*：
  
  https://leetcode-cn.com/problems/fibonacci-number/

斐波那契数，通常用F(n)表示，形成的序列称为 斐波那契数列 。该数列由 0 和 1 开始，后面的每一项数字都是前面两项数字的和。也就是：


*F(0) = 0*，*F(1) = 1*
*F(n) = F(n - 1) + F(n - 2)*，其中 *n > 1*
给你 n ，请计算 F(n) 。

示例 1：

输入：2
输出：1

解释：*F(2) = F(1) + F(0) = 1 + 0 = 1*
*******
***纯递归***
*******
  递归有两个基本要素：基例以及递归关系式。
  * 基例：*F(0) = 0*,*F(1) = 1*,即递归结束的地方
  * 递归关系式：*F(n) = F(n-1) + F(n- 2)*  
  ********************************  

```java
class Solution {
    public int fib(int n) {
        if (n <= 1) {
            return n;
        } else {
            return fib(n-1) + fib(n-2);
        }
    }
}
```

***
滑动窗口

其实上面的解法是暴力解法，不够优雅，之所以耗时长，主要是**回头迭代函数**









```java
class Solution {
    public int fib(int n) {
        int first = 0,second = 1;
        while (n --> 0) {
            int temp = first + second;
            first = second;
            second = temp;
        }
        return first;
    }
}
```