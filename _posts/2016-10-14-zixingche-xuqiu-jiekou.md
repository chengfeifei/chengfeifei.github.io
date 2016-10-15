---
layout: post
title: 行践自行车项目接口需求
date: 2016-10-14
categories: work
tags: [接口需求]
---

 版本  | 修订内容                  | 修订日期    |
------|--------------------------|------------|
 V1.0 | 用户App、员工App接口参数描述 | 2016-10-14 |

>所有接口均返回状态码，表示请求成功或请求失败，失败状态码定义多种错误类型。
>
>参数标记可空的为可空参数，未标记的为非空参数。
>
>时间格式在App中变化较多，建议后台返回long型时间，App做格式处理。

### 用户App

#### 地图－附近站点

**请求参数：**

* 用户当前位置
* 范围半径

**响应参数：**

* 范围内的站点坐标
* 每个站点的名称
* 每个站点的编号
* 每个站点的可借车辆数
* 每个站点的可还锁桩数
* 每个站点的站点状态（充足、紧缺、无可用）。

**备注：**站点状态根据可借车辆数、可还锁桩数判断。可借车辆数大于总量70%为充足（锁桩同理，两者都满足此条件的情况下），可借车辆数大于0且小于总量40%为紧缺（锁桩同理，两者满足任意一种的情况下），可借车辆数等于0为无可用（锁桩同理，两者满足任意一种的情况下）。**这里的70%和40%可能会改动。**

---

#### 登录

**请求参数：**

* 手机号
* 密码

**响应参数：**

* 昵称（可空）
* 头像（可空）
* 手机号（可空，办理骑行卡时的预留手机号）
* 骑行卡号（可空）
* 骑行卡余额（可空）
* 保证金（可空）

---

#### 获取验证码

**请求参数：**

* 手机号

**响应参数：**

* 验证码

---

#### 注册

**请求参数：**

* 手机号
* 密码
* 短信验证码

**响应参数：**

* 无

---

#### 找回密码

**请求参数：**

* 手机号
* 密码
* 短信验证码

**响应参数：**

* 无

---

#### 绑定骑行卡

**请求参数：**

* 手机号（办理骑行卡时的预留手机号）
* 短信验证码
* 骑行卡号
* 真实姓名
* 身份证号

**响应参数：**

* 无

**备注：**办理骑行卡时的预留手机号，可与注册手机号不一致，App个人中心需要展示的手机号为办理骑行卡时的预留手机号。**一个骑行卡号对应一个登录帐号，绑定骑行卡后登录帐号做一个标记，再用新的登录帐号绑定该骑行卡不允许。**

---

#### 报修－故障提交

**请求参数：**

* 骑行卡号
* 车辆编号或锁桩编号或站点编号，根据故障类型填写相应编号（可空，用户可能不知道编号）
* 故障类型
* 故障照片（暂定一张）
* 故障描述

**响应参数：**

* 无

---

#### 地图－借车时间

**请求参数：**

* 骑行卡号

**响应参数：**

* 是否为借车状态（已借车或未借车）
* 借车时间（可空，时间格式为“01:23”、“1天”）

**备注：**根据骑行卡号获取借车状态，如果已借车返回借车时间。

---

#### 租车－扫码租车

**请求参数：**

* 骑行卡号
* 租用方式
* 二维码信息

**响应参数：**

* 站点名称
* 锁桩编号
* 车辆编号
* 单价

---

#### 出行－收入明细

**请求参数：**

* 骑行卡号
* 页数
* 每页显示数据的条数

**响应参数：**

* 时间（格式：“2016-10-14 13:23”）
* 金额

**备注：**默认每10条数据分页处理。

---

#### 出行－支出明细

**请求参数：**

* 骑行卡号
* 页数
* 每页显示数据的条数

**响应参数：**

* 时间（格式：“2016-10-14 13:23”）
* 金额
* 租用方式
* 租用时间
* 借车站点
* 还车站点

**备注：**默认每10条数据分页处理。

---

#### 个人中心－修改昵称

**请求参数：**

* 昵称

**响应参数：**

* 无

---

#### 个人中心－上传头像

**请求参数：**

* 照片

**响应参数：**

* 无

---

#### 个人中心－设置－在线客服

**请求参数：**

* 骑行卡号
* 反馈内容

**响应参数：**

* 无

---

#### 消息－消息列表

**请求参数：**

* 骑行卡号（可空）

**响应参数：**

* 当前消息类型
* 每种类型消息的第一条消息的内容
* 每种类型消息的第一条消息的时间（当天时间格式为“xx分钟前”或“xx小时前”，非当天时间格式为“2016-10-14”）

**备注：**未登录或未绑卡用户可收到与卡无关的消息（如优惠活动），绑卡用户可收到与卡相关的消息（如借车提醒）。

---

#### 消息－消息详情

**请求参数：**

* 消息类型
* 页数
* 每页显示消息的条数
* 骑行卡号（可空）

**响应参数：**

* 每条消息的内容（限制100字以内）
* 每条消息的时间（当天时间格式为“xx分钟前”或“xx小时前”，非当天时间格式为“2016-10-14”）

**备注：**未登录或未绑卡用户可查看与卡无关的消息详情（如优惠活动），绑卡用户可查看与卡相关的消息详情（如借车提醒）。默认每10条消息分页处理。

---

### 员工App

#### 登录

**请求参数：**

* 账号
* 密码

**响应参数：**

* 员工类型（共四种：调度人员、巡检人员、维修人员、管理人员）
* 员工姓名
* 员工工号
* 所在公司

---

#### 调度人员－任务列表

**请求参数：**

* 员工类型
* 员工工号
* 页数
* 每页显示数据的条数

**响应参数：**

* 任务类型（后台调度人员指派任务、App维修人员指派任务）
* 任务编号
* 站点名称（调出站点、调入站点、维修车辆所在站点）
* 站点编号
* 调动数量（可空，App维修人员指派任务无此字段，后台调度人员指派任务有此字段）
* 要求开始时间（可空，App维修人员指派任务无此字段，后台调度人员指派任务有此字段）
* 要求结束时间（可空，App维修人员指派任务无此字段，后台调度人员指派任务有此字段）
* 任务状态（待开始、进行中、已完成）
* 提交者的姓名（可空，后台调度人员指派任务无此字段，App维修人员指派任务有此字段）
* 车架号（可空，后台调度人员指派任务无此字段，App维修人员指派任务有此字段）
* 照片（可空，后台调度人员指派任务无此字段，App维修人员指派任务有此字段）
* 故障描述（可空，后台调度人员指派任务无此字段，App维修人员指派任务有此字段）

**备注：**默认每10条数据分页处理。

---

#### 调度人员－任务详情－调出调入（后台指派任务）

**页面所需字段：**

* 站点名称（调出站点或调入站点）
* 站点编号
* 应调车辆数
* 要求开始时间
* 要求结束时间
* 任务状态（待开始、进行中、已完成）

**备注：**不需接口，从任务列表中获取此页面字段。

---

#### 调度人员－任务详情－维修点（App指派任务）

**页面所需字段：**

* 站点名称（维修车辆所在站点）
* 站点编号
* 提交者的姓名
* 照片（从维修人员任务中获取，维修人员通过巡检人员获取，巡检人员通过自己拍摄获取或从调度人员和用户提交的故障信息中获取）
* 车架号（可空，用户提交时可能不知道编号，同照片获取逻辑）
* 故障描述（同照片获取逻辑）
* 任务状态（待开始、进行中、已完成）

**备注：**不需接口，从任务列表中获取此页面字段。

---

#### 调度人员－任务详情－调出调入－确认完成

**请求参数：**

* 员工工号
* 任务编号
* 任务完成情况（可空）

**响应参数：**

* 实际调往站点编号（调度卡应该能获取此信息）
* 实际调往站点名称（调度卡应该能获取此信息）
* 实际调度车辆数
* 完成时间

**备注：**需要硬件交互，通过员工工号查询员工所用的调度卡信息来判断调度任务完成情况。**从调度卡读取到的任务完成情况可能与当前页面任务不对应，需要和当前页面任务比较吗？还是以调度卡任务完成情况为最终的任务完成情况？**和客户讨论的结果是以调度卡任务完成情况为最终的任务完成情况，但是需要怎么处理不至于使任务记录混乱需要考虑到。

---

#### 调度人员－任务详情－维修点－确认完成

**请求参数：**

* 员工工号
* 任务编号
* 任务完成情况（可空）

**响应参数：**

* 实际调往站点编号（调度卡应该能获取此信息）
* 实际调往站点名称（调度卡应该能获取此信息）
* 实际调度车辆数
* 完成时间

**备注：**需要硬件交互，通过员工工号查询员工所用的调度卡信息来判断调度任务完成情况。**从调度卡读取到的任务完成情况可能与当前页面任务不对应，需要和当前页面任务比较吗？还是以调度卡任务完成情况为最终的任务完成情况？**和客户讨论的结果是以调度卡任务完成情况为最终的任务完成情况，但是需要怎么处理不至于使任务记录混乱需要考虑到。

---

#### 调度人员－车辆处置－确认完成

**请求参数：**

* 员工工号
* 任务完成情况（可空）
* 站点名称（调出站点或调入站点）

**响应参数：**

* 实际调往站点编号（调度卡应该能获取此信息）
* 实际调往站点名称（调度卡应该能获取此信息）
* 实际调度车辆数
* 完成时间

**备注：**此页面功能是调度人员对调度中剩余车辆的处置。需要硬件交互，通过员工工号查询员工所用的调度卡信息来判断调度任务完成情况。**从调度卡读取到的任务完成情况可能与当前页面任务不对应，需要和当前页面任务比较吗？还是以调度卡任务完成情况为最终的任务完成情况？**和客户讨论的结果是以调度卡任务完成情况为最终的任务完成情况，但是需要怎么处理不至于使任务记录混乱需要考虑到。

---

#### 调度人员－故障提交

**请求参数：**

* 员工工号
* 车辆编号或锁桩编号或站点编号，根据故障类型填写相应编号
* 故障类型
* 故障照片（暂定一张）
* 故障描述

**响应参数：**

* 无

---

#### 巡检人员－任务列表

**请求参数：**

* 员工类型
* 员工工号
* 页数
* 每页显示数据的条数

**响应参数：**

* 任务编号
* 车辆编号或锁桩编号或站点编号（可空，用户可能不知道编号）
* 站点编号
* 故障地点
* 故障类型
* 故障照片
* 故障描述
* 任务状态（待开始、进行中、已完成）

**备注：**默认每10条数据分页处理。用户和调度人员提交的故障客服审核通过后显示在这里。

---

#### 巡检人员－任务详情

**页面所需字段：**

* 故障类型
* 故障地点
* 站点编号
* 车辆编号或锁桩编号或站点编号（可空，用户可能不知道编号）
* 故障照片
* 故障描述

**备注：**不需接口，从任务列表中获取此页面字段。

---

#### 巡检人员－任务详情－驳回

**请求参数：**

* 任务编号
* 员工工号（巡检人员的工号）

**响应参数：**

* 无

---

#### 巡检人员－任务详情－故障确认

**请求参数：**

* 任务编号
* 员工工号（巡检人员的工号）

**响应参数：**

* 无

**备注：**用户故障提交时上传了骑行卡号，故障确认存在后，根据后台设置的奖励规则，奖励现金发放到用户骑行卡中。而且，故障确认后的信息显示到维修人员任务列表。

---

#### 巡检人员－故障提交

**请求参数：**

* 员工工号（巡检人员的工号）
* 员工姓名（巡检人员的姓名）
* 车辆编号或锁桩编号或站点编号，根据故障类型填写相应编号
* 故障类型
* 故障照片（暂定一张）
* 故障描述

**响应参数：**

* 无

**备注：**巡检人员提交的故障显示到维修人员任务列表。

---

#### 维修人员－任务列表

**请求参数：**

* 员工类型
* 员工工号
* 页数
* 每页显示数据的条数

**响应参数：**

* 任务编号
* 提交者（巡检人员的姓名）
* 站点编号
* 故障地点
* 故障类型
* 车辆编号或锁桩编号或站点编号（可空，用户可能不知道编号）
* 故障照片
* 故障描述
* 任务状态（待开始、进行中、已完成）

**备注：**默认每10条数据分页处理。

---

#### 维修人员－任务详情

**页面所需字段：**

* 故障类型
* 故障地点
* 站点编号
* 提交者（巡检人员的姓名）
* 车辆编号或锁桩编号或站点编号（可空，用户可能不知道编号）
* 故障照片
* 故障描述

**备注：**不需接口，从任务列表中获取此页面字段。

---

#### 维修人员－任务详情－确认完成

**请求参数：**

* 任务编号
* 员工工号（巡检人员的工号）
* 维修方式
* 维修确认照片（可空，暂定一张，维修完成后添加此照片）

**响应参数：**

* 无

**备注：**维修方式选择送至维修点，不需维修确认照片，确认按钮功能为提醒调度员把车辆送至维修点，任务状态为进行中；维修人员回到维修点修好车辆后，再次点击确认按钮提醒调度员把车辆送回站点，任务状态为已完成。维修方式选择现场维修，需维修确认照片，点击确认按钮后任务状态为已完成。

---

#### 管理人员－任务列表

**备注：**调度人员、巡检人员、维修人员任务列表中任务状态为已完成的列表都会显示在这里。

---

#### 管理人员－任务详情－调度

**页面所需字段：**

* 调度人员任务详情中的字段和照片（可空，一张照片：维修人员通知调度员的调度任务中含故障照片）
* 实际调度车辆数（调度卡获取此信息）
* 实际调度每个车辆的编号（调度卡获取此信息）
* 实际开始时间（调度卡获取此信息）
* 实际结束时间（调度卡获取此信息）
* 管理人员确认照片（暂定一张）
* 管理人员任务评价
* 管理人员任务评分

---

#### 管理人员－任务详情－巡检

**页面所需字段：**

* 巡检人员任务详情中的字段和照片（一张照片：故障照片）
* 管理人员确认照片（暂定一张）
* 管理人员任务评价
* 管理人员任务评分

---

#### 管理人员－任务详情－维修

**页面所需字段：**

* 维修人员任务详情中的字段和照片（两张照片：故障照片＋维修确认照片）
* 管理人员确认照片（暂定一张）
* 管理人员任务评价
* 管理人员任务评分

---

#### 管理人员－任务详情－确认完成

**请求参数：**

* 任务编号
* 员工工号（管理人员的工号）

**响应参数：**

* 无

**备注：**确认后后台只是做记录，不需要通知其他员工。