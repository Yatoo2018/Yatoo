---
layout: post
title:  "机器眼睛里的小数"
date:   2018-06-13 17:09:57 +0800
categories: JavaScript
---
### 前言
这篇文章我想写下关于最近我学习的小数部分的内容。
本文首次发表于https://segmentfault.com/a/1190000015306417

A:what？ 小数，什么鬼？
B:我研究过大数相加，你说的是那个大数对应的小数吗？

你没听错，就是小数，不过是像 0.1，0.75，1.5这样的小数，不是很小的整数哟( ⊙ o ⊙ )！
### 关于小数的问题
关于小数你了解多少呢？先来一个小数的运算语句。  
```javascript
Number(0.1).toString(2)
// 如果你把这个语句JavaScript引擎里执行下，你会得到下面这个字符串
// "0.0001100110011001100110011001100110011001100110011001101"
```
如果这个难不到你，那三步走，拿起你的小黑鼠，移到页面上部的X，按下左键，然后88。因为本文不适合你了😒（有脾气了）
如果不幸，你被难倒了，那我😏(斜眼笑)。
### 解释奇怪的字符串
要解释这个字符串的来历，可得费点功夫了，施主，你准备好瓜子，板凳了吗？
（长篇警告）
鉴于你们都不耐其烦的看到这了，那我就耐心的来扒一扒，为什么是这么个字符串。。。
我们分为下面几步来解释下这个字符串的来历：
 1. 上面问题中JavaScript语句的功能
 2. 信息在计算机中是如何存储的
 3. 小数在计算机中是如何存储的
 4. 小数在JavaScript中是如何表示的
 5. 这条语句结果的分析
那么我们就逐步来：
  
#### 语句功能
我们的语句是 Number(0.1).toString(2)
我们拆分下这个复合语句
```
let wrapNumber = Number(0.1);                 (1)
let binaryNumber = wrapNumber.toString(2);    (2)
```
语句(1)将一个基本类型的数值0.1,使用数值类型的构造器将其包装成wrapNumber
[补充内容:关于wrapNumber的类型][1]
因为[原始数值类型][2]的数值存在一些有用的方法，比如 toFixed方法，
和我们第二行语句中的toString()方法等。
[toString([radix])][3]方法的将数值转换成一个radix进制数值对象的字符串
所以到这一步，我们应该知道，"0.0001100110011001100110011001100110011001100110011001101" 代表的是十进制数0.1的2进制表示形式
[如果你看了这篇就懂了，那就不用继续看下去了][4]
要了解这个字符串我们必须得了解一下，数据在计算机里是怎么表示的，又是怎么样运算的？
### 数据的表示
#### 计算机中的信息表示
计算机内部的实现：在现代计算机内部，所有的信息（图，声，字符串，数值等）都是通过二进制数值的形式来表示的；
推断：只要理解了二进制数表示信息的方法及其运算原理，对于理解小数在计算机中的存储那就更进一步了。
#### 计算机中使用二进制表示数据
那么现实中的计算机为什么内部使用二进制来表示信息呢，我们人不是更习惯十进制嘛，为什么不让机器也弄十进制呀。
这就得从计算机的组成说起，计算机都是由数字集成电路电子部件组成的。而这些电子部件都会有和其他部件连接的引脚，而所有的引脚上只有直流电压0V和5V俩个状态。二进制数刚好只有俩个状态，与电子部件的能表示俩个状态的特性刚好吻合，决定了计算机中的信息用二进制数来表示最为简单和高效。所以计算机处理信息的最小单位--位，就相当于二进制中的一位。位的英文bit是二进制数位（binary digit）的缩写。
而计算机中处理信息的基本计量单位是字节(Byte). 8位为1个字节. 位是最小单位,字节是基本单位。
所以我们表示
十进制的1，    二进制:00000001 一个字节来表示
十进制的6，    二进制:\<em style="text-decoration:line-through;font-style:normal;color:red;">00100111\</em> 00000110(Golden纠正) 一个字节来表示 0～2^8-1的数共2^8个数
十进制的512，二进制:  000000001 000000000 俩个字节来表示 0～2^16-1共2^16个数 
二进制数转十进制数的方法，简单概括为：按权相加。
![clipboard.png](https://segmentfault.com/img/bVbckuC?w=352&h=96)

对于XX进制数之间的转换我在这里就不赘述了，不是本篇文章讨论的核心问题：
所以程序中使用的十进制数，在计算机中会被编译为二进制数进行运算。
更多详细的内容：请参考[《程序是怎么跑起来的》][5]:中第二章-数据是用二进制数表示的
### 小数的表示法
小数和浮点数的区别相关文章可以参考迷渡大佬的文章
[代码之谜（四）- 浮点数（从惊讶到思考)][6]

那么我们再想想，十进制整数都是可以成功使用更多位的二进制数来表示，那小数呢？
比如从0~1就有无限多个小数，而计算机中用什么样的方式来表示这无限多个小数呢？
答案是不能全部表示；      惊讶后又点了点头.jpg

根据现在编程语言广泛采用的国际标准IEEE 754中制定的浮点数的表示方式
下面三张图来自[《程序是怎么跑起来的》][7]
![clipboard.png](https://segmentfault.com/img/bVbcnVc?w=577&h=371)
双精度和单精度对应的指数和尾数的长度入下图：
![clipboard.png](https://segmentfault.com/img/bVbcnVe?w=586&h=333)
依据浮点数表示法，我们可以将0.75表示成
![clipboard.png](https://segmentfault.com/img/bVbcnVx?w=571&h=198)

为了表示数的唯一性，标准对表示的形式也做了细致的规定：只能使用图3-5 中第一行的这种形式

如果看完上图还未理解本小节内容，请参考下面推荐的文章；
[浮点数的二进制表示][8] 
注：*看这篇文章可以更细致的理解这节的内容*
[《程序是怎么跑起来的第三章》][9]：计算机进行小数计算时出错的原因 
注：*看这篇可以理解到更多计算机的机制相关内容*
我的英文不够好，其他同学如果英文好：请直接阅读[IEEE 754][10]，WIKI中的内容
[IEEE 754 双精度 64 位浮点数][11]
### JavaScript中的小数
我们继续探索一下JavaScript中小数的表示：[Annotated ECMAScript 5.1][12]
ES6中Number类型的描述：
> primitive value corresponding to a double-precision 64-bit binary format IEEE 754-2008 value
Number类型的原始值对应于双精度64位二进制格式IEEE 754-2008的值;
所以说ECMA中的数都是采用IEEE754标准，小数的表示和我们看的上面的浮点数的表示是一致的。
注意：**整数也是这么表示的哦，只不过指数部分为正数而已。**
[详解 JavaScript 数据类型][13]
分析到这里，应该知道这个字符串是怎么来的了吧.
### 这个字符串的生成
可以利用下面这个小公式生成十进制小数对应的二进制字符串：
一个js的小工具：
[科学计数法表示的十进制浮点数转二进制字符串][14] 
如果你想写一个可以参考这篇文章中的步骤或者：
[ToString Applied to the Number Type][15]
[基础野：细说浮点数][16]
这篇文章主要是想去让自己了解浮点数的内容；
不过看了许多文章，都会提到规避这种计算机无法精确表示浮点数的实用方法，方便以后查阅。
方法一、小数转成整数后计算；
方法二、利用[bignumber][17]







### 补充部分：关于wrapNumber的类型

有人可能就有疑问了，这个wrapNumber是什么类型，是Number类型的实例对象吗？
我们用下面语句测试下
```
typeof wrapNumber === 'number'
Object.prototype.toString.call(wrapNumber) === "[object Number]"
Object.prototype.toString.call(0.1) === "[object Number]" //补充部分
```
结果一致，均可检测出wrapNumber为原始数值类型
但是它却不是Number类型的实例对象，仅仅是一个Number类型的值, 从下面语句可以看出。
```
wrapNumber instanceof Number === false
wrapNumber instanceof Object === false
wrapNumber === 0.1 // 值
let wrapNumberObj = new Number(0.1);
typeof wrapNumberObj === 'object'
wrapNumberObj instanceof Number === true
wrapNumberObj instanceof Object === true
Object.prototype.toString.call(wrapNumberObj) === "[object Number]"
wrapNumberObj.valueOf() === 0.1 //new 对象的取值方式
```
MDN中Number类型中关于无new构造的描述如下：

> In a non-constructor context (i.e., without the new operator), Number can be used to perform a type conversion.

所以大家在做类型检查的时候还是要区分下new构造和无new构造的区别；

相似文章：
<a href="https://segmentfault.com//a/1190000005022170" target="_blank">JS魔法堂：彻底理解0.1 + 0.2 === 0.30000000000000004的背后</a>  
<a href="https://segmentfault.com//a/1190000009084877" target="_blank">该死的IEEE-754浮点数，说「约」就「约」，你的底线呢？以JS的名义来好好查查你</a>  
<a href="https://segmentfault.com//a/1190000011328199" target="_blank">浮点数那些事儿</a>  
http://justjavac.com/codepuzzle/2012/11/02/codepuzzle-float-from-surprised-to-ponder.html  
http://justjavac.com/codepuzzle/2012/11/11/codepuzzle-float-who-stole-your-accuracy.html  
参考文章：
[IEEE 754-2008][18]  
[sec-terms-and-definitions-number-value][19]  
[JavaScript 中小数和大整数的精度丢失][20]  


  [1]: 一个待补充的链接
  [2]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number
  [3]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/toString
  [4]: http://es5.github.io/#x9.8.1
  [5]: http://www.ituring.com.cn/book/1136
  [6]: http://justjavac.com/codepuzzle/2012/11/02/codepuzzle-float-from-surprised-to-ponder.html
  [7]: http://www.ituring.com.cn/book/1136
  [8]: http://www.ruanyifeng.com/blog/2010/06/ieee_floating-point_representation.html
  [9]: http://www.ituring.com.cn/book/1136
  [10]: https://en.wikipedia.org/wiki/IEEE_754
  [11]: https://en.wikipedia.org/wiki/Floating-point_arithmetic#Internal_representation
  [12]: http://es5.github.io/#x8.5
  [13]: https://www.cnblogs.com/onepixel/p/5140944.html
  [14]: https://yatoo2018.github.io/utils/dist/#/
  [15]: http://es5.github.io/#x9.8.1
  [16]: https://segmentfault.com/a/1190000005015151
  [17]: https://github.com/MikeMcl/bignumber.js
  [18]: http://www.softelectro.ru/ieee754_en.html
  [19]: http://www.ecma-international.org/ecma-262/6.0/index.html#sec-terms-and-definitions-number-value
  [20]: http://demon.tw/copy-paste/javascript-precision.html