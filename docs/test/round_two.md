# Round Two

## ServerEnd & BackEnd API

### 阶段二

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
  |学生用户|N|信息不完整|**后台API**中没有role字段|
  |教师用户|N|同上|

- POST ​/account_info Update account info

  |Case|Pass|Error|Reason|
  |:--:|:--:|:---:|:----:|
  |正确信息|N|性别未更新|**服务端**未发送gender字段|
  |冲突信息|Y||


- POST ​/avatar Upload avatar image

  |Case|Pass|Error|Reason|
  |:--:|:--:|:---:|:----:|
  |上传头像|Y|||

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
  |正常发起|N|返回信息错误|**后台**未返回创建的任务ID|
  |信息不足|N|返回信息错误|**服务端**没有处理信息为空的清空|

- GET ​/public​/* Get public assests

  |Case|Pass|Error|Reason|
  |:--:|:--:|:---:|:----:|
  |正确图片|Y|||
  |不存在文件|Y|||

- GET ​/balance Query wallet balance of current user

  |Case|Pass|Error|Reason|
  |:--:|:--:|:---:|:----:|
  |正常查询|Y|

- GET ​/task Query one task

  |Case|Pass|Error|Reason|
  |:--:|:--:|:---:|:----:|
  |正确信息|Y|||
  |不存在任务|Y|||
  |信息不足|N|http://ip/task?taskID 返回了后台错误|**服务端**未处理 taskID 为 null 的情况|


- DELETE ​/task Complete an uncompleted task

  |Case|Pass|Error|Reason|
  |:--:|:--:|:---:|:----:|
  |正确删除|N|后台错误|**后台**应该从request.body获取参数|
  |不存在任务|Y|||
  |不足信息|Y|||
  |不属于自己的任务|Y|||

- GET ​/tasks Get a page of available tasks

  |Case|Pass|Error|Reason|
  |:--:|:--:|:---:|----|
  |不足信息|Y|||
  |正确信息|N|/tasks?page=1，返回404|**服务端**没有await等待后台返回且没有被page参数发送过去;<br/>**后台**服务端传输参数为isComplete但数据库字段是isCompleted，未作转换|
  |越界页数|N|数据错误|**后台**的 page 起始index计算错误，当最大页数为第二页时，输入第一页返回第二页，输入第二页告知越界|

- GET ​/accepted_tasks Query a page of accepted tasks of current user

  |Case|Pass|Error|Reason|
  |:--:|:--:|:---:|----|
  |None|N||**后台**page计算错误|
  

- POST ​/accepted_tasks Accept a new task.

  |Case|Pass|Error|Reason|
  |:--:|:--:|:---:|----|
  |正确接收|N|返回信息不足|**服务端**使用POST方法，但从query取数据<br>**后台**使用`!=`和None判等，应使用 `is`|
  |正确完成问卷|N||**服务端**没有读取过问卷的answer|
  

- GET ​/created_tasks Query a page of created tasks of current user

  |Case|Pass|Error|Reason|
  |:--:|:--:|:---:|----|
  |不足信息|Y|||
  |正确信息|N|请求第一页数据，返回第二页|后台page的起始 index 计算错误|
  |越界页数|N|**后台**的 page 起始index计算错误，当最大页数为第二页时，输入第一页返回第二页，输入第二页告知越界|
  
- POST ​/created_tasks Update a task

  |Case|Pass|Error|Reason|
  |:--:|:--:|:---:|----|
  |正确更新|N|404|**服务端**没有注册路由+从this获取axios+post方法却从query获取属性|
  |不足信息|N|同上||
  

- GET ​/acceptance Query a page of acceptance record of a specific task.

  |Case|Pass|Error|Reason|
  |:--:|:--:|:---:|----|
  |不足信息|Y|||
  |正确信息|N|请求第一页数据，返回第二页|后台page的起始 index 计算错误|
  |不存在任务|Y|||
  |不足信息|Y|||


- POST ​/acceptance Finish one created task for a specific user.

  |Case|Pass|Error|Reason|
  |:--:|:--:|:---:|----|
  |不足信息|Y|||
  |正确信息|Y|||
  |不存在任务|Y|||
  |再次完成|Y|||
  |不属于自己的任务|N|返回500|**服务端**没有解析后台返回的401状态码，当作500处理|


- DELETE ​/acceptance One can delete its acceptance record. 

  |Case|Pass|Error|Reason|
  |:--:|:--:|:---:|----|
  |正确信息|N|返回信息不足|**服务端**从body取数据，但API中说明使用query string+解析出username，发送数据却使用userID+后台API使用字段为username，发送了userID|
  |不存在任务|Y|||
  |已完成|Y|||
  |不属于自己的任务|N|返回500|**服务端**没有解析后台返回的401状态码，当作500处理|
