---
layout: post
title: 深入理解计算机系统练习题答案
categories: Basic
description: 深入理解计算机系统（原书第2版）练习题答案。
keywords: CSAPP, 深入理解计算机系统
---

约定：2^n表示二的n次方。

###第2章

**练习题2.1** 完成下列数字转换：

A. 将0x39A7F8转换为二进制。

`0011 1001 1010 0111 1111 1000`

B. 将二进制11001001001111011转换为十六进制。

`0xC97B`

C. 将0xD5E4C转换为二进制。

`1101 0101 1110 0100 1100`

D. 将二进制1001101110011110110101转换为十六进制。

`0x26E7B5`

**练习题2.2** 填写下表中的空白项，给出2的不同次幂的二进制和十六进制表示：

|n|2^n（十进制）|2^n（十六进制）|
|:---:|:---:|:---:|
|9|512|0x200|
|19|524288|0x80000|
|14|16384|0x4000|
|16|65536|0x1000|
|17|131072|0x2000|
|5|32|0x20|
|7|128|0x80|

**练习题2.3** 一个字节可以用两个十六进制表示。填写下表中缺失的项，给出不同字节模式的十进制，二进制和十六进制值。

|十进制|二进制|十六进制|
|:---:|:---:|:---:|
|0|0000 0000|0x00|
|167|1010 0111|0xA7|
|62|0011 1110|0x3E|
|188|1100 1101|0xBC|
|55|0011 0111|0x37|
|136|1000 1000|0x88|
|243|1111 0011|0xF3|
|82|0101 0010|0x52|
|172|1010 1100|0xAC|
|224|1110 0111|0xE7|

**练习题2.4** 不将数字转换为十进制或者二进制，试着解答下面的算术题，答案要用十六进制表示。提示：将执行十进制加法和减法所使用的方法改成以16为基数。

A. 0x503c+0x8=0x5044

B. 0x503c-0x40=0x4ffc

C. 0x503c+64=0x507c

D. 0x50ea-0x503c=0xae

**练习题2.5** 思考下面对show\_bytes的三次调用：

int val=0x87654321;

byte\_pointer valp=(byte\_pointer)&val;

show\_bytes(valp, 1);/\* A.\*/

show\_bytes(valp, 2);/\* B.\*/

show\_bytes(valp, 3);/\* C.\*/

指出在小端法机器和大端法机器上，每次调用的输出值。

A. 小端法：` 21` 大端法：` 87`

B. 小端法：` 21 43` 大端法：` 87 65`

C. 小端法：` 21 43 65` 大端法：` 87 65 43`

**练习题2.6** 使用show\_int和show\_float，我们确定整数3510593的十六进制数表示为0x00359141，而浮点数3510593.0的十六进制为0x4A564504。

A. 写出这两个十六进制值的二进制表示。

0x00359141的二进制表示：`0000 0000 0011 0101 1001 0001 0100 0001`

0x4A564504的二进制表示：`0100 1010 0101 0110 0100 0101 0000 0100`

B. 移动这两个二进制串的相对位置，使得它们相匹配的位数最多。有多少位相匹配呢？

有21位相匹配。

C. 串中的什么部分不相匹配？

浮点数的指数偏差部分，二进制科学计数法的整数位默认为1。浮点数的二进制表示法参见<http://www.mazhuang.org/2015/01/19/printf/#ieee-754>

**练习题2.7** 下面对show\_bytes的调用将输出什么结果？

```
const char *s = "abcdef";
show_bytes( (byte_pointer)s, strlen(s));
```

注意字母'a'~'z'的ASCII码为0x61~0x7A。

输出结果：

` 61 62 63 64 65`

**练习题2.8** 填写下表，给出位向量的布尔运算的求值结果。

|运算|结果|
|:---:|:---:|
|a|[01101001]|
|b|[01010101]|
|~a|[10010110]|
|~b|[10101010]|
|a & b|[01000001]|
|a \| b|[01111101]|
|a ^ b|[00111100]|

**练习题2.9** 通过混合三种不同颜色的光（红色、绿色和蓝色），计算机可以在视频屏幕或者液晶显示器上产生彩色的画面。设想一种简单的方法，使用三种不同颜色的光，每种光都能打开或关闭，投射到玻璃屏幕上，如图所示：

```
Light Source        Glass Screen

RED ---                 ++
       \-----           ||
             \-----     ||    Observer
GREEN --------------->  ||      |>
               ----     ||
        ------/         ||
BLUE --/                ||
                        ++
```

那么基于光源R（红）、G（绿）、B（蓝）的关闭（0）或打开（1），我们就能够创建8种不同的颜色：

|R G B|颜色|
|:---:|:---:|
|0 0 0|黑色|
|0 0 1|蓝色|
|0 1 0|绿色|
|0 1 1|蓝绿色|
|1 0 0|红色|
|1 0 1|红紫色|
|1 1 0|黄色|
|1 1 1|白色|

这些颜色中的每一种都能用一个长度为3的位向量来表示，我们可以对它们进行布尔运算。

A. 一种颜色的补是通过关掉打开的光源，且打开关闭的光源而形成的。那么上面列出的8种颜色每一种的补是什么？

黑色 与 白色 互为补。

蓝色 与 黄色 互为补。

绿色 与 红紫色 互为补。

蓝绿色 与 红色 互为补。

B. 描述下列颜色应用布尔运算的结果：

蓝色 | 绿色 = 蓝绿色

黄色 & 蓝绿色 = 绿色

红色 ^ 红紫色 = 蓝色
