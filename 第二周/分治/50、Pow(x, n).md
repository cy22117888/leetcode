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
        if (x == 0) return 0.0;
        if (x == 1) return 1.0;
        //指数为负数时，对底数、指数进行数学转换
        if (n < 0) {
            x= 1 / x;
            n = -n;
        }

        return fastPow(x, n);
    }

    //递归方法
    private double fastPow(double x, int n) {
        if (n == 0) {
            return 1.0;
        }
        double half = fastPow(x, n / 2);
        if (n % 2 == 0) {
            return half * half;
        } else {
            return half * half * x;
        }
    }
    
}
```
