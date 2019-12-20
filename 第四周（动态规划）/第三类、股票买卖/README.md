股票买卖问题的动态规划通用思路
===

### 1、状态储存数组
```
int[][][] dp = new int[i][k][2];
其中：
    i：天数    0 <= i < prices.length
    k：当天为止已完成的交易次数     1 <= k <= K（K为最大交易次数）
    2：当天的股票持有状态   以0为未持股，1为持股（因只有2种状态，故此维空间长度为2）
```

### 2、基准情况
```
dp[0][k][0] = 0         解释：第一天，手中未持股，说明还没有开始交易，这时候的利润当然是 0 。

dp[0][k][1] = -prices[0]            解释：第一天，刚买入股票，所以利润为亏损的第一天股票价格

dp[i][0][0] = 0         解释：因为 k 是从 1 开始的，所以 k = 0 意味着根本不允许交易，这时候利润当然是 0 。

dp[i][0][1] = Integer.MIN_VALUE     解释：不允许交易的情况下，是不可能持有股票的，用负无穷表示这种不可能。
```

### 3、状态转移方程
```
dp[i][k][0] = Math.max(dp[i-1][k][0], dp[i-1][k-1][1] + prices[i]);
dp[i][k][1] = Math.max(dp[i-1][k][1], dp[i-1][k-1][0] - prices[i]);
```


#### 本类中所有动态规划解法的思路来源于以下链接：
``
作者：labuladong
链接：https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock-iii/solution/yi-ge-tong-yong-fang-fa-tuan-mie-6-dao-gu-piao-wen/
来源：力扣（LeetCode）
著作权归作者所有。商业转载请联系作者获得授权，非商业转载请注明出处。
``
