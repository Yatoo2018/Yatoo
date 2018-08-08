---
layout: post
title:  "前端工程化的一些术语和对应的工具"
---
# 前端工程名词
认识一下前端工程化过程可能会涉及到的一些名词，这些术语对应的工具。

## 构建工具

### Gulp

> Automate and enhance your workflow
>
> 自动化和提升你的工作流
>
> gulp is a toolkit for automating painful or time-consuming tasks in your development workflow, so you can stop messing around and build something.

### Grunt

> The JavaScript Task Runner
>
> 一个JS任务运行器
>
> In one word: automation. The less work you have to do when performing repetitive tasks like minification, compilation, unit testing, linting, etc, the easier your job becomes.

### FIS

> FIS3 是面向前端的工程构建工具。
>
> 解决前端工程中性能优化、资源加载（异步、同步、按需、预加载、依赖管理、合并、内嵌）、模块化开发、自动化工具、开发规范、代码部署等问题。

## 脚手架

### Yeoman

> Yeoman helps you to kickstart new projects, prescribing best practices and tools to help you stay productive.
>
> Yeoman 帮助你启动生成一个最佳实践部分，有助于你关注产品本身的工具的新的项目。
>
> To do so, we provide a generator ecosystem. A generator is basically a plugin that can be run with the \`yo\` command to scaffold complete projects or useful parts.
>
> Through our official Generators, we promote the "Yeoman workflow". This workflow is a robust and opinionated client-side stack, comprising tools and frameworks that can help developers quickly build beautiful web applications. We take care of providing everything needed to get started without any of the normal headaches associated with a manual setup.
>
> With a modular architecture that can scale out of the box, we leverage the success and lessons learned from several open-source communities to ensure the stack developers use is as intelligent as possible.
>
> As firm believers in good documentation and well thought out build processes, Yeoman includes support for linting, testing, minification and much more, so developers can focus on solutions rather than worrying about the little things.

### Vue-cli

> Vue CLI 是一个基于 Vue.js 进行快速开发的完整系统，提供：
> - 通过 @vue/cli 搭建交互式的项目脚手架。
> - 通过 @vue/cli + @vue/cli-service-global 快速开始零配置原型开发。
> - 一个运行时依赖 (@vue/cli-service)，该依赖：
>   - 可升级；
>   - 基于 webpack 构建，并带有合理的默认配置；
>   - 可以通过项目内的配置文件进行配置；
>   - 可以通过插件进行扩展。
> - 一个丰富的官方插件集合，集成了前端生态中最好的工具。
> - 一套完全图形化的创建和管理 Vue.js 项目的用户界面。


### 打包工具

## Webpack

> At its core, webpack is a static module bundler for modern JavaScript applications. When webpack processes your application, it internally builds a dependency graph which maps every module your project needs and generates one or more bundles.

> 一个现代JavaScript应用的静态模块打包器。打包过程会生成模块之间的依赖表。

__loader__:  打包依赖于loader.
__plugin__:  webpack也提供了插件系统，通过插件系统，你可以在模块打包之后进行进一步处理，比如代码检查，代码压缩等进行一些自动化构建工作。

### Browserify

> Browserify lets you require('modules') in the browser by bundling up all of your dependencies.

> browserify is a tool for compiling node-flavored commonjs modules for the browser.

> 一个用于为浏览器编译node风格模块的工具

> You can use browserify to organize your code and use third-party libraries even if you don't use node itself in any other capacity except for bundling and installing packages with npm.

> The module system that browserify uses is the same as node, so packages published to npm that were originally intended for use in node but not browsers will work just fine in the browser too.

> Increasingly, people are publishing modules to npm which are intentionally designed to work in both node and in the browser using browserify and many packages on npm are intended for use in just the browser. npm is for all javascript, front or backend alike.

### rollup.js

> Rollup is a module bundler for JavaScript which compiles small pieces of code into something larger and more complex, such as a library or application. It uses the new standardized format for code modules included in the ES6 revision of JavaScript, instead of previous idiosyncratic solutions such as CommonJS and AMD. ES6 modules let you freely and seamlessly combine the most useful individual functions from your favorite libraries. This will eventually be possible natively, but Rollup lets you do it today.

## 包管理器

### NPM

> Build amazing things
>
> 构建神奇的事情
>
> npm is the package manager for JavaScript and the world’s largest software registry. Discover packages of reusable code — and assemble them in powerful new ways.

### Yarn

> FAST, RELIABLE, AND SECURE DEPENDENCY MANAGEMENT.
> 快速、可靠、安全的依赖管理。
> Yarn is a package manager for your code. It allows you to use and share code with other developers from around the world. Yarn does this quickly, securely, and reliably so you don’t ever have to worry.
>
> Yarn allows you to use other developers’ solutions to different problems, making it easier for you to develop your software. If you have problems, you can report issues or contribute back, and when the problem is fixed, you can use Yarn to keep it all up to date.
>
> Code is shared through something called a package (sometimes referred to as a module). A package contains all the code being shared as well as a package.json file which describes the package.

### Bower

> A package manager for the web
>
> 一个web模块管理器
>
> Web sites are made of lots of things — frameworks, libraries, assets, and utilities. Bower manages all these things for you.



