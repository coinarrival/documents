# 技术栈

## 前端

基于以下技术工具的**单页面网页应用**：

<table>
  <tbody>
    <tr>
      <td align="center" valign="middle">
        <a href="https://vuejs.org" target="_blank">
          <img width="222px" src="https://vuejs.org/images/logo.png">
        </a>
      </td>
      <td align="center" valign="middle">
        <a href="https://element.eleme.io/" target="_blank">
          <img width="222px" src="http://element-cn.eleme.io/favicon.ico">
        </a>
      </td>
      <td align="center" valign="middle">
        <a href="https://github.com/webpack/webpack" target="_blank">
          <img width="222px" src="https://www.webpackjs.com//6bc5d8cf78d442a984e70195db059b69.svg">
        </a>
      </td>
      <td align="center" valign="middle">
        <a href="https://github.com/mochajs/mocha" target="_blank">
          <img width="222px" src="https://camo.githubusercontent.com/af4bf83ab2ca125346740f9961345a24ec43b3a9/68747470733a2f2f636c6475702e636f6d2f78465646784f696f41552e737667">
        </a>
      </td>
      <td align="center" valign="middle">
        <a href="https://github.com/chaijs/chai" target="_blank">
          <img width="222px" src="https://camo.githubusercontent.com/431283cc1643d02167aac31067137897507c60fc/687474703a2f2f636861696a732e636f6d2f696d672f636861692d6c6f676f2e706e67">
        </a>
      </td>
      <td align="center" valign="middle">
        <a href="https://github.com/axios/axios" target="_blank">
          <img width="222px" src="https://i.loli.net/2019/04/06/5ca844dbe8106.png">
        </a>
      </td>
      <td align="center" valign="middle">
        <a href="https://github.com/visionmedia/supertest" target="_blank">
          <img width="222px" src="https://i.loli.net/2019/04/06/5ca84517a1b53.png">
        </a>
      </td>
    </tr>
  </tbody>
</table>

- *Vue* 作为前端应用框架
- *Element-UI* 作为样式框架
- *webpack* 打包应用
- *mocha/chai/supertest* 负责单元测试
- *axios* 负责网页中发起请求

## 服务端

负责**路由管理，用户鉴权**和**数据分发**

<table>
  <tbody>
    <tr>
      <td align="center" valign="middle">
        <a href="https://koajs.com/" target="_blank">
          <img width="58px" src="https://github.com/koajs/koa/raw/master/docs/logo.png">
        </a>
      </td>
      <td align="center" valign="middle">
        <a href="https://github.com/axios/axios" target="_blank">
          <img width="58px" src="https://i.loli.net/2019/04/06/5ca844dbe8106.png">
        </a>
      </td>
    </tr>
  </tbody>
</table>

- *koa* 作为服务端框架
- *koa-router* 中间件负责路由管理
- *koa-session/koa-token* 负责用户鉴权，最终选择依赖进一步的设计
- *axios* 负责从后端请求和发送数据

## 后端

提供**数据服务**。以下是候选框架和数据库：

<table>
  <tbody>
    <tr>
      <td align="center" valign="middle">
        <a href="https://www.djangoproject.com/" target="_blank">
          <img width="222px" src="https://avatars3.githubusercontent.com/u/27804?s=200&v=4">
        </a>
      </td>
      <td align="center" valign="middle">
        <a href="http://flask.pocoo.org/docs/1.0/" target="_blank">
          <img width="222px" src="http://flask.pocoo.org/docs/1.0/_static/flask.png">
        </a>
      </td>
      <td align="center" valign="middle">
        <a href="https://www.sqlite.org/index.html" target="_blank">
          <img width="222px" src="https://www.sqlite.org/images/sqlite370_banner.gif">
        </a>
      </td>
      <td align="center" valign="middle">
        <a href="https://www.mongodb.com/" target="_blank">
          <img width="222px" src="https://avatars1.githubusercontent.com/u/45120?s=200&v=4">
        </a>
      </td>
      <td align="center" valign="middle">
        <a href="https://www.mysql.com/" target="_blank">
          <img width="222px" src="https://i.loli.net/2019/04/06/5ca849b54cfc7.jpg">
        </a>
      </td>
    </tr>
  </tbody>
</table>

- *django/flask* 作为后端应用框架，最终选择依赖进一步的设计
- *SQLite/Mongodb/MySQL* 作为数据库框架，最终选择依赖进一步的设计