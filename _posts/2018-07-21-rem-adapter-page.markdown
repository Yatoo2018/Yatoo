## REM适配的深入思考

### 设定几个别名如下，方便写公式:  
该设计稿的px宽度值:           psdWidth(px)  
当前窗口的px宽度值:           clientWidth(px)

我们希望设计出一个大小的设计稿，程序可以适配所有机型，也就是说 psdWidth(px)值要对应到设备的clientWidth(px)的值。

### 要做到上述有好几种思路：
1. 使用mate标签的缩放属性设置缩放比例
```jade
 meta(name="viewport" content="width=device-width,initial-scale=1.0,minimum-scale=1.0,maximum-scale=1.0,user-scalable=no")
 // 改变这个initial-scale的值
```
2. 使用transform:scaleX(clientWidth/psdWidth)
3. 使用rem单位

### 使用REM单位
这里，我们先看第3种方案，那我们就看看rem是如何做的？

我们知道rem这个单位是基于html标签fontSize属性的大小来换算元素的尺寸。
根据这个机理，可以知道我们需要一个根据窗口大小变化的fontSize值。

“为了保证我们写一份数据rem值在不同宽度屏幕下都适配”


整理上述要求，可以得到：  
需求：根据客户端窗口大小动态更新html的fontSize值，以保证元素适应  
目的: 动态fontSize值的计算规则

根据rem的机理，我们可以得到这样一个公式
```
1rem = rate * 1px（一）   
```
得到rem和px单位之间的换算关系, rate是一个换算系数，无单位，其值取html的fontSize的大小.
值得一提的是，浏览器默认html的大小通常为16px, 这时候 ```rate = 16```

### 确定rate和clientWidth的关系
客户端宽度为clientWidth时，rate和clientWidth的关系是怎样的呢？我们需要通过现在已知的条件和要求，找出这俩者之间的关系，那这些条件和要求（潜在的，或者明确的）我们就需关注一下，到底哪些条件约束着他们的关系，为了避免过于空洞，我们从一个特定的元素切入，寻找这个特定元素的rate的计算规则，并将计算方法的各个变化因素都尽量的消除，仅仅剩下clientWidth或者已知的几个变化。
#### 找出特定元素上rate的计算方法
我们取一个该设计稿中一个元素A为例, 以A元素的width属性为例：

根据公式（一）就可以得到视口宽度和设计稿宽度相等的情况下，元素width的rem数值 
```
width / rate = A元素宽度的rem值
```
这个元素在改变视口后的另一个视口下的rem值  width2 / rate2 和上述计算结果应该是相等的， 那么
```
width / rate = width2 / rate2 = 固定的rem值
```

由于在设计稿宽度的情况下，元素的px大小可以量出，我们只需要设定一个rate值就可以写出元素对应的rem宽度值，为了偷懒去量一个元素，现在我们取这个元素为舞台元素，宽度为设计稿宽度 1920px 根字体大小为16px，那么我们就可以得到舞台的固定的rem值
```
1920px / 16 = width2 / rate2 = 固定的rem值
```
改变视口大小，同步舞台大小也必须跟着同步一致变化，那么就可以得到
```
rate2 = width2 / (1920px / 16) = 16 * width2 / 1920
```
上述公式适用舞台元素同样也适用设计稿内的其他元素，因为固定的rem值是全局固定的，那么我们就可以写成通用换算rate的公式

```
rate = baseFontSize * clientWidth / psdWidth
```
这个基准值baseFontSize可以设置任何合适的值，但是为了方便获取这个rem值，也就是这个值 psdWidth / baseFontSize，当然是越好换算越好。
这样我们给html设置 
```
document.documentElement.style.fontSize 
= rate + 'px' 
= baseFontSize * clientWidth / psdWidth + 'px'
```
就可以适配全屏幕。