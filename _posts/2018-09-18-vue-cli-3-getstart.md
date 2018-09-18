# 下一代 Vue 脚手架工具 VueCLI3 上手

根据官方核心开发者的说法，vue 升级到 3，他的脚手架应该也是这个 。

## 为什么要用 3 呢，官方给了这么几个原因：

- Cannot upgrade via deps
  - vue cli 2 创建的项目，我们能升级的只有 vue, webpack 和 webapck 插件本身，而 webpack 和项目的配置文件（即 config 和 build 目录中的文件）无法通过依赖升级来改掉，而 webpack 和 vue-loader 一直在更新，其配置文件也需要随之升级，就成为一个问题
- Useless scripts checked into projects
  - 一些无用的脚本文件和资源文件，对写模板的人有用，但对使用的人来说都是无用的，所以需要去删除
- No ecosystem sharing
  - 没有一个生态系统的分享，没有插件系统，没有通用的 preset, 如果要调整需要从 templates-vuejs/ewebpack 项目 fork 自己的仓库进行更改并进行调整，但是这个与上游的同步就成为问题

## 其他 CLI 工具

- ember-cli
- angular-cli
- create-react-app // facebook 比较理想的脚手架工具

### Vue CLI的灵感来源

- poi
- neutrino mozila:webpack-chain

## 核心概念 Core Concepts

- Scaffolding, not only templating //可编程操作
- Zero Configuration // 借鉴 parcel
- Plugin-based // preset

## 安装和使用 Insatallation & Usage

```shell
yarn global @vue/cli
# yarn 被推荐，大部分vue的开发的项目都使用yarn
# 快，缓存
vue create my-project

vue ui
```

### 注意

> 这里如果是 windows 环境，如果遇到问题尝试安装 yarn 包管理工具后选择包管理工具时选择 yarn。
> yarn VS npm 的文章 http://web.jobbole.com/88459/
> 有问题可以 https://github.com/vuejs/vue-cli/issues 或者 https://forum.vuejs.org/latest
> 默认 preset 里面只带有 babel 和 eslint 插件

### 使用旧版

```shell
# 使用cli-init工具
npm install -g @vue/cli-init
vue init webpack my-project
```

## 引入 vuex, vue-router

```shell
# VueCLI3脚手架中默认是没有安装vuex和vue-router
vue add router
vue add vuex
```

## 定制化项目配置

```js
// 项目根目录下新建 vue.config.js
lintOnSave: false // 保存时检查格式，使用eslint
crossorigin: 'anonymous' // htmlWebpackPlugin
css: { // 对组件中css的配置
  modules: true
},
devServer: { // 对开发服务的设置
  // Various Dev Server settings
  host: '0.0.0.0', process.env.HOST
  port: 8080, // can be overwritten by process.env.PORT, if port is in use, a free one will be determined
  open: true, // 自动调用默认浏览器打开
  https: false // 是否使用https, https默认使用node的一个内部默认的ca证书

}
// 查看内置webpack配置需要使用 vue inspect命令
```

## 启动一个 vue 文件

```shell
vue serve template.vue
```
