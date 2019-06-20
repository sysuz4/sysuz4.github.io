<h1>Use cases</h1>
<h1>详述用例Use case 1 发布任务</h1>
<b>范围：</b>易闲圈应用 <br /><br />
<b>级别：</b>用户目标 <br /><br />
<b>主要参与者：</b>APP用户 <br /><br />
<b>涉众及关注点：</b>

- 发任务者：希望发任务的操作尽可能简单、方便；希望可以灵活设置与任务相关的内容，比如任务截止时间、任务酬劳等，希望能够筛选任务目标人群，达到更好的任务完成效果。希望通过平台能够快速发布任务，并使很多人看到自己发布的任务。
- 接收任务者：希望能对平台上的任务进行筛选，快速寻找自身符合条件的任务和自己有意愿接受的任务，希望对任务的讲述足够清晰明确。
- APP平台管理者：希望发布任务者能够按照指引正确地发布任务，希望发布任务和接收任务的人都诚实守信，按照平台的管理条例行事。

<b>前置条件：</b><br />
APP用户必须经过系统验证身份，成功登陆才可以发布任务。同时，平台要求发布任务的用户的信誉值不低于某个数值，否则系统将认为该用户信誉值不够而不能够发布任务。另外，平台要求用户所发布任务的任务酬劳金额不得大于该用户账户所剩余额，否则无法发布任务。<br />

<b>成功保证(后置条件):</b><br />
存储任务信息。准确投放目标人群。发布任务者和接收任务者均诚实守信。

<b>主成功场景(基本流程):</b>

1. 用户通过个人账户的账号和密码成功登陆平台。
2. 用户通过点击发布任务按钮进入发布任务界面。
3. 用户在发布任务界面按照格式规范添加任务内容。
4. 用户在填写完任务内容之后设置任务截止时间。
5. 用户设置任务酬劳并确认发布任务。
6. 系统根据用户设置的任务酬劳从用户的账户余额中扣除相应的金额。

<b>扩展(替代流程):</b>

- 1a.用户忘记密码而无法成功登陆平台
    1. 通过邮箱找回密码
    2. 通过手机号找回密码

- 3a.用户没有按照格式要求填写任务内容，比如跑腿任务没有留下自己的联系方式
    1. 系统将检测用户填写的内容是否符合规范，检测到不符合规范的内容将弹窗提示用户做相应的修改

- 6a.用户的账户余额过少无法扣除任务酬劳
    1. 平台将拒绝用户发布任务的请求并提示用户账户余额过低

- 用户发布任务后发现任务内容设置错误
    1. 平台不支持任务发布后的修改功能，若任务内容有误，发布者可通过先取消此任务再发布一个新的任务

<b>发生频率：</b><br />可能会不断地发生。<br /><br />
<b>未解决问题：</b><br />
用户填写任务的过程中系统突然失效，重新进入发布任务界面之后原先填写的内容不在了。



<h1>2.非正式用例</h1>
<h2>Use case 2.1 注册登录</h2>

- Actor：用户
- Type：Primary
- Description：用户打开APP时需要登录，首次使用APP需要注册账号。
- 活动图：<br/>
![注册登录](https://raw.githubusercontent.com/zhengxq27/picture/master/%E6%B3%A8%E5%86%8C%E7%99%BB%E5%BD%95.png)

<h2>Use case 2.2 查看任务</h2>

- Actor：用户
- Type：Primary
- Description：用户可查看平台上已发布的任务，可对任务进行筛选;点击任务可查看任务详情。
- 活动图：<br/>
![查看任务](https://raw.githubusercontent.com/zhengxq27/picture/master/%E6%9F%A5%E7%9C%8B%E7%AD%9B%E9%80%89%E4%BB%BB%E5%8A%A1.png)

<h2>Use case 2.3 领取任务</h2>

- Actor：用户
- Type：Primary
- Description：用户可在平台上领取适合自己的任务。
- 活动图：<br/>
![领取任务](https://raw.githubusercontent.com/zhengxq27/picture/master/%E9%A2%86%E5%8F%96%E4%BB%BB%E5%8A%A1.png)

<h2>Use case 2.4 发布任务者确认完成任务</h2>

- Actor：用户
- Type：Primary
- Description：发布任务的人可以在一段时间后确认任务完成，此时领取该任务并顺利完成任务的人会自动收到任务酬劳；若发布任务者没有确认任务完成，一段时间后系统将自动判定该任务已完成。
- 活动图:<br/>
![发布任务者完成任务](https://raw.githubusercontent.com/zhengxq27/picture/master/%E5%8F%91%E5%B8%83%E8%80%85%E5%AE%8C%E6%88%90%E4%BB%BB%E5%8A%A1.png)

<h2>Use case 2.5 领取任务者确认完成任务</h2>

- Actor：用户
- Type：Primary
- Description：领取任务的人在完成任务之后可以登录系统确认任务完成；若领取任务者在任务Deadline之前顺利完成任务，则系统将任务酬劳发送到该完成者账户，若任务完成时间超过截止时间，则系统判定任务完成失败，领取任务者将不会获得酬劳。
- 活动图：<br/>
![领取任务者确认完成任务](https://raw.githubusercontent.com/zhengxq27/picture/master/%E9%A2%86%E5%8F%96%E4%BB%BB%E5%8A%A1%E8%80%85%E5%AE%8C%E6%88%90%E4%BB%BB%E5%8A%A1.png)

<h2>Use case 2.6 发布任务者取消任务</h2>

- Actor：用户
- Type：Primary
- Description：发布任务者可在任务截止时间之前取消任务，若取消任务时该任务还没有被人领取，则发布者成功取消任务；若任务已被领取，则可申请系统仲裁。
- 活动图：<br/>
![发布者取消任务](https://raw.githubusercontent.com/zhengxq27/picture/master/%E5%8F%91%E5%B8%83%E8%80%85%E5%8F%96%E6%B6%88.png)

<h2>Use case 2.7 领取任务者取消任务</h2>

- Actor：用户
- Type：Primary
- Description：领取任务者可选择取消自己领取的任务，领取任务之后未完成取消会扣除自己的信誉值。
- 活动图:<br/>
![领取者取消任务](https://raw.githubusercontent.com/zhengxq27/picture/master/%E9%A2%86%E5%8F%96%E8%80%85%E5%8F%96%E6%B6%88.png)

<h2>Use case 2.8 举报任务</h2>

- Actor：用户
- Type：Primary
- Description：系统设置任务举报功能，用户可以举报自己认为内容违规的任务，举报成功的用户将获得信誉值奖励，当用户信誉值过低时，积极查找违规内容、举报不良任务是快速提升自身信誉值的良好途径。
- 活动图:<br/>
![举报任务](https://raw.githubusercontent.com/zhengxq27/picture/master/%E4%B8%BE%E6%8A%A5%E4%BB%BB%E5%8A%A1.png)

<h2>Use case 2.9 查看、修改个人信息</h2>

- Actor：用户
- Type: Primary
- Description：用户可查看、修改自己的个人信息。
- 活动图:<br/>
![查看、修改个人信息](https://raw.githubusercontent.com/zhengxq27/picture/master/%E6%9F%A5%E7%9C%8B%E4%BF%AE%E6%94%B9%E4%B8%AA%E4%BA%BA%E4%BF%A1%E6%81%AF.png)