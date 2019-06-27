# 部署文档

|版本|日期|描述|作者|
|-|-|-|-|
|v0.1|2019年6月25日|初稿|BroImBro|

### Docker support

1. 下载源码

    ```bash
    git clone https://github.com/coinarrival/coinarrival.git
    bash ./download.sh
    ```

2. 修改配置文件

    - 后台

      修改配置文件`BackEnd/BackEnd/settings.py`
      ```python
      DATABASES = {
        'default': {
          # ...
          'HOST': 'coin_arrival',  # 与 ServerEnd 下 docker-compose 中的数据库服务容器名保持一致
        }
      }
      ```

    - 服务端

      修改配置文件`ServerEnd/bin/config/config.js`

      ```javascript
      'backend': 'http://backend:8000', // 为本项目 docker-compose 中的后台服务名
      ```

3. 部署运行项目
    ```bash
    bash ./install.sh
    ```

    通过`http://localhost:3000/public/index.html`

### Manually

首先在非本仓库目录下创建一个空目录

```bash
mkdir coinarrival
```

下面在该目录下进行安装并运行 coinarrival

- 后台

  ```bash
  cd coinarrival
  # BackEnd code
  git clone https://github.com/coinarrival/BackEnd.git
  cd BackEnd
  ```

  - MySQL:5.7 数据库配置

    启动 MySQL:5.7 数据库并在其中创建项目所需数据库

    ```bash
    CREATE DATABASE coin_arrival CHARACTER SET utf8 COLLATE utf8_general_ci;
    ```

  - 修改项目配置文件

    - **数据库配置**

      你需要通过修改 `BackEnd/settings.py` 中的数据库配置来帮助项目连接你所希望的数据库

      ```python
      DATABASES = {
          'default': {
              'ENGINE': 'django.db.backends.mysql',   # 数据库引擎
              'NAME': 'coin_arrival',  # 与前一步的数据库名保持一致
              'USER': 'zhangshanfeng',     # 用户名，可以自己创建用户
              'PASSWORD': '******',  # 密码
              'HOST': '127.0.0.1',  # mysql服务所在的主机ip
              'PORT': '3306',         # mysql服务端口
          }
      }
      ```

    - **设置允许访问的 IP**

      ```python
      ALLOWED_HOSTS = ['127....']
      ```

    - 密钥（务必修改，长度为50的字符串）

      ```python
      SECRET_KEY = '****' # 通信数据加密模式所需的 ASE 加密密钥
      ```

    - 关闭调试模式

      ```python
      DEBUG = False
      ENABLE_CRYPTO = False # 设置为 True 开启通信数据加密模式
      ```

    - 使用 Django 自带服务器启动

      - 脚本启动

        ```bash
        pip install -r requirements.txt # 安装项目依赖，只需运行一次
        bash ./start.sh
        ```
        项目将运行在本地局域网的 8000 端口

      - 手动启动

        脚本默认通过 8000 端口启动，你当然可以手动启动，设置成你所希望的端口号：

        ```bash
        pip install -r requirements.txt # 安装项目依赖，只需运行一次
        cd BackEnd
        python manage.py migrate # 更新数据表
        python manage.py makemigrations # 在数据库中应用更新
        python manage.py runserver 0.0.0.0:8000 # 启动项目，端口号可自己修改
        ```

- 服务端

  ```bash
  cd coinarrival
  # ServerEnd code
  git clone https://github.com/coinarrival/ServerEnd.git
  cd ServerEnd
  ```

  - 安装依赖

    ```bash
    npm install
    ```
  
  - 修改后台服务器地址配置

    如果你的后台运行地址有变更，请更改配置文件`bin/config/config.js`

    ```javascript
    'backend': 'http://localhost:8000', // backend 为本项目的后台地址
    ```

- 前端

  ```
  # FrontEnd code
  cd coinarrival
  git clone https://github.com/coinarrival/FrontEnd.git
  cd FrontEnd
  ```

  - 部署前端代码
  
  ```bash
  npm install
  npm run build
  ```

  将生成代码拷贝到服务端
  ```bash
  mkdir ../ServerEnd/resources/public/dist
  mkdir ../ServerEnd/resources/dist
  cp index.html ../ServerEnd/resources/public/index.html
  cp -r ./dist ../ServerEnd/resources
  cp -r ./static ../ServerEnd/resources/public/static
  mv ../ServerEnd/resources/dist/*.js ../ServerEnd/resources/public/dist/*.js
  ```

- 运行项目

  ```bash
  cd coinarrival/ServerEnd
  npm start
  ```

  项目将运行在 http://localhost:3000/public/index.html
