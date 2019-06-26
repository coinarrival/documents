# 软件设计文档

|版本|日期|描述|作者|
|-|-|-|-|
|v0.1|2019年6月14日|初稿|BroImBro|
|v0.2|2019年6月25日|模板设计|快乐舔狗|
|v0.3|2019年6月26日|补充前端部分|Cynthia|

> 声明：  
> **小组原创**：本项目(coinarrival)中全部仓库代码与文档为小组成员原创。  
> **使用项目**：本项目(coinarrival)同时作为**系统分析与设计**课程小组项目，项目中的所有小组成员均未改变。


# 软件整体架构

![SoftwareStructure](../../assets/design/softwareStructure.png)

前端、服务端、后端分离，前端和服务端，服务端和后端之间采用RESTful API 完成交互。

其他详见 [软件架构](https://github.com/coinarrival/documents/blob/master/docs/design/softwareStructure.md)，[服务端API设计](https://github.com/coinarrival/documents/blob/master/docs/design/serverendAPI.md)，[后端API设计](https://github.com/coinarrival/documents/blob/master/docs/design/backendAPI.md)

# 前端

## 技术选型及理由

前端整体技术栈为：
Vue + Element-UI + webpack + axios

+ Vue：一套用于构建用户界面的渐进式框架，作为前端应用框架
+ Element-UI： 基于Vue的组件库，作为样式框架
+ webpack： 用于项目打包
+ axios：异步请求工具库

Vue：

+ 简洁的API和相对完整的文档对于开发者较友好
+ 轻量级且性能好
+ 数据驱动视图自动更新，可以让开发者更关注数据与逻辑，易于上手使用

Element-UI：

+ 风格简洁美观，免去了繁杂的美工设计工作
+ 可按需加载，只写入需要的样式即可，方便易用

webpack:

+ 可以将模块按照依赖和规则打包成符合生产环境部署的前端资源,实现项目的自动构建

axios:

+ 基于promise的工具库，处理异步请求部分的代码可读性较强
+ 轻量、高效、易用

## 架构设计

前端部分的主要文件结构：

```txt
├── index.html        // 主界面页面
├── package.json      // 记录项目依赖等配置信息
├── webpack.config.js // webpack打包的配置文件
├── src
    ├── App.vue
    ├── main.js
    ├── assets  // 存放所需的图标等静态资源
        ├── js
            ├── config.js
            ├── cookie.js // 用户登陆cookie的存取操作
        ... // 其他静态资源
    ├── router
        ├── index.js  // 页面跳转路由
    ├── views
        ├── home
            ├── home.vue // 
        ├── login
	        ├── login.vue // 登陆及注册页面
	    ├── main
	        ├── main.vue               // 包含下面五个页面作为组件，处理页面切换
	        ├── SurveyPublication.vue  // 发布问卷页面
	        ├── TaskList.vue           // 任务总览页面
	        ├── TaskPublication.vue    // 发布任务页面
	        ├── UserInfo.vue           // 用户信息页面
	        ├── UserWallet.vue         // 用户钱包页面
	        ├── TaskManager            
	            ├── TaskManager.vue        // 包含下面两个页面作为组件，处理页面切换
	            ├── TaskManagerAccept.vue  // 已接受的任务管理页面
	            ├── TaskManagerCreated.vue // 已发布的任务管理页面

```

## 模块划分

前端主要分为以下几个部分：

+ login：用户登陆及注册页面
+ TaskManager：任务管理页面（包含已接受任务的管理和以发布任务的管理页面）
+ main：主页面（包含任务总览，任务发布，问卷发布，用户钱包，用户信息五个页面）
+ router 控制页面间的跳转
+ assests 中存放前端的静态资源，其中的js文件夹下存放共用的工具函数

## 软件设计技术

### MVVM
![MVVM](../../assets/design/MVVM.PNG)

Vue是基于MVVM架构的，因此前端部分可以应用了MVVM的设计，通过双向数据绑定使 View 和 Model 自动同步，不需要手动更新DOM，简化了开发者的工作。

### 模块化、组件化的构建方式
前端中多个页面之间采用组件化方式构建，将其他页面作为组件整合在一个主页面中，可以通过 tab 方便地切换组件页面。

# 服务端

## 技术选型及理由

服务端整体技术栈为：
Koa2 + axios

+ Koa2：轻量级 Web 开发框架，作为服务端框架
+ koa-router： 中间件负责路由管理
+ koa-token： 负责用户鉴权
+ axios： 负责从后端请求和发送数据

koa2：

+ 轻量、易于扩展

axios：



## 架构设计

服务端部分的主要文件结构：

```txt

```

## 模块划分


## 软件设计技术

**TODO**: 给出具体设计在源代码中出现的位置，指明对应模块和代码

# 后端

## 技术选型及理由

后端整体技术栈为：

Django + MySQL + Docker

+ Django： 作为后端应用框架
+ MySQL： 作为数据库框架
+ Docker: 分布式部署

Django：

MySQL:

Docker:


## 架构设计

后端部分的主要文件结构：

```txt

```

## 模块划分


## 软件设计技术

**TODO**: 给出具体设计在源代码中出现的位置，指明对应模块和代码