<h1>数据库设计</h1>

## 数据库模式 ##

### user ###

| 名称        | 类型    |  描述  |
| --------   | -----:   | :----: |
|userId|int(11)|用户id|
|userType|int(11)|用户类型|
|stuId|varchar(32)|用户学号|
|name|varchar(32)|用户真实姓名|
|avator|varchar(128)|用户头像URL|
|nickName|varchar(32)|用户昵称|
|age|int(11)|用户年龄|
|sex|int(11)|用户性别|
|grade|int(11)|用户年级|
|mailAddr|varchar(64)|用户邮箱|
|major|varchar(32)|用户专业|
|phoneNum|varchar(64)|用户手机号码|
|creditVal|int(11)|用户信誉值|
|balance|double|用户余额|
|tags|varchar(255)|用户标签|
|password|varchar(255)|用户密码|

### 物理模型 ###

![user模式](img/user_schema.PNG)<br>

* 主键：userId
  

### mission ###

 
* 注：mission指用户发布的任务

| 名称        | 类型    |  描述  |
| --------   | -----:   | :----: |
|missionId|int(11)|任务id|
|publishTime|varchar(32)|任务发布时间|
|missionStatus|int(11)|任务状态|
|title|varchar(64)|任务标题|
|deadLine|varchar(32)|任务截止日期|
|tags|varchar(255)|任务标签|
|money|double|任务奖金|
|userId|int(11)|任务发布者的id|
|taskNum|int(11)|任务需要的人数|
|reportNum|int(11)|任务被举报的次数| 

### 物理模型 ###
![mission模式](img/mission_schema.PNG)<br>

* 主键：missionId
* 外键：userId(user)

### task ###

* 注：task指用户接受的任务
  
| 名称        | 类型    |  描述  |
| --------   | -----:   | :----: |
|taskId|int(11)|任务id|
|taskType|int(11)|任务类型|
|taskStatus|int(11)|任务状态|
|finishTime|varchar(32)|任务完成日期|
|pubUserId|int(11)|发布者的id|
|accUserId|int(11)|接受者的id|
|missionId|int(11)|对应的mission的id|

* 主键：taskId
* 外键：pubUserId(user), accUserId(user),missionId(mission)

### 物理模型 ###
![task模式](img/task_schema.PNG)<br>



### questionare ###

| 名称        | 类型    |  描述  |
| --------   | -----:   | :----: |
|questionareId|int(11)|问卷id|
|taskId|int(11)|问卷对应任务的id|
|questionNum|int(11)|问卷中问题的数目|
|description|varchar(255)|问卷描述|

### 物理模型 ###
![questionare模式](img/questionare_schema.PNG)<br>

* 主键：questionareId
* 外键：taskId(task)

### errand ###

| 名称        | 类型    |  描述  |
| --------   | -----:   | :----: |
|errandId|int(11)|跑腿id|
|pic|varchar(255)|跑腿对应的图片URL|
|taskId|int(11)|跑腿对应任务的id|
|description|varchar(255)|跑腿描述|
|privateInfo|varchar(255)|接受跑腿后显示的联系方式等隐私信息|
### 物理模型 ###
![errand模式](img/errand_schema.PNG)<br>
* 主键：errandId
* 外键：taskId(task)

### question ###
| 名称        | 类型    |  描述  |
| --------   | -----:   | :----: |
|questionId|int(11)|问题id|
|questionType|int(11)|问题类型|
|question|varchar(255)|问题题干|
|answer|varchar(255)|问题的回答|
|choiceNum|int(11)|选择题可以选择的项目数量|
|choiceStr|varchar(255)|选择题所有选项的内容|
|questionareId|int(11)|问题对应问卷的id|
### 物理模型 ###
![question模式](img/question_schema.PNG)<br>

* 主键：questionId
* 外键：questionareId(questionare)



  
