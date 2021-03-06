---
layout: post
title: "一个特殊的正则表达式"
---
<style>
li {
    line-height: 40px;
    color: #333;
    border-bottom: 1px solid #eee;
}
</style>
## 正则表达式
实现一个 img三个字符随机组合，不重复出现 的正则表达式
经过群里同学们和老师的讨论最终确定结果为：/^((\[img\])(?!.*\2))+$/
我们可以将正则放在[正则铁路图工具](https://yatoo2018.github.io/regexper-static/build/index.html)中显示出铁路图
![正则铁路图](../../../assert/imgs/regexp-railroad.png)
这个结果的测试用例，请参见[测试项目](https://github.com/Yatoo2018/RegExp-showcase13)
在这里主要是想分步解析这个正则，所以我们将上述正则拆解一下, 如下图：
![正则拆解](../../../assert/imgs/reg-gmi.jpg)
我们先不管顺序哈，这个图做的比较粗糙，这个顺序只为了做个区分。
我们先看
 1. <code style="color:red">红色线条7</code>  ====>  <code style="font-size:border;color:black;">\[img\]</code> 表示匹配img这三个字符集中的任何一个
 2. <code style="color:yellow">黄色线条3</code>  ====>  <code style="font-size:border;color:black;">(\[img\])</code> 将表达式7作为一个分组
 3. <code style="color:red">红色线条6</code>  ====>  <code style="font-size:border;color:black;">.*\2</code> 表示匹配  任何字符串和\2 的字符串 这个\2其实就是（\[img\]）
    1. . => 匹配除换行符（\n、\r）之外的任何单个字符
    2. \* => 匹配前面的子表达式零次或多次
    3. \2 => 对所获取的匹配的引用，在这里表示匹配 group2匹配到的字符串
 4. <code style="color:green">绿色线条4</code>  ====> <code style="font-size:border;color:black;">(?!.*\2)</code> 正向否定断言，非捕获型匹配，表示匹配到6的内容都是否定的
 5. <code style="color:lightblue">浅蓝色线条5</code>  ====> <code style="font-size:border;color:black;">(\[img\])(?!.*\2)</code> 匹配(\[img\])中的一个字符，但是后面的字符串中不包含 **任意长度的任意字符串** 和 **(\[img\])这个表达式之前已经捕获到的那个字符** 的字符串
    1. 因为在整个表达式中((\[img\])(?!.*\2))是group1,（\[img\]）是group2, 所以\2就指的是（\[img\]）这个匹配group
 6. <code style="color:gray">灰色线条2</code>  ====> <code style="font-size:border;color:black;">((\[img\])(?!.*\2))</code> 将5进行分组 group1 引用的话 \1
 7. <code style="color:#ddd">白色线条1</code>  ====> <code style="font-size:border;color:black;">((\[img\])(?!.*\2))+</code>将6这个匹配重复1到多次，因为这里只能匹配最多三个字符，再多一个字符就会重复，所以次数是1-3

拆解到这里，可以概括一下就是，从字符串开头开始匹配每一个字符，匹配都需要进行5的断言，也就是不能出现和当前匹配的字符重复。
更直白一点的说就是： **每一个字符都不重复出现，至于这个字符就是字符集里面的任意一个。**
所以这个要是进行四个字符扩展，加个e, 那么正则就可以写成 /^((\[imge\])(?!.*\2))+$/

