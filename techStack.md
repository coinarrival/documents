# Technology Stack

- Other Language Translations

  [中文](./translate/techStack.md)

## Front-End

**Web Single Page Application**, based on following technology tools:

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

- *Vue* for building the application
- *Element-UI* for  the application style
- *webpack* for packing the application
- *mocha/chai/supertest* for unit test
- *axios* for web request

## Server-End

Serving **router management, authorization control** and **data dispatch**.

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

- *koa* builds the server-end application
- *koa-router* helps router management
- *koa-session/koa-token* helps authorization control and the final choice based the further design.
- *axios* helps retrieve data from back-end

## Back-End

Providing **data service**. Following are the candidate framework and database.

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

- *django/flask* builds the back-end application and the final choice based the further design.
- *SQLite/Mongodb/MySQL* for the database and the final choice based the further design.