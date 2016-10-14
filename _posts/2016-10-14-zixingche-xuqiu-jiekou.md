---
layout: post
title: 行践自行车项目接口需求
date: 2016-10-14
categories: work
tags: [接口需求]
---

### 用户App

**启动App流程**

![](http://7xsv37.com1.z0.glb.clouddn.com/zixingche_jiekou_qidongapp.png)

请求参数：用户当前位置、范围半径。

响应参数：站点坐标、可借车辆数、可还锁桩数、站点状态（充足、紧缺、无可用）。

>备注：站点状态根据可借车辆数、可还锁桩数判断。可借车辆数大于总量70%为充足（锁桩同理），可借车辆数大于0且小于总量40%为紧缺（锁桩同理），可借车辆数为0为无可用（锁桩同理）。**这里的70%和40%可能会改动。**

---

**登录流程**

![](http://7xsv37.com1.z0.glb.clouddn.com/zixingche_jiekou_denglu.png)

请求参数：手机号、密码。

响应参数：昵称（可空）、头像（可空）、手机号（非空）、骑行卡号（可空）骑行卡余额（可空）、保证金（可空）。

---

**获取验证码流程**

![](http://7xsv37.com1.z0.glb.clouddn.com/zixingche_jiekou_yanzhengma.png)

请求参数：手机号。

响应参数：验证码。

---

**注册流程**

![](http://7xsv37.com1.z0.glb.clouddn.com/zixingche_jiekou_zhuce.png)

请求参数：手机号、密码、短信验证码。

响应参数：无（返回成功或失败code）。

---

**找回密码流程**

![](http://7xsv37.com1.z0.glb.clouddn.com/zixingche_jiekou_zhaohuimima.png)

请求参数：手机号、密码、短信验证码。

响应参数：无（返回成功或失败code）。

---

**绑定骑行卡流程**

![](http://7xsv37.com1.z0.glb.clouddn.com/zixingche_jiekou_bangka.png)

请求参数：手机号（办理骑行卡时的预留手机号，可与注册手机不一致）、短信验证码、骑行卡号、真实姓名、身份证号。

响应参数：无（返回成功或失败code）。

>备注：一个骑行卡号对应一个登录帐号，绑定骑行卡后登录帐号做一个标记，再用新的登录帐号绑定该骑行卡不允许。

---

**故障提交流程**

![](http://7xsv37.com1.z0.glb.clouddn.com/zixingche_jiekou_guzhangtijiao.png)

请求参数：车辆编号或锁桩编号或站点编号（可空）、故障照片（非空，暂定一张）、故障描述（非空）。

响应参数：无（返回成功或失败code）。

>备注：这里的响应目的是通知App故障是否提交成功。