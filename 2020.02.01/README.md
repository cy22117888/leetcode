算法之位运算(针对二进制数值)
===


#### 一、按位运算

<table>
  <tr>
    <td width="33%">
      1、按位与  & <br>
      特点：全1才为1（同 与门）<br>          
      特征表：<br>
      <table>
        <tr>
          <th>&</th> <th>0</th> <th>1</th>
        </tr>
        <tr>
          <th>0</th> <td>0</td> <td>0</td>
        </tr>
        <tr>
          <th>1</th> <td>0</td> <td>1</td>
        </tr>
      </table>
    </td>
    <td width="33%">
      2、按位或  | <br>
      特点：有1即为1（同 或门）<br>          
      特征表：<br>
      <table>
        <tr>
          <th>|</th> <th>0</th> <th>1</th>
        </tr>
        <tr>
          <th>0</th> <td>0</td> <td>1</td>
        </tr>
        <tr>
          <th>1</th> <td>1</td> <td>1</td>
        </tr>
      </table>
    </td>
    <td width="33%">
      3、按位亦或   ^ <br>
      特点：同0异1（同 亦或门）<br>          
      特征表：<br>
      <table>
        <tr>
          <th>^</th> <th>0</th> <th>1</th>
        </tr>
        <tr>
          <th>0</th> <td>0</td> <td>1</td>
        </tr>
        <tr>
          <th>1</th> <td>1</td> <td>0</td>
        </tr>
      </table>
    </td>
  </tr>
</table>

#### 二、移位运算


1、向左移位    << <br>
新增空位用0填充<br>
```
例：
0010 << 2 == 1000
```

2、向右移位（带符号）   >> <br>
新增空位用符号位值填充<br>
```
例：
0100 >> 1 == 0010
1100 >> 1 == 1110
```

3、向右移位（无符号）   >>> <br>
新增空位均用0填充<br>
```
例：
1100 >>> 1 == 0110
```




