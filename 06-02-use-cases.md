<h1>Use cases</h1>
<h2>Use case1 注册登录</h2>

- Actor：用户
- Type：Primary
- Description：用户打开APP时需要登录，首次使用APP需要注册账号。
- 活动图：
![注册登录](https://raw.githubusercontent.com/zhengxq27/picture/master/%E6%B3%A8%E5%86%8C%E7%99%BB%E5%BD%95.png)

<h2>Use case2 查看任务</h2>

- Actor：用户
- Type：Primary
- Description：用户可查看平台上已发布的任务，可对任务进行筛选;点击任务可查看任务详情。
- 活动图：
![查看任务](https://raw.githubusercontent.com/zhengxq27/picture/master/%E6%9F%A5%E7%9C%8B%E7%AD%9B%E9%80%89%E4%BB%BB%E5%8A%A1.png)

<h2>Use case3 发布任务</h2>

- Actor：用户
- Type：Primary
- Description：用户可在平台上发布任务，发布的任务类型有两种：问卷调查，跑腿型任务；用户发布任务需要扣除一定的金额。
- 活动图：
![发布任务](https://raw.githubusercontent.com/zhengxq27/picture/master/%E5%8F%91%E5%B8%83%E4%BB%BB%E5%8A%A1.png)

<h2>Use case4 领取任务</h2>

- Actor：用户
- Type：Primary
- Description：用户可在平台上领取适合自己的任务。
- 活动图：
![领取任务](https://raw.githubusercontent.com/zhengxq27/picture/master/%E9%A2%86%E5%8F%96%E4%BB%BB%E5%8A%A1.png)

<h2>Use case5 发布任务者确认完成任务</h2>

- Actor：用户
- Type：Primary
- Description：发布任务的人可以在一段时间后确认任务完成，此时领取该任务并顺利完成任务的人会自动收到任务酬劳；若发布任务者没有确认任务完成，一段时间后系统将自动判定该任务已完成。
- 活动图:
![发布任务者完成任务](https://raw.githubusercontent.com/zhengxq27/picture/master/%E5%8F%91%E5%B8%83%E8%80%85%E5%AE%8C%E6%88%90%E4%BB%BB%E5%8A%A1.png)

<h2>Use case6 领取任务者确认完成任务</h2>

- Actor：用户
- Type：Primary
- Description：领取任务的人在完成任务之后可以登录系统确认任务完成；若领取任务者在任务Deadline之前顺利完成任务，则系统将任务酬劳发送到该完成者账户，若任务完成时间超过截止时间，则系统判定任务完成失败，领取任务者将不会获得酬劳。
- 活动图：
![领取任务者确认完成任务](https://raw.githubusercontent.com/zhengxq27/picture/master/%E9%A2%86%E5%8F%96%E4%BB%BB%E5%8A%A1%E8%80%85%E5%AE%8C%E6%88%90%E4%BB%BB%E5%8A%A1.png)

<h2>Use case7 发布任务者取消任务</h2>

- Actor：用户
- Type：Primary
- Description：发布任务者可在任务截止时间之前取消任务，若取消任务时该任务还没有被人领取，则发布者成功取消任务；若任务已被领取，则可申请系统仲裁。
- 活动图：
![发布者取消任务](https://raw.githubusercontent.com/zhengxq27/picture/master/%E5%8F%91%E5%B8%83%E8%80%85%E5%8F%96%E6%B6%88.png)

<h2>Use case8 领取任务者取消任务</h2>

- Actor：用户
- Type：Primary
- Description：领取任务者可选择取消自己领取的任务，领取任务之后未完成取消会扣除自己的信誉值。
- 活动图:<br/>
![领取者取消任务](https://raw.githubusercontent.com/zhengxq27/picture/master/%E9%A2%86%E5%8F%96%E8%80%85%E5%8F%96%E6%B6%88.png)

<h2>Use case9 举报任务</h2>

- Actor：用户
- Type：Primary
- Description：系统设置任务举报功能，用户可以举报自己认为内容违规的任务，举报成功的用户将获得信誉值奖励，当用户信誉值过低时，积极查找违规内容、举报不良任务是快速提升自身信誉值的良好途径。
- 活动图:<br/>
![举报任务](https://raw.githubusercontent.com/zhengxq27/picture/master/%E4%B8%BE%E6%8A%A5%E4%BB%BB%E5%8A%A1.png)

<h2>Use case10 查看、修改个人信息</h2>

- Actor：用户
- Type: Primary
- Description：用户可查看、修改自己的个人信息。
- 活动图:
![查看、修改个人信息](https://raw.githubusercontent.com/zhengxq27/picture/master/%E6%9F%A5%E7%9C%8B%E4%BF%AE%E6%94%B9%E4%B8%AA%E4%BA%BA%E4%BF%A1%E6%81%AF.png)