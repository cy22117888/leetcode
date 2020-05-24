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

方法1、暴力法（一一比较）
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
