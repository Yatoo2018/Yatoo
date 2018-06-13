---
layout: post
title:  "机器眼睛里的小数"
date:   2018-06-13 17:09:57 +0800
categories: JavaScript
---

这篇文章我想写下关于最近我学习的小数部分的内容。

A:what？ 小数，什么鬼？

B:我研究过大数相加，你说的是那个大数对应的小数吗？

你没听错，就是小数，不过是像 0.1，0.75，1.5这样的小数，不是很小的整数哟( ⊙ o ⊙ )！

关于小数你了解多少呢？先来一个小数的语句，看难不难得到你。  
```javascript
Number(0.1).toString(2)
// 如果你把那个语句JavaScript引擎里执行下，你会得到下面这个字符串
// "0.0001100110011001100110011001100110011001100110011001101"
```
如果上面难不到你，那你需要鼠标挪到右上角，叉掉然后转身离开，因为本站不欢迎你了😒（有脾气了）
如果不幸，你被我难倒了，那我会😏(斜眼笑)。
（长篇警告）
要解释这个字符串的来历，可得费点功夫了，施主，你准备好瓜子，板凳了吗？
鉴于你们都不耐其烦的看到这了，那我就耐心的来扒一扒，为什么是这么个字符串。。。
要了解这个我们必须得了解一下，数据在计算机里是怎么表示的，又是怎么样运算的？


Check out the [Jekyll docs][jekyll-docs] for more info on how to get the most out of Jekyll. File all bugs/feature requests at [Jekyll’s GitHub repo][jekyll-gh]. If you have questions, you can ask them on [Jekyll Talk][jekyll-talk].

[jekyll-docs]: https://jekyllrb.com/docs/home
[jekyll-gh]:   https://github.com/jekyll/jekyll
[jekyll-talk]: https://talk.jekyllrb.com/
