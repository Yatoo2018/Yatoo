---
layout: post
title: "层叠样式表中的层叠的含义"
---
<style>
    blockquote {
        color: #a5a5a5;
        border-left: 4px solid #e8e8e8;
        padding-left: 15px;
        font-size: 16px;
        letter-spacing: 0px;
        font-style: normal;
    }
</style>

## [CSS权重计算](https://www.w3.org/TR/CSS2/cascade.html#specificity)


> A selector's specificity is calculated as follows:  
>
>一个选择器的权重计算依据下面规则：
>
> 1. count 1 if the declaration is from is a 'style' attribute rather than a rule with a selector, 0 otherwise (= a) (In HTML, values of an element's "style" attribute are style sheet rules. These rules have no selectors, so a=1, b=0, c=0, and d=0.)
> 2. count the number of ID attributes in the selector (= b)
> 3. count the number of other attributes and pseudo-classes in the selector (= c)
> 4. count the number of element names and pseudo-elements in the selector (= d)
> 5. The specificity is based only on the form of the selector. In particular, a selector of the form "[id=p33]" is counted as an attribute selector (a=0, b=0, c=1, d=0), even if the id attribute is defined as an "ID" in the source document's DTD.
>
> Concatenating the four numbers a-b-c-d (in a number system with a large base) gives the specificity.

### 翻译解释
1. 如果声明是“style”属性而不是带有选择器的规则, 计数1，否则为计数0（= a）（在HTML中，元素的“样式”属性的值是样式表规则）。这些规则没有选择器，所以a＝1，b＝0，c＝0，d＝0。
2. 在选择器中计数ID属性的数目 （= b）
3. 在选择器中计数其他属性和伪类的数目 （= c）
4. 在选择器中计算元素名称和伪元素的数目 （= d）
5. 特异性仅基于选择器的形式。特别地，将形式“[id= p33”]的选择器作为属性选择器（a＝0，b＝0，c＝1，d＝0）计数，即使id属性被定义为源文档DTD中的“id”。

注意1: <span style="color: #a5a5a5; font-size: 14px; font-weight: normal;">*这里的 （= n） 这个代表的含义是 将统计出来的数目用 n 来表示， 那这里，在一组（一组指的是我们写的复合选择器）选择器里，a就是style属性是否存在（存在为a=1，不存在a=0），b就是id选择器的数目，c就是属性和伪类的数目，d就是元素和伪元素的数目.*</span>

注意2：<span style="color: #a5a5a5; font-size: 14px; font-weight: normal;">*通用选择器（\*），子选择器（>）和相邻同胞选择器（+）并不在这四个等级中，所以他们的权值都为0。*</span>

**将四个数字a-b-c-d（在一个有大小关系的数字系统中）连接起来给出了特殊性。**  

再解释下：
**将这四个数字连起来，并放入一个有大小关系的数字系统中，其值就代表了这条选择器的权重。**


请看下面例子:
```css
 *             {}  /* a=0 b=0 c=0 d=0 -> specificity = 0,0,0,0 */
 li            {}  /* a=0 b=0 c=0 d=1 -> specificity = 0,0,0,1 */
 li:first-line {}  /* a=0 b=0 c=0 d=2 -> specificity = 0,0,0,2 */
 ul li         {}  /* a=0 b=0 c=0 d=2 -> specificity = 0,0,0,2 */
 ul ol+li      {}  /* a=0 b=0 c=0 d=3 -> specificity = 0,0,0,3 */
 h1 + *[rel=up]{}  /* a=0 b=0 c=1 d=1 -> specificity = 0,0,1,1 */
 ul ol li.red  {}  /* a=0 b=0 c=1 d=3 -> specificity = 0,0,1,3 */
 li.red.level  {}  /* a=0 b=0 c=2 d=1 -> specificity = 0,0,2,1 */
 #x34y         {}  /* a=0 b=1 c=0 d=0 -> specificity = 0,1,0,0 */
 style=""          /* a=1 b=0 c=0 d=0 -> specificity = 1,0,0,0 */
```
有人总结，一个选择器是否被选中依赖于下面算法得出的值的大小：  
*a的权重是1000，b是100， c是10， d是1。 然后
得出  a\*1000 + b\*100 + c\*10 + d\*1 这样算出的值。*  
我们来测试下

### 权重计算

#### 一个错误的权重计算
请看如下测试：
![specificity](../../../assert/imgs/css-cascade-specificity.jpg)

**应用上述规则，\#div11 应用了11个id选择器，一个style属性background-color，按照上述计算：11 \* 100 > 1000 \* 1 应该id选择器生效，但是最后生效的样式仍然使style属性，所以这个权重系统的假设并不正确.**

#### 正确的权重计算规则
这个权重系统的判断规则应是如下：
```javascript
 // 规则1 a1-b1-c1-d1
 // 规则2 a2-b2-c2-d2
 if a1 > a2 /* 规则1生效 */ else /*规则2生效*/
 if b1 > b2 /* 规则1生效 */ else /*规则2生效*/
 if c1 > c2 /* 规则1生效 */ else /*规则2生效*/
 if d1 > d2 /* 规则1生效 */ else /*规则2生效*/
 // 这个计算规则是具有优先级的，a > b > c > d, 一旦前面的分出高低，后面规则的数量将不影响结果
```
#### important的使用影响优先级
- !important 的使用始终高于其他规则；  
- 俩条都有!important时，还是依据上述规则。  

### 参考文章
http://www.snook.ca/archives/html_and_css/understanding_c/
其中说到解决权重快速的方法是避免使用 !important , 所以你要是不想给自己找麻烦，就不要使用!important