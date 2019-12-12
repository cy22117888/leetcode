50、Pow(x, n)
===
实现 pow(x, n) ，即计算 x 的 n 次幂函数。<br>

示例 1:<br>
```
输入: 2.00000, 10
输出: 1024.00000
```
示例 2:<br>
```
输入: 2.10000, 3
输出: 9.26100
```
示例 3:<br>
```
输入: 2.00000, -2
输出: 0.25000
解释: 2-2 = 1/22 = 1/4 = 0.25
```
说明:<br>
-100.0 < x < 100.0<br>
n 是 32 位有符号整数，其数值范围是 [−231, 231 − 1] 。<br>

``
来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/powx-n
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。
``

```
class Solution {
    public double myPow(double x, int n) {
         //特值判定
         if (x == 0 || n == 1) return x;
         //当n为下边界时，取反会越界，故用long类型来接收一下
         long longN = n;
         // 当n为负数时
         if (longN < 0) {
             x = 1 / x;
             longN = -longN;
         }
         //递归
        return recursion(x, longN);
    }

    //递归方法
    private double recursion(double x, long n) {
        //定义基准情况
        if (n == 0) return 1.0;
        //向下递归
        double half = recursion(x, n / 2);
        //定义本层业务逻辑
        if (n % 2 == 1) return half * half * x;
        else return half * half;
    }
}
```
