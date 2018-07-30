## 你所了解的浏览器引擎的几个概念

### 浏览器引擎[参见wiki](https://en.wikipedia.org/wiki/Browser_engine) 

A browser engine is a core software component of every major web browser. The primary job of a browser engine is to transform HTML documents and other resources of a web page into an interactive visual representation on a user's device.  

浏览器引擎是每个主要Web浏览器的核心软件组件.浏览器引擎的主要任务是将HTML文档和网页的其他资源转换成用户设备上的交互式视觉表示。

#### 布局引擎和渲染引擎 （layout engine and rendering engine）

Besides "browser engine", two other terms are in common use regarding related concepts: layout engine and rendering engine. In theory, layout and rendering (or "painting") could be handled by separate engines. In practice, however, they are tightly coupled and rarely considered separately.

除了“浏览器引擎”之外，还有两个术语用于相关概念：布局引擎和渲染引擎。理论上，布局和渲染（或“绘画”）可以由单独的引擎来处理。然而，在实践中，它们紧密耦合，很少单独考虑。

#### 安全策略和DOM数据结构 （security policy and DOM data structure）

in addition to layout and rendering, browser engines enforce the security policy between documents and implement the Document Object Model (DOM) data structure exposed to page scripts. They also handle hyperlinks and web forms.

除了布局和渲染之外，浏览器引擎还强制执行文档之间的安全策略，并实现暴露于页面脚本的文档对象模型（DOM）数据结构。他们还处理超链接和Web表单。

#### JavaScript脚本引擎 （javascript engine）

Executing JavaScript (JS) code is a separate matter, however, as every major web browser uses a dedicated engine for this. The JS language was originally created for use in browsers, but it is now used elsewhere too, so the implementation of JS engines is decoupled from browser engines. In a web browser, the two engines work in concert via the shared DOM data structure.

然而，执行JavaScript（JS）代码是一个独立的问题，因为每个主要的Web浏览器都使用专用引擎。JS语言最初是在浏览器中创建的，但现在也在别处使用，所以JS引擎的实现与浏览器引擎脱钩。在Web浏览器中，两个引擎通过共享DOM数据结构协同工作。

#### 浏览器引擎不仅仅用于浏览器

Browser engines may be used in other types of programs besides web browsers (just as different types of cars can be manufactured with the same engine). For example, an email client may need one to display HTML email. The Electron framework, which is powered by the two engines of the Google Chrome browser, has been used to create many applications.

浏览器引擎可以用于除了浏览器之外的其他类型的程序（就像不同类型的汽车可以用同一个引擎制造）一样。例如，电子邮件客户端可能需要一个来显示HTML电子邮件。由谷歌浏览器浏览器的两个引擎供电的电子框架已经被用来创建许多应用程序。
[了解更多,请阅读 How browsers work](http://taligarsiel.com/Projects/howbrowserswork1.htm)

### 主要的浏览引擎(Notable engines)

Because the Web platform is an open standard, there are multiple browser engine implementations.
因为Web平台是开放的标准，所以有多个浏览器引擎实现。

#### [Trident（中文:三叉戟？）](https://en.wikipedia.org/wiki/Trident_(software))
Trident (also known as MSHTML) is a proprietary browser engine for the Microsoft Windows version of Internet Explorer, developed by Microsoft.

It was first introduced with the release of Internet Explorer version 4.0 in October 1997; it has been steadily upgraded and remains in use today. For versions 7 and 8 of Internet Explorer, Microsoft made significant changes to the Trident layout engine to improve compliance with web standards and add support for new technologies.

它最初是在1997年10月发布的Internet Explorer版本4中推出的，它已经稳步升级并在今天仍在使用。对于Internet Explorer的版本7和8，微软对三叉戟布局引擎进行了重大更改，以提高与Web标准的一致性并增加对新技术的支持。

In the Microsoft Edge browser, Trident is superseded by its fork, EdgeHTML.

在Edge浏览器中，Trident被他的fork项目EdgeHTML所取代。

#### [EdgeHTML](https://en.wikipedia.org/wiki/EdgeHTML)

EdgeHTML is a proprietary browser engine developed by Microsoft for the Microsoft Edge web browser. It is a fork of Trident that has removed all legacy code of older versions of Internet Explorer and rewritten the majority of its source code with web standards and interoperability with other modern browsers in mind.[2] The rendering engine was first released as an experimental option in Internet Explorer 11 as part of the Windows 10 Technical Preview build 9879.

EdgeHTML是微软为微软Edge网页浏览器开发的专有浏览器引擎。它是一个三叉戟的分支，它删除了旧版本的Internet Explorer的所有遗留代码，并用Web标准和与其他现代浏览器的互操作性重写了它的大部分源代码。首次将渲染引擎发布为Internet Explorer 11上的实验选项作为Windows 10技术预览构建9879的一部分。

#### [Gecko (中文： 壁虎？)](https://en.wikipedia.org/wiki/Gecko_(software))

Gecko is a browser engine developed by Mozilla. It is used in the Firefox browser, the Thunderbird email client, and many other projects.

Gecko是Mozilla开发的浏览器引擎。它在Firefox浏览器、雷鸟电子邮件客户端和许多其他项目中使用。

#### [WebKit](https://en.wikipedia.org/wiki/WebKit)

WebKit is the browser engine that powers Safari and was the engine originally used in Google Chrome. WebKit began as an Apple-initiated fork of the KHTML engine, which was created by KDE for its Konqueror browser. Google later forked WebKit into the Blink engine, which is now developed independently from WebKit.

WebKit是为Safari提供动力的浏览器引擎，是谷歌浏览器最初使用的引擎。WebKit最初是一个苹果启动的KHTML engine分支，KHTML engine是由KDE为Konqueror浏览器创建的。谷歌后来fork了WebKit转为Blink引擎，它现在是独立于WebKit开发的。

#### [Blink](https://en.wikipedia.org/wiki/Blink_(web_engine))

Blink is a browser engine used in the Google Chrome browser and many other projects. It is developed as part of the Chromium project[2] with contributions from Google, Opera Software ASA, Adobe Systems, Intel, Samsung and others.[3][4] It was first announced in April 2013.

Blink是谷歌浏览器浏览器和许多其他项目中使用的浏览器引擎。它是chromium项目的一部分，由谷歌、Opera软件ASA、Adobe系统、英特尔、三星等公司的贡献。在2013年4月首次宣布。

Blink is a fork of the WebCore component of WebKit[6], which is originally a fork of the KHTML and KJS libraries from KDE[7][8]. It is used in Chrome starting at version 28,[9][10] Opera (15+),[9] Vivaldi, Amazon Silk and other Chromium-based browsers and frameworks.

Blink是WebKit的WebCore组件的分支，它最初是KDE中的KHTML和KJS库的分支。它用于chrome在版本28，Opera（15 +）， Vivaldi，Amazon Silk和其他基于chromium的浏览器和框架。


#### [各个引擎对比表](https://en.wikipedia.org/wiki/Comparison_of_browser_engines)

|Engine	| Status|	Steward|	Embedded in|
| --- | --- | --- | --- |
|WebKit	| Active|	Apple|		Safari browser, Adobe AIR apps, and other browsers like Maxthon|
|Blink	| Active|	Google|		Google Chrome and Chromium, plus many other browsers including Opera and Vivaldi|
|KHTML	| Discontinued|		Konqueror| browser|
|Goanna	| Active|	M.C. Straver| Pale Moon and Basilisk browsers|
|EdgeHTML	| Active|		Proprietary|	Microsoft Edge browser and Universal Windows Platform apps|
|Trident	| Discontinued|	Microsoft|	Proprietary	Internet Explorer browser and Microsoft Outlook email client|
|Gecko	| Active|	Mozilla|		Firefox browser and Thunderbird email client, plus forks like SeaMonkey and Waterfox|
|Servo	| Active|	Mozilla|		experimental browser|


#### 浏览器Timeline
![浏览器timeline](../../../assert/imgs/engines_timeline.png)


### 浏览器 [参见wiki](https://en.wikipedia.org/wiki/Web_browser)
### 常见的浏览器
1. Google Chrome(简称:Chrome)
2. Safari
3. Mozilla Firefox(中文:火狐)
4. Internet explorer(简称:IE)
5. Edge

### javascript engine [参见wiki](https://en.wikipedia.org/wiki/JavaScript_engine)
javascript engine 用于解析和运行javascript代码。
主要的javascript的脚本解析引擎
1. Rhino, managed by the Mozilla Foundation, open source, developed entirely in Java
2. SpiderMonkey, the first JavaScript engine, which powered Netscape Navigator and today powers Firefox
3. V8 - open source, developed by Google in Denmark, part of Google Chrome and Node.js
4. JavaScriptCore - open source, marketed as Nitro and developed by Apple for Safari
5. KJS - KDE's ECMAScript/JavaScript engine originally developed by Harri Porten for the KDE project's Konqueror web browser
6. Chakra (JScript9), for Internet Explorer[17][18]
7. Chakra (JavaScript) for Microsoft Edge
8. Nashorn, open source as part of OpenJDK, written by Oracle Java Languages and Tool Group[19]
9. Duktape, an embeddable engine with focus on portability and a compact footprint
10. Juce, a C++ application framework, contains a custom embedded interpreter using part of JavaScript's syntax.
11. JerryScript, is an ultra-lightweight JavaScript engine for the Internet of Things.
12. Jsish, a JavaScript engine with type-checking modelled after Tcl.
13. Esper, a JavaScript self-interpreter with a focus on sandboxed execution and runtime introspection

#### [Rhino](https://en.wikipedia.org/wiki/Rhino_(JavaScript_engine))

Rhino is a JavaScript engine written fully in Java and managed by the Mozilla Foundation as open source software. It is separate from the SpiderMonkey engine, which is also developed by Mozilla, but written in C++ and used in Mozilla Firefox.

Rhino 是一个完全用Java编写的JavaScript引擎，由Mozilla基金会作为开源软件管理。它与SpiderMonkey引擎是分开的，它也是由Mozilla开发的，但是用C++编写，用于Mozilla Firefox。

#### [SpiderMonkey](https://en.wikipedia.org/wiki/SpiderMonkey)

SpiderMonkey is the code name for the first JavaScript engine, written by Brendan Eich at Netscape Communications, later released as open source and currently maintained by the Mozilla Foundation. SpiderMonkey provides JavaScript support for Mozilla Firefox and various embeddings such as the GNOME 3 desktop.

SpiderMonkey是第一个JavaScript引擎的代码名，由Netscape Communications的布兰登·艾奇编写，后来发布为开源，目前由Mozilla基金会维护。SpiderMonkey为Mozilla Firefox提供了JavaScript支持，以及Gnome 3桌面等各种嵌入。

#### [chrome V8 JavaScript Engine](https://en.wikipedia.org/wiki/Chrome_V8)

V8 is Google's open source JavaScript engine.
V8 implements ECMAScript as specified in ECMA-262.
V8 is written in C++ and is used in Google Chrome, the open source browser from Google.
V8 can run standalone, or can be embedded into any C++ application.[from V8 Project page](https://github.com/v8/v8/wiki)

V8是谷歌开源的JavaScript脚本语言解析引擎。
V8实现了ECMA-262中对ECMAScript的语法约定。
V8是用C++语言写的，被用于Google Chrome, 谷歌开源的浏览器。
V8可以单独运行，也可以嵌入到任何C++的应用中。

Chrome V8, or simply V8, is an open-source JavaScript engine developed by The Chromium Project for Google Chrome and Chromium web browsers.[5] The project’s creator is Lars Bak.[6] The first version of the V8 engine was released at the same time as the first version of Chrome: September 2, 2008. It has also been used in Couchbase, MongoDB and Node.js that are used server-side. [from Wiki](https://en.wikipedia.org/wiki/Chrome_V8)

Chrome V8，或者简称V8，是一个开源的JavaScript引擎，由chrome浏览器和Chromium浏览器的chromium项目开发。项目的创建者是Lars Bak.V8引擎的第一个版本同时发布为Chrome的第一个版本：2008年9月2日。在Couchbase、MangoDB和Node.js(node中被用于服务器端)。


#### [JavaScriptCore](https://en.wikipedia.org/wiki/WebKit#JavaScriptCore)

JavaScriptCore is a framework that provides a JavaScript engine for WebKit implementations, and provides this type of scripting in other contexts within macOS.[14][68] JavaScriptCore is originally derived from KDE's JavaScript engine (KJS) library (which is part of the KDE project) and the PCRE regular expression library. Since forking from KJS and PCRE, JavaScriptCore has been improved with many new features and greatly improved performance.[69]

JavaScriptCore是一个为WebKit实现提供JavaScript引擎的框架，并在MACOS的其他上下文中提供这种脚本。JavaScript核心最初源于KDE的JavaScript引擎（KJS）库（KDE项目的一部分）和PCRE 正则表达式库。自从KJS和PCRE分叉以来，JavaScript核心得到了改进，具有许多新的特性和极大的改进性能。

On June 2, 2008, the WebKit project announced they rewrote JavaScriptCore as "SquirrelFish", a bytecode interpreter.[31][32] The project evolved into SquirrelFish Extreme (abbreviated SFX, marketed as Nitro), announced on September 18, 2008, which compiles JavaScript into native machine code, eliminating the need for a bytecode interpreter and thus speeding JavaScript execution.[33]

2008年6月2日，WebKit项目宣布他们将JavaCcriptCore改写为“SquirrelFish”，一个字节码解释器。该项目演变为SquirrelFish Extreme（缩写为SFX，销售为Nitro），2008年9月18日宣布，将JavaScript编译成本机代码，不在需要字节码解释器，从而加快JavaScript执行。

#### [KJS](https://en.wikipedia.org/wiki/KJS_(software))

KJS is KDE's ECMAScript-JavaScript engine that was originally developed for the KDE project's Konqueror web browser by Harri Porten in 2000.

On June 13, 2002, Maciej Stachowiak announced on a mailing list that Apple was releasing JavaScriptCore, a framework for Mac OS X that was based on KJS.[3] Through the WebKit project, JavaScriptCore has since evolved into SquirrelFish Extreme, a JavaScript engine that compiles JavaScript into native machine code.

KJS是KDE的ECMAScript JavaScript引擎，最初是在2000由KDE项目KONQOROR Web浏览器开发的。
2002年6月13日，Maciej Stachowiak在邮件列表中宣布苹果正在发布一个基于KJS的Mac OS X的框架JavaScriptCore。JavaScriptCore已经演变成SquirrelFish Extreme，一个JavaScript引擎，将JavaScript编译成原生机器代码。

#### [Chakra(JScript engine)](https://en.wikipedia.org/wiki/Chakra_(JScript_engine))

Chakra is a JScript engine developed by Microsoft for its 32-bit version of the Internet Explorer 9 (IE9) web browser.

The JScript engine is developed as closed source proprietary software. Microsoft has developed a different JavaScript engine based on the JScript, for the newer Microsoft Edge browser (also called Chakra). The Chakra JavaScript engine has been open-sourced under the MIT license

Chakra是一个JScript引擎，由微软开发的32位版本的Internet Explorer 9（IE9）Web浏览器。
JScript引擎被开发为封闭源专有软件。微软已经开发了一种基于JScript的不同JavaScript引擎，用于更新微软边缘浏览器（也称为查克拉）。Chakra JavaScript引擎是在MIT许可下开放的。

#### [Chakra(JavaScript_engine)](https://en.wikipedia.org/wiki/Chakra_(JavaScript_engine)) 

Chakra is a JavaScript engine developed by Microsoft for its Microsoft Edge web browser. It is a fork of the JScript engine used in Internet Explorer. Like the Edge layout engine and unlike previous versions in Internet Explorer the declared intention is that it will reflect the "Living Web".[1] On December 5 of 2015, it was announced that core components of Chakra will be open-sourced as ChakraCore.

Chakra是微软开发的微软edge浏览器的JavaScript引擎。它是在Internet Explorer中使用的JScript引擎的一个分支。与edge布局引擎不同，与Internet Explorer中的以前版本不同，声明的意图是它将反映“living Web”。 在2015 12月5日，宣布Chakra的核心组件将作为ChakraCore开源。

#### 其他js引擎
后面这几个没怎么听过，有兴趣的可以去翻翻。   
[Nashorn](https://en.wikipedia.org/wiki/Nashorn_(JavaScript_engine))
[duktape](http://duktape.org/)
[JUCE](https://en.wikipedia.org/wiki/JUCE)
[JerryScript](https://en.wikipedia.org/wiki/JerryScript)
[Jsish](https://en.wikipedia.org/wiki/Jsish) 
[Esper](https://en.wikipedia.org/wiki/Esper_(software))