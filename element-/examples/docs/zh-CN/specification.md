## 开发规范
1.组件化开发说明

2.命名规范

3.结构化规范

4.注释规范

5.编码规范

### **1.组件化开发说明**

#### 什么是组件？
:::tip
组件其实就是页面组成的一部分，好比是电脑中的每一个元件（如硬盘、键盘、鼠标），它是一个具有独立的逻辑和功能或界面
   
同时又能根据规定的接口规则进行相互融化，变成一个完整的应用。
   
页面只不过是这样组件的容器，组件自由组合形成功能完整的界面，当不需要某个组件，或者想要替换某个组件时
   
可以随时进行替换和删除，而不影响整个应用的运行。前端组件化的核心思想就是将一个巨大复杂的东西拆分成粒度合理的小东西。

:::
#### 组件化开发的好处
:::tip
 提高开发效率
    
 方便重复使用
    
 简化调试步骤
    
 提升整个项目的可维护性
    
 便于协同开发
    
 使其高内聚，低耦合，达到分治与复用的目的。
 :::  
#### 组件化和模块化的区别
:::tip
  组件化是从产品功能角度进行分割，模块化是从代码实现角度进行分割，模块化是组件化的前提和基础。
:::
#### Vue组件化开发
```html 
 单文件系统，样式局部作用域
    
 基本组成结构：<template/> <script/> <style scoped/>
    
 组件注册方式：1）公共组件全局注册 2）其余组件局部注册
```    
### **2.命名规范**

#### 组件命名规范，Vue官方文档给予以下说明：
:::tip
当注册组件 (或者 prop) 时，可以使用 kebab-case (短横线分隔命名)、camelCase (驼峰式命名) 或 PascalCase (单词首字母大写命名)。
PascalCase 是最通用的声明约定而 kebab-case 是最通用的使用约定。
命名可遵循以下规则：

 1、有意义的名词、简短、具有可读性
 
 2、以小写开头，采用短横线分割命名
 
 3、公共组件命名以公司名称简拼为命名空间(app-xx.vue)
 
 4、文件夹命名主要以功能模块代表命名
 
 同时还需要注意：必须符合自定义元素规范: 使用连字符分隔单词，切勿使用保留字。
 
 app- 前缀作为命名空间: 如果非常通用的话可使用一个单词来命名，这样可以方便于其它项目里复用。  
:::
#### views 命名
views 文件夹下面是由 以页面为单位的 vue 文件 或者 模块文件夹 组成的，放在 src 目录之下，与 components、assets 同级。

#### views 下的文件夹命名
:::tip
 views 下面的文件夹代表着模块的名字
    
 由名词组成（car、order、cart）
    
 单词只能有一个（good: car order cart）（bad: carInfo carpage）
    
 尽量是名词（good: car）（bad: greet good）
    
 以小写开头（good: car）（bad: Car）
:::
#### views 下的 vue 文件命名
views 下面的 vue 文件代表着页面的名字
:::tip
放在模块文件夹之下

只有一个文件的情况下不会出现文件夹，而是直接放在 views 目录下面，如 Login Home

尽量是名词

大写开头，开头的单词就是所属模块名字（CarDetail、CarEdit、CarList）

名字至少两个单词（good: CarDetail）（bad: Car）

常用结尾单词有（Detail、Edit、List、Info、Report）

以 Item 结尾的代表着组件（CarListItem、CarInfoItem）
:::

#### method 自定义方法命名
:::tip
动宾短语（good：jumpPage、openCarInfoDialog）（bad：go、nextPage、show、open、login）

ajax 方法以 get、post 开头，以 data 结尾（good：getListData、postFormData）（bad：takeData、confirmData、getList、postForm）

事件方法以 on 开头（onTypeChange、onUsernameInput）

init、refresh 单词除外

尽量使用常用单词开头（set、get、open、close、jump）

驼峰命名（good: getListData）（bad: get_list_data、getlistData）
:::
#### CSS命名规范
**使用组件名作为样式作用域空间**
:::tip
1.Vue.js 的组件是自定义元素，这非常适合用来作为样式的根作用域空间。可以将组件名作为 css 类的命名空间。

2.给样式加上作用域空间可以避免组件样式影响外部的样式

3.保持模块名、目录名、样式根作用域名一样，可以很好的将其关联起来，便于开发者理解。
:::
**使用组件名作为样式命名的前缀，基于 [BEM](https://www.jianshu.com/p/49023c3f242c)范式。
同时给style标签加上 scoped 属性。加上 scoped 属性编译后会给组件的 class 自动加上唯一的前缀从而避免样式的冲突。**
```html
<style scoped>
    /* 推荐 */
    .MyExample { }
    .MyExample li { }
    .MyExample__item { }

    /* 避免 */
    .My-Example { } /* not scoped to component or module name, not BEM compliant */
</style>
```

### **3.结构化规范**

#### 基于Vue-admin-cli脚手架的v3 websolution 项目结构
```html
    ├── build                      // 构建相关 webpack config
    │   ├── build.js                        生产环境构建脚本
    │   ├── utils.js                        构建相关工具方法
    │   ├── webpack.base.conf.js            wabpack基础配置
    │   ├── webpack.dev.conf.js             wabpack开发环境配置
    │   └── webpack.prod.conf.js            wabpack生产环境配置  
    ├── config                     // 配置相关 开发 测试 生产环境的配置
    │   ├── dev.env.js                        开发环境变量 
    │   ├── index.js                          整体参数配置 web.config.js
    │   ├── prod.env.js                       生产环境变量
    │   └── sit.env.js                        测试环境变量 
    ├── dist                       // 打包输出目录
    ├── node_modules               // 项目依赖的各种包 包含[基础控件]
    ├── src                        // 源代码
    │   ├── api                    // [前端ORM层] 
    │   │   ├── v2                            V+2.0的接口配置dataConfig.json
    │   │   ├── baseModule.js                 后端微服务和axios的适配层
    │   │   ├── BusinessService.js            业务设置服务类
    │   │   ├── DiagnosisService.js           诊断服务类
    │   │   ├── LoginService.js               登录鉴权等公用服务类
    │   │   ├── MapService.js                 地图监控服务类 
    │   │   ├── ResourceService.js            资源中心服务类
    │   │   └── TransferService.js            Transfer服务类，用于向3.0向2.0接口调用    
    │   ├── assets                 // echarts主题 字体 图片等静态资源
    │   ├── components             // [通用组件] 文件夹以大写开头
    │   ├── directive              // 全局自定义指令
    │   ├── filters                // 全局自定义filter
    │   ├── icons                  // svg icons图标和fallback png图标
    │   ├── lang                   // 国际化 
    │   ├── mock                   // 项目mock 模拟数据和拦截转发
    │   ├── router                 // [路由层] 前端静态资源池
    │   │   ├── v2                              V+2.0的路由配置
    │   │   ├── _import_development.js          加速dev hotreload时间 开发环境不使用code splite
    │   │   ├── _import_production.js           生产环境采用code splite减少打包大小和实现异步按需加载模块
    │   │   └── index.js                        路由配置    
    │   ├── store                  // [VUEX层]   状态管理机
    │   │   ├── modules                         按模块划分的store 包含选项卡 用户信息 权限等
    │   │   ├── getters.js                      store的接入层
    │   │   └── index.js                        store的初始化  
    │   ├── styles                 // 全局样式 Atom CSS 和 Critcal CSS
    │   ├── utils                  // 能够抽离出的工具类
    │   ├── views                  // [视图层]接入型组件（容器组件）
    │   │   ├── common                          公共的视图比如layout
    │   │   │   ├── layout                     不同类型的布局写在layout下，一个常规的layout通常包含header footer sidebar navbar main等
    │   │   │   ├── ...
    │   │   │   └── login                      登录页面是按解决方案定制的，是特殊的layout 
    │   │   ├── diagnosis   
    │   │   │   ├── components                 诊断模块用到的[领域通用组件]，将来可以合并同类项到[通用组件]
    │   │   │   ├── 诊断页面1...               可以是文件夹，如有子页面再建children文件夹
    │   │   │   └── 诊断页面2...               结构简单的可以是.vue文件    
    │   │   ├── mapMonitoring   
    │   │   │   ├── components                 地图监控模块用到的[领域通用组件]，将来可以合并同类项到[通用组件]
    │   │   │   ├── 地图页面1...               可以是文件夹，如有子页面再建children文件夹
    │   │   │   └── 地图页面2...               结构简单的可以是.vue文件                                   
    │   │   └── ...                             其他的各种页面视图 省略                        
    │   ├── App.vue                // 入口页面
    │   ├── errorLog.js            // 错误日志 供开发和测试使用
    │   ├── main.js                // 入口 加载组件 初始化等
    │   └── pro.loader.js          // 登陆后的预加载资源处理和权限过滤
    ├── .babelrc                    // babel-loader 配置
    ├── eslintrc.js                 // eslint 配置项
    ├── eslintignore.js             // eslint 忽略目录
    ├── .gitignore                  // git 忽略项
    ├── favicon.ico                 // favicon网站图标
    ├── gulpfile.js                 // gulp任务 用于打包网站主题
    ├── index.html                  // html模板
    └── package.json                // package.json
    └── package-lock.json           // 依赖锁定 需要 npm > 5
    
  
  ```
#### vue文件基本结构
 ```html
        <template>
          <div>
            <!--必须在div中编写页面-->
          </div>
        </template>
        <script>
          export default {
            components : {
            },
            data () {
              return {
              }
            },
            methods: {
            },
            mounted() {
        
            }
         }
        </script>
        <!--声明语言，并且添加scoped-->
        <style lang="less" scoped>
        </style>
 ```
#### vue文件方法声明顺序
:::tip
    - components   
    - props    
    - data     
    - created
    - mounted
    - activited
    - update
    - beforeRouteUpdate
    - metods   
    - filter
    - computed
    - watch
:::
### 4.注释规范

代码注释在一个项目的后期维护中显的尤为重要，所以我们要为每一个被复用的组件编写组件使用说明，为组件中每一个方法编写方法说明。
以下情况，务必添加注释
:::tip 
1.公共组件使用说明

2.各组件中重要函数或者类说明

3.复杂的业务逻辑处理说明

4.特殊情况的代码处理说明,对于代码中特殊用途的变量、存在临界值、函数中使用的hack、使用了某种算法或思路等需要进行注释描述

5.注释块必须以/**（至少两个星号）开头

6.单行注释使用//开头
:::

#### 单行注释
:::tip    
    普通方法一般使用单行注释// 来说明该方法主要作用
:::
#### 多行注释
:::tip
   组件使用说明，和调用说明 
   <!--公用组件：数据表格
      /**
      * 组件名称
      * @module 组件存放位置
      * @desc 组件描述
      * @author 组件作者
      * @date 2017年12月05日17:22:43
      * @param {Object} [title]    - 参数说明
      * @param {String} [columns] - 参数说明
      * @example 调用示例
      *  <hbTable :title="title" :columns="columns" :tableData="tableData"></hbTable>
          */
       -->
 :::
### 5.编码规范
优秀的项目源码，即使是多人开发，看代码也如出一人之手。统一的编码规范，可使代码更易于阅读，易于理解，易于维护。
尽量按照[ESLint](http://eslint.cn/)格式要求编写代码

#### 编码风格
:::tip
1.使用ES6风格编码源码

    定义变量使用let 
    
    定义常量使用const
    
    使用export ，import 模块化
2.组件 props 原子化

    提供默认值
    
    使用 type 属性校验类型
    
    使用 props 之前先检查该 prop 是否存在
    
3.避免 this.$parent

4.谨慎使用 this.$refs

5.无需将 this 赋值给 component 变量

6.调试信息console.log() debugger 使用完及时删除
:::

#### 组件单一职责
尽量对所有的组件应用对所有的组件应用[单一职责原则(SRP)](http://blog.csdn.net/hfreeman2008/article/details/52234287)
:::tip
坚持每个文件只定义一样东西

考虑把文件大小限制在 400 行代码以内
:::
#### 定义小函数
:::tip
坚持定义简单函数

考虑限制在 75 行之内。
:::