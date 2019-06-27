# 软件架构

|版本|日期|描述|作者|
|-|-|-|-|
|v0.1|2019年6月24日|初稿|BroInBro|

![SoftwareStructure](../../assets/design/softwareStructure.png)

## 架构问题

多用户并发请求，后台数据处理缓慢

## 解决方案说明

采用分布式数据库，将数据库单点压力分担到整个集群，使得后台服务器可以快速响应
