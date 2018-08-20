# TypeScript语言入门

## 语言后盾

 - 微软开发
 - JavaScript的超集
 - 新的遵循ES6的语法
 - Angular2是由Google开发的前端框架，基于TypeScript语言

## 课程介绍

### 课程内容介绍

 - TS的好处
 - 安装TS开发环境
 - TS的概念语法和特性介绍

### 前置知识

 - 理解ES5,ES6,JS,TS的概念和关系
 - 基础JS的开发

### TS优势

 - 支持ES6规范，前端脚本JS未来
 - 强大的IDE支持
    - 类型检查 （减小出错率）
    - 代码提示 （提高开发效率）
    - 自动搜索同步变量更名
    - Angular2的开发语言

## 搭建TS的开发环境
安装TS的compile

 - 什么是compiler? 为什么需要compiler?
    - 浏览器支持ES5语法，TS是ES6语法，需要compiler编译
 - 使用线上compiler开发
 - 搭建本地compiler
    - 安装TS的compiler    `npm i -g typescript`
    - 编译一个ts文件， `tsc Hello.ts   // > Hello.js // Hello.js 默认被添加严格模式声明` 
    - TS默认使用严格模式
    - IDE（webstorm）中自动化编译，只需要写TS

## 语言特性

###  字符串特性
 - 多行字符串 撇号包裹
 - 字符串模板 `${var}`
 - 自动拆分字符串 字符串模板调用   
```
function test(template, name) {console.log(template, name)}
test I'm ${name}.
```
### 参数特性
 - 指定类型 `var name: string = "lili"` 这个会被支持TS的IDT指示检查
 - 类型推断 `var alias: string = "123" alias = 123 // 会指示错误可使用any类型 `
 - void 指定函数返回值类型
 - 函数参数指定类型
 - 默认参数 等号指定默认值，带默认值的参数一定要声明在必选参数后面
 - 可选参数 参数名后面加？，可选参数也得声明在必选参数后面
 - 扩展运算符  
    - 形参位置，代表不定个数参数
    - 实参位置，数组展开
### 函数新特性
 - generator函数
    - yeild关键字
    - next调用
 - 扩展运算符在函数中的应用
    - 形参位置，不定参数
    - 实参位置，展开参数
 - 析构表达式在函数中的应用
    - 形参位置
    - 实参位置

### 箭头函数
 - 避免this的诡异现象

### for of 循环语句
 - 遍历数组，遍历数集等均可获得正确的理解

### 面向对象特性
 - 类
    - class 声明
    - extends 继承
    - 修饰符
        - public 大家都可以访问
        - private 只有自己可以访问
        - protected 自己和子类可以访问
- 泛型
    - 允许类型作为参数
- 接口
    - Interface 关键字声明
    - 实现接口用 implements 关键字
- 模块
    - export 导出模块
    - import 导入模块
- 注解
    - 供框架或者工具使用
    - @Component(option)类似形式
- 类型定义文件 .d.ts文件

## 总结
了解到TS中的基本语法，以及一些oop特性。