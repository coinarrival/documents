# 用户系统数据库设计

|版本|日期|描述|作者|
|:-:|:-:|:-:|:-:|
|v0.1|2019年5月24日|初稿|BroInBro|
|v0.2|2019年6月12日|增加具体实现|张三丰|
|v0.3|2019年6月25日|完成所有功能|张三丰|

**第一轮迭代**

完成基本的用户数据表

数据库初始代码

```mysql
CREATE TABLE `account_info_account_info` (`id` integer AUTO_INCREMENT NOT NULL PRIMARY KEY, `username` varchar(200) NOT NULL UNIQUE, `email` varchar(200) NOT NULL UNIQUE, `phone` varchar(200) NOT NULL UNIQUE, `password` varchar(200) NOT NULL, `avatar` varchar(200) NOT NULL);
COMMIT;
```

**第二轮迭代**

丰富原有的用户数据表，增加任务信息表、钱包表、参与信息表

数据库初始代码

- 用户

```mysql
CREATE TABLE `account_info_user` (`id` integer AUTO_INCREMENT NOT NULL PRIMARY KEY, `username` varchar(100) NOT NULL UNIQUE, `gender` varchar(30) NULL, `email` varchar(50) NOT NULL UNIQUE, `phone` varchar(15) NOT NULL UNIQUE, `school` varchar(50) NULL, `major` varchar(30) NULL, `age` integer NULL, `role` varchar(30) NULL, `studentID` varchar(30) NULL, `teacherID` varchar(30) NULL, `grade` varchar(30) NULL, `password` varchar(30) NOT NULL, `avatar` varchar(300) NULL);
```

- 钱包

```mysql
CREATE TABLE `account_info_wallet` (`id` integer AUTO_INCREMENT NOT NULL PRIMARY KEY, `balance` integer NOT NULL, `user_id` integer NOT NULL);
```
- 任务

```mysql
CREATE TABLE `account_info_task` (`taskID` integer AUTO_INCREMENT NOT NULL PRIMARY KEY, `title` varchar(50) NOT NULL, `content` varchar(300) NOT NULL, `types` varchar(50) NOT NULL, `reward` double precision NOT NULL, `deadline` varchar(50) NOT NULL, `repeatTime` integer NOT NULL, `isCompleted` bool NOT NULL);
```

- 接受任务

```mysql
CREATE TABLE `account_info_accepttask` (`id` integer AUTO_INCREMENT NOT NULL PRIMARY KEY, `isFinished` bool NOT NULL, `answer` varchar(300) NULL);
```