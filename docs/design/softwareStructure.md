# 软件架构

![SoftwareStructure](../../assets/design/softwareStructure.png)

## 架构问题

多用户并发请求，后台数据处理缓慢

## 解决方案说明

采用分布式数据库，将数据库单点压力分担到整个集群，使得后台服务器可以快速响应
