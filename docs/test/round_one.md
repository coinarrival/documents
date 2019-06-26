# Round One

## ServerEnd & BackEnd API

### 阶段一

- GET ​/public​/* Get public assests

|Case|Pass|Error|Reason|
|:--:|:--:|:---:|:----:|
|正确图片|Y|||
|不存在文件|Y|||

- POST ​/login Verify the username and password

|Case|Pass|Error|Reason|
|:--:|:--:|:---:|:----:|
|不完整信息|Y|||
|不存在用户名|Y|||
|错误密码|Y|||
|正常登陆|Y|||

- GET ​/account_info Get user info

|Case|Pass|Error|Reason|
|:--:|:--:|:---:|:----:|
|错误信息|Y|||
|不存在用户|Y|||
|学生用户|N|后台崩溃|后台：1. 用户表没有 userID 字段 2. 注册时没有登记用户角色；服务端：只返回了用户名，邮箱，电话和头像四个字段|
|教师用户|N|同上||

- POST ​/account_info Update account info

|Case|Pass|Error|Reason|
|:--:|:--:|:---:|:----:|
|正确信息|N|之更新了邮箱，电话和头像|服务端只接受了这三个字段并且只传给了后台这三个字段|
|Waiting||||


- POST ​/avatar Upload avatar image

|Case|Pass|Error|Reason|
|:--:|:--:|:---:|:----:|
|上传头像|N|服务端错误|未开启multiparty-form解析功能|

- POST ​/registration Create an account

|Case|Pass|Error|Reason|
|:--:|:--:|:---:|:----:|
|不完整信息|Y|||
|正常信息|Y|||
|重复用户名|Y|||
|重复邮箱|Y|||
|重复电话|Y|||

- POST ​/task Create a task

|Case|Pass|Error|Reason|
|:--:|:--:|:---:|:----:|
|正常发起|N|服务端错误 + 后台错误|服务端乱用 for in 循环；后台task type 错误，应为 string|
|Waiting||||


**业务已崩溃，fix bug 后继续**

### 未测试

- GET ​/balance Query wallet balance of current user



- GET ​/task Query one task


- DELETE ​/task Complete an uncompleted task



- GET ​/tasks Get a page of available tasks



- GET ​/accepted_tasks Query a page of accepted tasks of current user



- POST ​/accepted_tasks Accept a new task.



- GET ​/created_tasks Query a page of created tasks of current user



- POST ​/created_tasks Update a task



- GET ​/acceptance Query a page of acceptance record of a specific task.



- POST ​/acceptance Finish one created task for a specific user.



- DELETE ​/acceptance One can delete its acceptance record. 
