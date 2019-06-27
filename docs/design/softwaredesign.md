# 软件设计文档

|版本|日期|描述|作者|
|-|-|-|-|
|v0.1|2019年6月14日|初稿|BroImBro|
|v0.2|2019年6月25日|模板设计|快乐舔狗|
|v0.3|2019年6月26日|补充前端部分|Cynthia|
|v0.4|2019年6月26日|补充服务端部分|BroInBro|
|v0.5|2019年6月27日|补充后端部分|张三丰|

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
koa2 + axios + mocha + chai + Docker

+ koa2：基于 JavaScript 的 Web 开发框架，利用生态圈内中间件开发服务端
+ koa-cors： 中间件负责处理跨域请求
+ koa-jwt： 中间件负责用户鉴权
+ jsonwebtoken： 中间件签发jwt
+ koa-body： 中间件负责解析请求数据
+ koa-router： 中间件负责路由管理
+ koa-static： 中间件负责静态资源发送
+ axios： 负责从后端请求和发送数据
+ mocha：基于 JavaScript 的测试框架
+ chai：基于 JavaScript 的断言库
+ Docker：免于环境配置困扰，快速部署运行

koa2：

+ 轻量、易于扩展
+ 生态圈中间件丰富，满足各种需求
+ 支持 ES6 语法，async 和 await 避免回调地狱

axios：

+ waiting

mocha + chai

+ 顺序执行测试，异常不中断
+ 测试报告中异常与测试样例相匹配
+ 支持异步函数测试
+ 断言语义化，测试代码可读性更高

## 架构设计

服务端部分的主要文件结构：

```txt
├─bin // 代码文件夹
│  ├─config // 项目配置文件夹
│  │  └─config.js   // 项目配置
│  ├─controllers // 路由文件夹
│  │  ├─acceptance.js
│  │  ├─accepted_tasks.js
│  │  ├─account_info.js
│  │  ├─balance.js
│  │  ├─created_tasks.js
│  │  ├─login.js
│  │  ├─registration.js
│  │  ├─task.js
│  │  └─tasks.js
│  ├─middleware // 自制中间件
│  │  ├─body.js         // 请求解析
│  │  ├─controller.js   // 路由注册
│  │  ├─login_check.js  // jwt 验证
│  │  └─static.js       // 静态资源服务
│  └─utils // 工具函数
│  │  ├─decodeToken.js      // 解析 jwt
│  │  ├─decodeUsername.js   // 解析用户名
│  │  ├─format.js           // 验证数据格式
│  │  └─logger.js           // log 函数
│  └─app.js // 项目入口文件
├─logs // 日志文件
│  ├─error      // 错误日志
│  └─response   // 请求日志
├─node_modules  // 第三方库
│  └─... modules 
├─resources // 静态资源文件夹
├─test // 测试代码文件夹
│  └─test.js // 测试代码
├─.travis.yml   // Travis CI 配置文件
├─development.js// 项目热更新入口
├─Dockerfile    // 项目 docker 镜像配置文件
├─docker-compose.yml    // 整合项目 docker 配置文件
└─package.json  // 项目描述和依赖关系
```

## 模块划分

服务端模块主要划分为：**配置模块，路由模块，中间件模块**和**工具函数模块**

![ServerEnd](../../assets/design/koa.png)

## 软件设计技术

- 流程式控制

  对于服务端接收到请求，它的处理生命周期，通过流程管理。每一个流程，处理一部分内容，到最后处理完毕，返回结果；在处理流程内出现异常，则中断处理返回错误信息。

  ![control](../../assets/design/serverControl.png)

  ```javascript
  const app = new koa();

  // cors request
  app.use(cors({
    //...
  }));

  // verification
  app.use(
    koaJwt({
      //...
    })
  );

  // body parse
  app.use(body());

  // router
  app.use(router());

  // other control

  app.listen(config.port, () => {
    defaultLogger.trace(`Server running at port:${config.port}`);
  });
  ```

  流程式控制使得一条请求的处理过程变得更加可控，从分析请求合法性，到请求解析，到处理数据，到最终返回，每一个过程只专注于该过程的工作，不必担心前序合法的校验。

- 模块分离

  将代码分模块(`config`，`controller`，`middleware`，`utils`)进行开发，不同模块处理不同工作，并且相互之间提供支持。模块分离使得代码耦合度降低，维护时可快速定位问题所在。

  ```txt
  ├─bin // 代码文件夹
  │  ├─config // 项目配置
  │  ├─controllers // 路由
  │  ├─middleware // 中间件
  │  └─utils // 工具函数
  ```

# 后端

## 技术选型及理由

后端整体技术栈为：

Django + MySQL + Docker

Django：
- 用于创建模型的对象关系映射
- 为最终用户设计的完美管理界面
- 一流的 URL 设计
- 设计者友好的模板语言
- 缓存系统


MySQL:
- 支持多线程，充分利用CPU资源
- 优化的SQL查询算法，有效地提高查询速度
- 支持大型的数据库。可以处理拥有上千万条记录的大型数据库
- 复制全局事务标识，可支持自我修复式集群
- 复制无崩溃从机，可提高可用性
- 复制多线程从机，可提高性能


## 架构设计

后端部分的主要文件结构：

```txt
├─BackEnd
│  │  Dockerfile // 项目 docker 镜像配置文件
│  │  requirements.txt // 项目依赖
│  │  start.sh // 启动脚本
│  │  
│  ├─BackEnd
│  │  │  manage.py // 管理文件
│  │  │  
│  │  ├─accept_task_info // 管理接受任务的应用
│  │  │  │  admin.py // 后台管理
│  │  │  │  apps.py
│  │  │  │  crypto.py // 加密控件
│  │  │  │  models.py // 数据模型
│  │  │  │  tests.py // 测试文件
│  │  │  │  urls.py // 路由
│  │  │  │  views.py // 交互逻辑函数
│  │  │          
│  │  ├─account_info // 管理账户信息
│  │  │  │  admin.py // 后台管理
│  │  │  │  apps.py
│  │  │  │  crypto.py // 加密控件
│  │  │  │  models.py // 数据模型
│  │  │  │  tests.py // 测试文件
│  │  │  │  urls.py // 路由
│  │  │  │  views.py // 交互逻辑函数
│  │  │          
│  │  ├─BackEnd
│  │  │  │  settings.py // 配置文件
│  │  │  │  urls.py // 路由
│  │  │  │  wsgi.py
│  │  │          
│  │  ├─task_info // 任务管理
│  │  │  │  admin.py // 后台管理
│  │  │  │  apps.py
│  │  │  │  crypto.py // 加密控件
│  │  │  │  models.py // 数据模型
│  │  │  │  tests.py // 测试文件
│  │  │  │  urls.py // 路由
│  │  │  │  views.py // 交互逻辑函数
│  │  │          
│  │  └─wallet_info // 钱包管理
│  │     │  admin.py // 后台管理
│  │     │  apps.py
│  │     │  crypto.py // 加密控件
│  │     │  models.py // 数据模型
│  │     │  tests.py // 测试文件
│  │     │  urls.py // 路由
│  │     │  views.py // 交互逻辑函数
│  │              
│  ├─currency_system
│  │  │  truffle-box.json
│  │  │  truffle-config.js // 配置文件
│  │  │  
│  │  ├─contracts
│  │  │      CoinArrivalCoin.sol // 货币合约
│  │  │      Migrations.sol
│  │  │      SafeMath.sol // 保证安全的数学函数
│  │  │      
│  │  ├─migrations
│  │  │      1_initial_migration.js
│  │  │      2_deploy_contracts.js
│  │          
│  └─design
│          model.uxf // 数据库设计文件
```

## 模块划分

后端主要分为路由模块、逻辑处理模块、模型交互模块、安全模块、后台管理模块、分布式数据库模块、区块链货币服务模块

- **路由模块** 负责将服务端不同的请求导向
- **逻辑处理模块** 负责解析服务端请求，获取和处理数据库数据
- **模型交互模块** 负责与数据库对接
- **安全模块** 以中间件的形式，为数据提供保密性、完整性的保障，且不需要修改其它代码，低耦合
- **后台管理模块** 方便后台人员以超级用户的方式修改、查看数据
- **分布式数据库模块** 采用负载均衡实现的数据库模块，鲁棒性好
- **区块链货币服务模块** 去中心化的货币服务

## 软件设计技术

后端采用MVT架构设计

![MVT](../../assets/design/MVT.PNG)

MVT是Model-View-Template的缩写

Django框架接收了用户请求和参数后，再通过正则表达式匹配URL，转发给对应视图进行处理。视图调用M处理数据，再调用T返回数据给服务端

- M表示model，负责与数据库交互
  - 对应与四个子应用的model.py，定义了数据结构，例如用户管理子应用的model
```python
class User(models.Model):
    username = models.CharField(max_length=100, unique=True)
    gender = models.CharField(max_length=30, null=True)
    email = models.CharField(max_length=50, unique=True)
    phone = models.CharField(max_length=15, unique=True)
    school = models.CharField(max_length=50, null=True)
    major = models.CharField(max_length=30, null=True)
    age = models.IntegerField(null=True)
    role = models.CharField(max_length=30, null=True)
    studentID = models.CharField(max_length=30, null=True)
    teacherID = models.CharField(max_length=30, null=True)
    grade = models.CharField(max_length=30, null=True)
    password = models.CharField(max_length=30)
    avatar = models.CharField(max_length=300, null=True)
```
- V表示view，是核心，负责接收请求、获取数据、返回结果
  - 对应于四个子应用的view.py，负责处理解析服务端的请求，执行相应的数据获取和处理，例如返回参与任务情况的部分逻辑
```python
def operate_acceptance(request):
    if request.method == 'GET':
        try:# 解析服务端请求
            page = int(decrypt(request.GET['page']))
            tusername = decrypt(request.GET['issuer'])
            ttaskID = decrypt(request.GET['taskID'])
        except:
            return dealResponse(400)
        try: # 获取数据
            fuser = User.objects.get(username=tusername)
            ttask = Task.objects.get(taskID=ttaskID)
        except(User.DoesNotExist, Task.DoesNotExist):
            return dealResponse(404)
        if fuser != ttask.issuer:
            return dealResponse(401)
        # 计算和处理数据
        result = AcceptTask.objects.filter(task=ttask)
        max_pages = math.ceil(float(len(result)) / MAX_PAGE_ITEMS)
        if page > max_pages or page <= 0:
            return dealResponse(416, {"data": {"max_pages": max_pages}})
        page = page - 1
        resp = {"data" : {
                "records" : [], 
                "max_pages" : max_pages
            }
        }
        startid = page * MAX_PAGE_ITEMS
        endid = min(len(result), (page+1)*MAX_PAGE_ITEMS)
# ...
```
- T表示template，负责将数据呈现给服务端
  - 由于格式简单，包含在四个子应用中的view.py文件，例如呈现任务列表的逻辑
```python
# 返回指定格式
for i in range(startid, endid):
    oner =  {
    "userID": result[i].user.id,
    "isFinished": result[i].isFinished, 
    "answer":result[i].answer
}
    resp['data']['records'].append(oner)
```

在安全方面，采用AES加密和消息验证码，能有效保证数据的保密性、完整性，避免信道窃听、重放攻击的实施，例如crypto.py中的AES加密

```python
def _pad(s): return s + (AES.block_size - len(s) % AES.block_size) * chr(AES.block_size - len(s) % AES.block_size) 
def _cipher():
    key = settings.SECRET_KEY
    # return AES.new(key=key, mode=AES.MODE_CBC, IV=iv)
    return AES.new(key=key[:32], mode=AES.MODE_CBC, IV=key[:16])
 
def encrypt(data):
    if settings.ENABLE_CRYPTO:
        return _cipher().encrypt(_pad(data))
    return data
    
def decrypt(data):
    if settings.ENABLE_CRYPTO:
        return _cipher().decrypt(data)
    return data
```