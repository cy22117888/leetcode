28、实现strStr()
===

实现 strStr() 函数。<br>
给定一个 haystack 字符串和一个 needle 字符串，在 haystack 字符串中找出 needle 字符串出现的第一个位置 (从0开始)。<br>
如果不存在，则返回  -1。<br>

示例 1:<br>
```
输入: haystack = "hello", needle = "ll"
输出: 2
```
示例 2:<br>
```
输入: haystack = "aaaaa", needle = "bba"
输出: -1
```
说明:<br>
* 当 needle 是空字符串时，我们应当返回什么值呢？这是一个在面试中很好的问题。
* 对于本题而言，当 needle 是空字符串时我们应当返回 0 。这与C语言的 strstr() 以及 Java的 indexOf() 定义相符。

``
来源：力扣（LeetCode）
链接：https://leetcode-cn.com/problems/implement-strstr
著作权归领扣网络所有。商业转载请联系官方授权，非商业转载请注明出处。
``

### 方法1、暴力法（一一比较）
```
public int strStr(String haystack, String needle) {
    // special case
    if (haystack == null || haystack == "") return -1;
    if (needle == "") return 0;

    int L = needle.length(), n = haystack.length();

    for (int start = 0; start < n - L + 1; ++start) {
        if (haystack.substring(start, start + L).equals(needle)) {
            return start;
        }
    }
    return -1;
}
```

### 方法2、KMP算法
```
/* KMP算法 */
public int strStr(String haystack, String needle) {
    // special case
    if (needle.equals("")) return 0;
    if (haystack == null || haystack.equals("")) return -1;

    // 构造KMP中的dp矩阵
    int m = needle.length();
    // 各个状态(行)遇到下一个字符(列)跳转到哪个状态
    int[][] dp = new int[m][256]; 
    // 影子状态
    int X = 0;  
    dp[0][needle.charAt(0)] = 1;
    for (int i = 1; i < m; i++) {
        for (int j = 0; j < 256; j++) {
            //假设下个字符不匹配，此时要回去看影子状态，从而得知跳转到哪个状态
            dp[i][j] = dp[X][j];  
        }
        // 只有pat上i的字符匹配，跳转到下个状态
        dp[i][needle.charAt(i)] = i + 1;  
        // 更新影子状态
        X = dp[X][needle.charAt(i)];
    }

    // 构造dp完成后，开始search
    // 初始状态为0
    int s = 0;
    for (int i = 0; i < haystack.length(); i++) {
        s = dp[s][haystack.charAt(i)];
        if (s == m) {
            return i - m + 1;
        }
    }

    // 匹配失败，返回-1
    return -1;
}
```
