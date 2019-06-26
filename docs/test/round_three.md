# Round Three

## ServerEnd & BackEnd API

### 阶段三

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
  |学生用户|Y||
  |教师用户|Y||

- POST ​/account_info Update account info

  |Case|Pass|Error|Reason|
  |:--:|:--:|:---:|:----:|
  |正确信息|Y|||
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
  |正常发起|Y|||
  |信息不足|Y|||

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
  |信息不足|Y|||


- DELETE ​/task Complete an uncompleted task

  |Case|Pass|Error|Reason|
  |:--:|:--:|:---:|:----:|
  |正确删除|Y|||
  |不存在任务|Y|||
  |不足信息|Y|||
  |不属于自己的任务|Y|||

- GET ​/tasks Get a page of available tasks

  |Case|Pass|Error|Reason|
  |:--:|:--:|:---:|----|
  |不足信息|Y|||
  |正确信息|Y|||
  |越界页数|Y|||

- GET ​/accepted_tasks Query a page of accepted tasks of current user

  |Case|Pass|Error|Reason|
  |:--:|:--:|:---:|----|
  |正常获取|Y|||
  |越界页数|Y|||
  

- POST ​/accepted_tasks Accept a new task.

  |Case|Pass|Error|Reason|
  |:--:|:--:|:---:|----|
  |正确接受|Y|||
  |正确完成问卷|Y|||
  

- GET ​/created_tasks Query a page of created tasks of current user

  |Case|Pass|Error|Reason|
  |:--:|:--:|:---:|----|
  |不足信息|Y|||
  |正确信息|Y|||
  |越界页数|Y|||
  
- POST ​/created_tasks Update a task

  |Case|Pass|Error|Reason|
  |:--:|:--:|:---:|----|
  |正确更新|Y|||
  |不足信息|Y|||
  

- GET ​/acceptance Query a page of acceptance record of a specific task.

  |Case|Pass|Error|Reason|
  |:--:|:--:|:---:|----|
  |不足信息|Y|||
  |正确信息|Y||
  |不存在任务|Y|||
  |不足信息|Y|||


- POST ​/acceptance Finish one created task for a specific user.

  |Case|Pass|Error|Reason|
  |:--:|:--:|:---:|----|
  |不足信息|Y|||
  |正确信息|Y|||
  |不存在任务|Y|||
  |再次完成|Y|||
  |不属于自己的任务|Y|||


- DELETE ​/acceptance One can delete its acceptance record. 

  |Case|Pass|Error|Reason|
  |:--:|:--:|:---:|----|
  |正确信息|Y|||
  |不存在任务|Y|||
  |已完成|Y|||
  |不属于自己的任务|Y|||
