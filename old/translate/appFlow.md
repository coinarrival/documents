# 应用请求流程

## 应用请求流程图

![appFlow](../assets/appFlowCH.png)

- **前端从服务端请求数据**
  
  前端需要提供 token/session，以便服务端进行鉴权。
  如果请求合法，服务端向后端请求数据。

- **服务端向后端请求数据**
  
  后端需要对请求进行鉴别，看是否来自于信赖方(即应用的服务端)。
  如果确认来自合法服务端，后端发回数据，服务端将数据返回前端。
